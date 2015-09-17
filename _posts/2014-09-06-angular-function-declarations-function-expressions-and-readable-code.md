---
layout: post
title: Angular Function Declarations, Function Expressions, and Readable Code
date: 2014-09-06 14:46
author: John
comments: true
categories: [angular, javascript, patterns, Uncategorized]
---
<p>We spend more time reading our code than writing it. That's why it makes sense to write code that is easier to read. The good news is that there are a lot of really simple things that can make your code much more readable. This post describes simple techniques to make AngularJS controllers and services/factories more readable.</p>

<blockquote>
  <p>For more details on these and other Angular coding styles, please see my <a href="http://jpapa.me/ngstyles">Angular Style Guide</a> and my upcoming Pluralsight course "AngularJS Patterns: Clean Code" (Sep 2014).</p>
</blockquote>

<h2>Quiz</h2>

<p>OK, first let's take a step back and start with a quiz. See if you can get the answers to these correctly. Indulge me, there is a point (and quizzes are fun).</p>

<p><strong>Question 1</strong>: What will func1() yield?</p>

<pre><code>function func1() {
  function foo() {
    return 'foo-top';
  }
  return foo();
}
func1();
</code></pre>

<p><strong>Question 2</strong>: What will func2() yield?</p>

<pre><code>function func2() {
  return foo();
  function foo() {
    return 'foo-bottom';
  }
}
func2();
</code></pre>

<p><strong>Question 3</strong>: What will func3() yield?</p>

<pre><code>function func3() {
  var foo = function () {
    return 'foo-top';
  }
  return foo();
}
func3();
</code></pre>

<p><strong>Question 4</strong>: What will func4() yield?</p>

<pre><code>function func4() {
  return foo();
  var foo = function () {
    return 'foo-bottom';
  }
}
func4();
</code></pre>

<h2>Answers</h2>

<p>You may have noticed that this took a twist into a hoisting quiz. Hoisting is a key aspect that every JavaScript developer ought to understand. It can get you into trouble if you don't know how it works. Some folks say to avoid it, but I say understand it.</p>

<p>So about those answers, let's examine them 1 by one.</p>

<p><strong>Question 1</strong></p>

<pre><code>function func1() {
  function foo() {
    return 'foo-top';
  }
  return foo();
}
func1();
</code></pre>

<p>The output is <code>foo-top</code>. The function <code>foo</code> is defined and then the function is executed and returned. This one is pretty straight forward.</p>

<p><strong>Question 2</strong></p>

<pre><code>function func2() {
  return foo();
  function foo() {
    return 'foo-bottom';
  }
}
func2();
</code></pre>

<p>The output is <code>foo-bottom</code>. When <code>func2</code> executes it immediately returns the execution of the function <code>foo</code>. But wait, <code>foo</code> hasn't been defined yet? Or has it? Understanding that situation requires some experience with hoisting and the difference between a function declaration and function expression. <code>foo</code> is a function declaration (aka a function statement). JavaScript will hoist function declarations to the top of their closure, in this case that is the top of <code>func2</code>. What's hoisting? Hoisting is when JavaScript moves the definition of some code to the top of the closure. (There will be more on hoisting to follow, so remember that).</p>

<p>So in this case, it is helpful to think of Question 2 like this:</p>

<pre><code>function func2() {
  // Hoisted from below
  function foo() {
    return 'foo-bottom';
  }
  return foo();
  // This is hoisted to the top of func2
  //function foo() {
  //  return 'foo-bottom';
  //}
}
func2();
</code></pre>

<p><strong>Question 3</strong></p>

<pre><code>function func3() {
  var foo = function () {
    return 'foo-top';
  }
  return foo();
}
func3();
</code></pre>

<p>The output here is <code>foo-top</code>. This examples uses a function expression. A function expression takes a function and sets it to a variable, in this case <code>foo</code>. This works like any other variables defined in JavaScript if it is defined before it is used, then it's value is accessible. That's why we can execute <code>foo</code> successfully in this question.</p>

<p><strong>Question 4</strong></p>

<pre><code>function func4() {
  return foo();
  var foo = function () {
    return 'foo-bottom';
  }
}
func4();
</code></pre>

<p>The output here is an error <code>undefined is not a function</code>. Here is where hoisting comes into play yet again. The return statement executes <code>foo</code> which appears below the return. Since <code>foo</code> is a function expression, it is hoisted above the return right to the top of <code>func4</code>. But wait, didn't I just say it was hoisted up? Then why can't the return execute it properly? The interesting part is that the variable <code>foo</code> is hoisted, but the value it is set to is left in place. Say what? OK, let's look at how it actually is interpreted.</p>

<pre><code>function func4() {
  var foo; // which is undefined
  return foo(); // now executing `undefined`
  foo = function () {
    return 'foo-bottom';
  }
}
func4();
</code></pre>

<p>If you want to run all of these questions/examples yourself, <a href="http://plnkr.co/3IYT5f8bH47Ew1ODkbU1?p=preview">browse to this plunker to see them run</a>.</p>

<p>Here is another <a href="http://javascriptweblog.wordpress.com/2010/07/06/function-declarations-vs-function-expressions/">good post on hoisting and functions</a></p>

<h2>Function Declarations and Expressions</h2>

<p>You might think that one is better or worse than the other, and some folks may feel that way, but I offer another perspective: understand both and use what makes sense.</p>

<p>What I certainly agree with is the common industry belief that using function expressions and always keeping your <code>var</code> statements at the top of your functions can help you avoid hoisting issues. Absolutely spot on. Before I get to the "but", let's go back to some examples.</p>

<h2>Angular and Function Expressions</h2>

<p>This is an article about Angular, isn't it? Tiny little examples are easy to follow, like the ones above. But we don't code controllers and factories in Angular that are all &lt; 10 lines of code. We have real word code. So let's see how an Angular factory named <code>dataservice</code> would look using function expressions.</p>

<p>When I open this file I have to start scrolling like mad to find out what features I can access. So let's do that and scroll past this code.</p>

<pre><code>// Using function expressions
(function() { 'use strict';
    angular
        .module('app.core')
        .factory('dataservice', dataservice);

    /* @ngInject */
    function dataservice($http, $location, $q, exception, logger) {
        var isPrimed = false;
        var primePromise;

        var getAvengers = function() {
            var getAvengersComplete = function(data, status, headers, config) {
                return data.data[0].data.results;
            };

            return $http.get('/api/maa')
                .then(getAvengersComplete)
                .catch(function(message) {
                    exception.catcher('XHR Failed for getAvengers')(message);
                    $location.url('/');
                });
        };

        var getAvengerCount = function() {
            var count = 0;

            var getAvengersCastComplete = function(data) {
                count = data.length;
                return $q.when(count);
            };

            return getAvengersCast()
                .then(getAvengersCastComplete)
                .catch(exception.catcher('XHR Failed for getAvengerCount'));
        };

        var getAvengersCast = function() {
            var cast = [
                {name: 'Robert Downey Jr.', character: 'Tony Stark / Iron Man'},
                {name: 'Chris Hemsworth', character: 'Thor'},
                {name: 'Chris Evans', character: 'Steve Rogers / Captain America'},
                {name: 'Mark Ruffalo', character: 'Bruce Banner / The Hulk'},
                {name: 'Scarlett Johansson', character: 'Natasha Romanoff / Black Widow'},
                {name: 'Jeremy Renner', character: 'Clint Barton / Hawkeye'},
                {name: 'Gwyneth Paltrow', character: 'Pepper Potts'},
                {name: 'Samuel L. Jackson', character: 'Nick Fury'},
                {name: 'Paul Bettany', character: 'Jarvis'},
                {name: 'Tom Hiddleston', character: 'Loki'},
                {name: 'Clark Gregg', character: 'Agent Phil Coulson'}
            ];
            return $q.when(cast);
        };

        var prime = function() {
            // This function can only be called once.
            if (primePromise) {
                return primePromise;
            }

            var success = function() {
                isPrimed = true;
                logger.info('Primed data');
            };
            primePromise = $q.when(true).then(success);
            return primePromise;
        };

        var ready = function(nextPromises) {
            var readyPromise = primePromise || prime();

            return readyPromise
                .then(function() { return $q.all(nextPromises); })
                .catch(exception.catcher('"ready" function failed'));
        };

        var service = {
            getAvengersCast: getAvengersCast,
            getAvengerCount: getAvengerCount,
            getAvengers: getAvengers,
            ready: ready
        };

        return service;
    }
})();
</code></pre>

<p>Ah, here we are. Now at the bottom we can see the features I can call: <code>getAvengersCast</code>, <code>getAvengersCount</code>, <code>getAvengers</code>, and <code>ready</code>. But if that's all I wanted to know, and often it is, wouldn't it be nice to put that right at the top? That would make it easier for me to get in and out of the file quickly with what I need and not get distracted with all of the implementation details. (To be clear, I don't recommend doing this, but please play along.)</p>

<p>But I can't just move the <code>var service</code> and its return statement to the top, because as we saw earlier, hoisting will effectively move the variables for our functions but not their contents/bodies. So it would look something like this (see below) where the functions all become undefined because they are used before their function bodies are set.</p>

<pre><code>// Using function expressions 
(function() { 'use strict';
    angular
        .module('app.core')
        .factory('dataservice', dataservice);

    /* @ngInject */
    function dataservice($http, $location, $q, exception, logger) {
        var isPrimed = false;
        var primePromise;
        var getAvengers; // undefined
        var getAvengerCount; // undefined
        var getAvengersCast; // undefined
        var prime; // undefined
        var ready; // undefined

        var service = {
            getAvengersCast: getAvengersCast, // undefined
            getAvengerCount: getAvengerCount, // undefined
            getAvengers: getAvengers, // undefined
            ready: ready // undefined
        };

        return service;

        var getAvengers = function() {
            // collapsed for readability
        };

        var getAvengerCount = function() {
            // collapsed for readability
        };

        var getAvengersCast = function() {
            // collapsed for readability
        };

        var prime = function() {
            // collapsed for readability
        };

        var ready = function(nextPromises) {
            // collapsed for readability
        };    
    }
})();
</code></pre>

<h2>Angular and Function Declarations</h2>

<p>Let's now look at how function declarations would behave in this Angular factory. When I open this file I want to be able to quickly read the code to find the role of this factory and what functions it exposes. This should only take a glance to see the key ingredients. I can call <code>getAvengersCast</code>, <code>getAvengersCount</code>, <code>getAvengers</code>, and <code>ready</code>. How they are implemented and all the details that goes into baking them is lower down in the code. When I open this file in an editor I may see the top 20 to 40 lines of code (depending on your resolution and tools).</p>

<p>Everything above the <code>////////////////</code> is what's important to read. Everything below it are the implementation details.</p>

<p>The object literal <code>service</code> that is being returned refers to function declarations, which are all hoisted in their entirety up to the top. This means we get the readability of keeping the accessible interface of the factory up top while JavaScript can access all the implementation details. Pretty cool, huh?</p>

<pre><code>// Using function declarations 
(function() { 'use strict';
    angular
        .module('app.core')
        .factory('dataservice', dataservice);

    /* @ngInject */
    function dataservice($http, $location, $q, exception, logger) {
        var isPrimed = false;
        var primePromise;

        var service = {
            getAvengersCast: getAvengersCast,
            getAvengerCount: getAvengerCount,
            getAvengers: getAvengers,
            ready: ready
        };

        return service;

        ////////////////

        function getAvengers() {
            return $http.get('/api/maa')
                .then(getAvengersComplete)
                .catch(function(message) {
                    exception.catcher('XHR Failed for getAvengers')(message);
                    $location.url('/');
                });

            function getAvengersComplete(data, status, headers, config) {
                return data.data[0].data.results;
            }
        }

        function getAvengerCount() {
            var count = 0;
            return getAvengersCast()
                .then(getAvengersCastComplete)
                .catch(exception.catcher('XHR Failed for getAvengerCount'));

            function getAvengersCastComplete (data) {
                count = data.length;
                return $q.when(count);
            }
        }

        function getAvengersCast() {
            var cast = [
                {name: 'Robert Downey Jr.', character: 'Tony Stark / Iron Man'},
                {name: 'Chris Hemsworth', character: 'Thor'},
                {name: 'Chris Evans', character: 'Steve Rogers / Captain America'},
                {name: 'Mark Ruffalo', character: 'Bruce Banner / The Hulk'},
                {name: 'Scarlett Johansson', character: 'Natasha Romanoff / Black Widow'},
                {name: 'Jeremy Renner', character: 'Clint Barton / Hawkeye'},
                {name: 'Gwyneth Paltrow', character: 'Pepper Potts'},
                {name: 'Samuel L. Jackson', character: 'Nick Fury'},
                {name: 'Paul Bettany', character: 'Jarvis'},
                {name: 'Tom Hiddleston', character: 'Loki'},
                {name: 'Clark Gregg', character: 'Agent Phil Coulson'}
            ];
            return $q.when(cast);
        }

        function prime() {
            // This function can only be called once.
            if (primePromise) {
                return primePromise;
            }

            primePromise = $q.when(true).then(success);
            return primePromise;

            function success() {
                isPrimed = true;
                logger.info('Primed data');
            }
        }

        function ready(nextPromises) {
            var readyPromise = primePromise || prime();

            return readyPromise
                .then(function() { return $q.all(nextPromises); })
                .catch(exception.catcher('"ready" function failed'));
        }
    }
})();
</code></pre>

<p>This example uses the <a href="http://addyosmani.com/resources/essentialjsdesignpatterns/book/#revealingmodulepatternjavascript">Revealing Module Pattern</a>, which is one of my favorites.</p>

<h2>Angular Controllers</h2>

<p>Let's turn to controllers, which also apply here, though using a slightly different syntax. I'll keep this controller very short just to keep it a bit clearer. But keep in mind that the more code you add, the harder one of these is to read.</p>

<p>Here is an example using function expressions in an Angular controller named <code>avengers</code>. Notice that that you have to scan the entire file to learn which members are exposed on the <code>vm</code> and what runs right away (<code>activate</code>).</p>

<pre><code>// Using function expressions 
(function() { 'use strict';
    angular
        .module('app.avengers')
        .controller('Avengers', Avengers);

    /* @ngInject */
    function Avengers(dataservice, logger) {
        var vm = this;
        vm.avengers = [];
        vm.title = 'Avengers';

        var activate = function() {
            return getAvengers().then(function() {
                logger.info('Activated Avengers View');
            });
        }

        var getAvengers = function() {
            return dataservice.getAvengers().then(function(data) {
                vm.avengers = data;
                return vm.avengers;
            });
        }

        vm.getAvengers = getAvengers;

        activate();
    }
})();
</code></pre>

<p>Now let's take a look at some function declarations in an Angular controller named <code>avengers</code>. Notice that the important stuff is up top. For example, the members bound to the controller such as <code>vm.avengers</code> and <code>vm.title</code>. The implementation details are down below. This is just esier to read.</p>

<pre><code>// Using function declarations 
(function() { 'use strict';
    angular
        .module('app.avengers')
        .controller('Avengers', Avengers);

    /* @ngInject */
    function Avengers(dataservice, logger) {
        var vm = this;
        vm.avengers = [];
        vm.getAvengers = getAvengers;
        vm.title = 'Avengers';

        activate();

        function activate() {
            return getAvengers().then(function() {
                logger.info('Activated Avengers View');
            });
        }

        function getAvengers() {
            return dataservice.getAvengers().then(function(data) {
                vm.avengers = data;
                return vm.avengers;
            });
        }
    }
})();
</code></pre>

<h2>Summary</h2>

<p>I included semi-long examples here because short ones just don't illustrate it well enough, in my experience. Hoisting can be troublesome when used poorly ... but then again, so can a lot of things. The key is undertanding how it works. In these specific cases we're just talking about function expressions and declarations.</p>

<p>If you choose 1 over the other are you a bad developer? Absolutely not! You can use function expressions and keep your <code>var</code>'s up top and not run into any problems. You can also choose to use function declarations and keep your functions below their use. I prefer the latter for the readability aspects, because again, I spend much more time reading code (mine and other people's code) than I do writing it.</p>

<p>Either way you win ... but hopefully this helps clarify 2 of the common techniques used in Angular applications.</p>

<p>Once you understand hoisting you can use it to help write the same lines of code, but in a more readable manner.</p>

