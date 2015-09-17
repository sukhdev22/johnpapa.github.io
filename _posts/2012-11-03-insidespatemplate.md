---
layout: post
title: Inside the ASP.NET Single Page Apps Template Beta
date: 2012-11-03 17:11
author: John
comments: true
categories: [html5, javascript, knockout, mvvm, SPA, Uncategorized, visual studio 2012, web api]
---
There are a bunch of shiny new toys, including a new Single Page App (SPA) template, inside the <a href="http://www.asp.net/vnext/overview/fall-2012-update/aspnet-fall-2012-update-release-notes" target="_blank">ASP.NET Fall 2012 Update BUILD Prelease </a> ( <a href="http://www.asp.net/vnext/overview/fall-2012-update" target="_blank">Download link for it is on this page here</a> ) . The original template for SPA made an appearance over a year ago in a preview and was later removed prior to VS 2012 being released. (You may recall Upshot.js was part of the former template before both of their demises) The first run at the former template wasn't really a template, but rather a specific way to create a SPA. This new template is a template . Kudos to <a href="https://twitter.com/mkristensen" target="_blank">Mads Kristensen</a> for spearheading this at Microsoft. Here is the sample app that they give you when you choose the new SPA template.
<blockquote><strong style="color: red;">UPDATE: </strong> This post has been updated. There is a new version of this template in the ASP.NET and Web Tools 2012.2 (Release Candidate). <a href="inside-the-asp-net-single-page-apps-template" target="_blank">You can read my latest post on this for more details</a>. Most of the server side code has not changed, however the JavaScript has changed considerably and for the better in the latest version.</blockquote>
<a href="http://www.johnpapa.net/insidespatemplate/spa-todo-2/" rel="attachment wp-att-8571"><img class="aligncenter size-full wp-image-8571" title="spa todo" alt="" src="http://www.johnpapa.net/wp-content/uploads/2012/11/spa-todo1-e1352003009937.png" width="549" height="307" /></a>
<h2>What Do You Get?</h2>
<ul>
	<li>ASP.NET Web API Controllers</li>
	<li>ASP.NET MVC</li>
	<li>Authentication / Authorization</li>
	<li>Sample DbContext with Entity Framework and some POCO Models and DTO's</li>
	<li>Bundling and Minification</li>
	<li>jQuery</li>
	<li>Knockout.js</li>
	<li>Samples in JavaScript
<ul>
	<li>models</li>
	<li>a viewmodel</li>
	<li>custom Knockout binding handlers</li>
	<li>data access module</li>
</ul>
</li>
</ul>
The template gets you started with the intent of helping you avoid the "blank page" syndrome and instead having a starting point for creating a SPA. Where you take it from there is up to you. This is especially important since there are many good ways to create a SPA.  The key takeaway use it as a starting point to get you going.
<blockquote>For more information about SPA's you can refer to my <a href="http://www.johnpapa.net/building-single-page-apps-with-knockout-jquery-and-web-api-ndash-the-story-begins" target="_blank">SPA blog post series</a> or watch my <a href="http://jpapa.me/spaps" target="_blank">video course on building Single Page Apps</a>.

<a href="http://jpapa.me/spaps" target="_blank"><img class="aligncenter size-full wp-image-8761" title="spaps" alt="" src="http://www.johnpapa.net/wp-content/uploads/2012/11/spaps1.png" width="508" height="92" /></a>
<ul>
	<li>Part 1 – <a href="http://jpapa.me/spapost1">The Story Begins (What is the Code Camper SPA?)</a></li>
	<li>Part 2 – <a href="http://jpapa.me/spapost2">Client Technologies</a></li>
	<li>Part 3 – <a href="http://www.johnpapa.net/spapost3">Server Technologies (the Data Layer)</a></li>
	<li>Part 4 – <a href="http://jpapa.me/spapost4">Serving JSON with ASP.NET Web API</a></li>
	<li>Part 5 – <a href="http://jpapa.me/spapost5">HTML 5 and ASP.NET Web Optimization</a></li>
	<li>Part 6 – <a href="http://jpapa.me/spapost6">JavaScript Modules</a></li>
	<li>Part 7 – <a href="http://jpapa.me/spapost7">MVVM and KnockoutJS</a></li>
	<li>Part 8 – <a href="http://jpapa.me/spapost8">Data Services on the Client</a></li>
	<li>Part 9 – <a href="http://jpapa.me/spapost9">Navigation, Transitions, Storage and Messaging</a></li>
	<li>Part 10 – <a href="http://jpapa.me/spapost10">Saving, Change Tracking, and Commanding</a></li>
</ul>
</blockquote>
Let's start by examining exactly what's inside.
<h2>DbContext</h2>
They toss a very simple sample DbContext at you based on Entity Framework. You can obviously swap in and out whatever you want here.
<pre class="prettyprint linenums">public class TodoItemContext : DbContext
{
    public TodoItemContext()
        : base("name=DefaultConnection")
    {
    }

    public DbSet TodoItems { get; set; }
    public DbSet TodoLists { get; set; }
}</pre>
<h2>Models</h2>
The template comes with a series of models and Data Transfer Objects (DTO's). It's interesting that they decided to use both models and DTO's which are intended to be vessels for the models' data to send to the client.  This does offer more separation of models from DTO's but I'm not sure I'd have gone this route with a template. I'd instead start with the models and not add the DTO's til I actually needed one. (Or possibly I'd use a projection, but that's a tale for another time.)

<a href="http://www.johnpapa.net/wp-content/uploads/2012/11/todo-models.png"><img class="aligncenter size-full wp-image-8581" title="todo models" alt="" src="http://www.johnpapa.net/wp-content/uploads/2012/11/todo-models.png" width="189" height="130" /></a>
<h2>Web API Controllers</h2>
The template comes with a TodoListController and a TodoController.  They both have the [Authorize] attribute on the web api method calls, which is a good practice. The TodoListController has several methods for CRUD including a GetTodoLists (which gets all of the todo lists). It returns an IEnumerable (though with the new features it would be more interesting to return an IQueryable). Notice the code below retrieves the  Todo entities and then creates the Todo DTO's from them, before returning them to the caller. Pretty straightforward. Of course, they also have the CUD method from CRUD (Create, Update and Delete).
<pre class="prettyprint linenums">    [Authorize]
    public class TodoListController : ApiController
    {
        private TodoItemContext db = new TodoItemContext();

        // GET api/TodoList
        public IEnumerable GetTodoLists()
        {
            return db.TodoLists.Include("Todos")
                .Where(u =&gt; u.UserId == User.Identity.Name)
                .OrderByDescending(u =&gt; u.TodoListId)
                .AsEnumerable()
                .Select(todoList =&gt; new TodoListDto(todoList));
        }</pre>
The key takeaway here is how simple it is to set up your database, Entity Framework and API controllers to get you rock and rolling very quickly. It's a very scaled down version of what I did in my Code Camper SPA and a great starting point. So what do you do with this part of the demo? I'd start by deciding how you want your Entity Framework code to look and if you want to use it as your repository and Unit of Work or you want your own Repo and UoW on top of EF (what I did in Code Camper). Both are good choices. Next I'd decide on your structure for your Controllers. I like Separation of Concerns (SoC) and recommend making your controllers responsible for pushign and pulling data. THis means making sure you don;t add business logic to this layer. For that, I like the Controller to call a business manager layer who is responsible for handling all the heavy thinking. Finally, decide if you want or need custom DTO's ... I start without them and only add them if I see a need.
<h2>The View</h2>
The code below comes form the index.cshtml view inside of the Views/Home folder of the sample app. Notice it starts off with a quick check to make sure the user is authenticated. If they are not, it shows a login page (not shown below), but if they are authenticated the page displays the available Todo lists. This is a simple way to add some authentication to your app using some built in ASP.NET features.
<pre class="prettyprint">@if (@User.Identity.IsAuthenticated)
{

}</pre>
Then, inside of the if statement is all of the HTML and the bindings for the View.
<pre class="prettyprint linenums"><button data-bind="click: addTodoList">Add Todo list</button></pre>
<header><form data-bind="validate: true"><input class="required" type="text" data-bind="value: Title, selected: IsEditingListTitle, blurOnEnter: true" /></form></header>
<pre class="prettyprint linenums"><a class="deletelist" href="#" data-bind="click: $parent.deleteTodoList">X</a></pre>
<ul data-bind="foreach: Todos">
	<li><input type="checkbox" data-bind="checked: IsDone" /> <input type="text" data-bind="value: Title, disable: IsDone, blurOnEnter: true" /> <a href="#" data-bind="click: $parent.deleteTodo">X</a></li>
</ul>
<form data-bind="submit: addTodo"><input class="addTodo" type="text" data-bind="value: NewTodoTitle, placeholder: 'Add new todo', event: { blur: addTodo }" /></form><section id="lists" data-bind="foreach: todoLists, visible: todoLists().length &gt; 0"><article class="todoList"> </article></section>
<h2>Data Binding with Knockout</h2>
Notice some interesting data binding features, that use Knockout.js. You can create a list using Knockout's click binding which calls the addTodoList method. This method binding invokes the addTodoList method on the JavaScript ViewModel.
<pre class="prettyprint"><button data-bind="click: addTodoList">Add Todo list</button></pre>
The ViewModel also exposes a todoLists property which will be iterated over using Knockout's foreach binding. Notice the entire section is visible only if there are any todo's (using Knockout's  visible binding). It's often a good idea to use the visible binding to hide and show DOM elements instead of adding and removing them. DOM manipulation is very expensive in browsers, while hiding and show is often much faster.

You could bind the visible binding to any expression that is truthy or falsey, like this: visible: todoLists().length
<pre class="prettyprint"></pre>
They also included a few custom Knockout binding handlers:
<ul>
	<li>validate - invokes jQuery validation on an element</li>
	<li>selected - selects (or unselects) a DOM element based on the bound property's value</li>
	<li>blurOnEnter - loses focus when the user clicks the ENTER key</li>
	<li>placeHolder - a shim for the HTML5 placeholder for older browsers</li>
</ul>
The key here is not that actual binding handlers but rather that they show you a simple way to extend Knockout's binding structure to add your own features. I do this in my Code Camper SPA to create simple handlers like escape (which performs an action when the ESCAPE key is pressed) and more complex handlers for thing s like a  custom starRating control.

Once inside of the view, another foreach binding is used to iterate of each todo lists's todos. Here the checked binding checks or unchecks a  checkbox, the value binding displays the values for INPUT type="text" elements, the visible binding shows or hides an error message (for validation , and the click binding calls the $parent.deletTodo method. $parent is a feature in Knockout that let's you go up one (or more) levels in the datacontext hierarchy. In this case the binding is to a single todo item. The deleteTodo  happens on the parent level (at the Todos list level), so to get there we have to reference $parent to get back up to that level first, and then delete it. You can learn more about <a href="http://knockoutjs.com/documentation/binding-context.html" target="_blank">$parent at the Knockout site</a> or in <a href="http://jpapa.me/komvvm" target="_blank">my Knockout course at Pluralsight</a>.
<ul data-bind="foreach: Todos">
	<li><input type="checkbox" data-bind="checked: IsDone" /> <input type="text" data-bind="value: Title, disable: IsDone, blurOnEnter: true" /> <a href="#" data-bind="click: $parent.deleteTodo">X</a></li>
</ul>
<h2>JavaScript Models</h2>
You get a sample model for the TodoItem and TodoList, as well as a TodoListViewModel (these are located in the todoList.js file). The TodoItem function is a constructor for an object that has properties for the Todo model (Title, IsDone, TotodItemId, etc) that are mapped from the DTO passed from the Web API. It also has some additional members that are not derived form the server nor the DTO such as a save method and a ErrorMessage property. The ErrorMessage property is an observable that can be set to display valdiation information about the object. The save method defers the save to a method in the dataAcess module (more on that in a moment) which returns a promise.
<pre class="prettyprint linenums">function TodoItem(data) {
    var self = this;

    // Persisted properties
    self.TodoItemId = data.TodoItemId;
    self.Title = ko.observable(data.Title);
    self.IsDone = ko.observable(data.IsDone);
    self.TodoListId = data.TodoListId;

    // Non-persisted properties
    self.ErrorMessage = ko.observable();

    self.save = function () {
        self.ErrorMessage(null);
        return TodoApp.Db.saveItem(self)
            .fail(function () {
                var message = self.TodoItemId ? "Error updating todo item." : "Error adding todo item.";
                self.ErrorMessage(message);
            });
    };

    self.del = function () {
        return TodoApp.Db.deleteItem(self.TodoItemId)
            .fail(function () { self.ErrorMessage("Error removing todo item."); });
    };

    // Auto-save when these properties change
    self.IsDone.subscribe(self.save);
    self.Title.subscribe(self.save);
}</pre>
This is a basic CRUD example but it certainly has some great starting points that you can build from.

One thing I don't like here is that the models have awareness of how to save themselves. It's not "wrong", but I prefer my models to be data stores while another module is responsible for handling the data awareness. This Separation of Concerns means I have models that hold the data on the client and a module that handles that getting and saving of its data. I have called this other module things such as datacontext (its name in my SPA course) or datamanager in the past.
<h2>JavaScript ViewModels</h2>
The sample comes with a ViewModel named TodoListViewModel (shown below). Think of it as "The View's Model". The View needs data. The models store the data. But the data is not in the format the view needs it in. So the ViewModel pulls the data from the models together and presents it in a way that the View requires. This is also known as the Model-View-ViewModel pattern (MVVM).

The ViewModel also adds additional features such as awareness of the the models, reference to the client side data services (todoList.dataAccess.js) for getting and saving data in the models, and validation/error information. Its the presentation logic for the View.
<pre class="prettyprint linenums">function TodoListViewModel() {
    var self = this;
    self.todoLists = ko.observableArray();
    self.error = ko.observable();

    // Operations for the Todo List
    self.addTodoList = function () {
        var todoList = new TodoList({ Title: "My todos", UserId: "to be replaced" });
        self.todoLists.unshift(todoList); // Inserts on client a new item at the beginning of the array
        todoList.save();                  // Inserts on server
        todoList.IsEditingListTitle(true);
    };

    self.deleteTodoList = function (todoList) {
        todoList.del() // Deletes on server
            .done(function () { self.todoLists.remove(todoList); }); // Deletes on client
    };

    // Load initial state from server, convert it to TodoList instances, then populate self.todoLists
    TodoApp.Db.getLists()
        .done(function (allData) {
            var mappedTodoLists = $.map(allData, function (list) { return new TodoList(list); });
            self.todoLists(mappedTodoLists);
        })
        .fail(function () {
            self.error("Error retrieving todo lists.");
        });
}</pre>
<h2>Modules</h2>
The sample follows a very simple form of a module pattern. It encloses the modules (ex; models and viewmodels) in an unnamed closure to help get the modules out of the global namespace. It's a good starting practice, though I expanding on this pattern with its big brother the  Revealing Module Pattern.
<pre class="prettyprint">(function () {

// All models and viewmodels are in here

})();</pre>
<h2>Data Service</h2>
The data service (aka the todoList.dataAccess.js) module handles all of the ajax requests. So the viewmodels and models call this to get and save data. I do this in my course too in a module called dataservice.js which handles it via amplify.js (using jquery to make the ajax calls). Both my course's SPA and the sample follow this separation of data services, which I really like so it keeps the ajaxian plumbing out of my viewmodels.
<pre class="prettyprint linenums">(function () {
    window.TodoApp = window.TodoApp || {};

    // Private: Routes
    var todoListUrl = function (id) { return "/api/todolist/" + (id || "") },
        todoItemUrl = function (id) { return "/api/todo/" + (id || "") };

    // Private: Ajax helper
    function ajaxRequest(type, url, data) {
        var options = { dataType: "json", contentType: "application/json", cache: false, type: type, data: ko.toJSON(data) }
        return $.ajax(url, options);
    }

    // Public: Db methods
    window.TodoApp.Db = {
        getLists: function () {
            return ajaxRequest("get", todoListUrl());
        },

        saveList: function (todoList) {
            if (todoList.TodoListId) {
                // Update
                return ajaxRequest("put", todoListUrl(todoList.TodoListId), todoList);
            } else {
                // Create
                return ajaxRequest("post", todoListUrl(), todoList)
                    .done(function (result) {
                        todoList.TodoListId = result.TodoListId;
                        todoList.UserId = result.UserId;
                    });
            }
        },

        deleteList: function (todoListId) {
            return ajaxRequest("delete", todoListUrl(todoListId));
        },

        saveItem: function (todoItem) {
            if (todoItem.TodoItemId) {
                // Update
                return ajaxRequest("put", todoItemUrl(todoItem.TodoItemId), todoItem);
            } else {
                // Create
                return ajaxRequest("post", todoItemUrl(), todoItem)
                    .done(function (result) {
                        todoItem.TodoItemId = result.TodoItemId;
                    });
            }
        },

        deleteItem: function (todoItemId) {
            return ajaxRequest("delete", todoItemUrl(todoItemId));
        }
    };

})()</pre>
<h2>Good Starting Point</h2>
If you are looking for a starting place, this is a good choice. It gets you going quickly and provides a good foundation for you to build on. The key here is to not use this as law, but use it instead as guidelines from which you can deviate where it makes sense for you. Some deviations will be to use your own choice of libraries instead of what they (or I) prefer. Some choices will be to decide to use different separation concepts like how I prefer my models to not have a "Save" method. The goal of this template seems to be to give folks a place to start and provide them enough information to choose their own adventure beyond that. I believe it hits that mark.
<h2>Choose Your Own Adventure</h2>
My only concern is that some folks may not explore beyond the template. So where might you go from here and what deviations might you want to make? This template doesn't do it all as this wasn't its intention. Again, its a good starting point. Here is a small set of functionality that you may want to add to the SPA:
<ul>
	<li>Multiple Views</li>
	<li>Page navigation between the Views</li>
	<li>Change Tracking</li>
	<li>Synching data between Views and ViewModels</li>
	<li>Saving and restoring from Local Storage (tombstoning)</li>
	<li>Caching data on the client</li>
	<li>Filtering, sorting, paging, ordering on the client</li>
	<li>Responsive design and UI concepts</li>
	<li>Reverse ajax for server to client communications</li>
</ul>
You can add in your own custom libraries or pull in 3rd party libraries such as <a href="http://sammyjs.org/" target="_blank">Sammy</a> for navigation, <a href="http://www.breezejs.com/" target="_blank">Breeze</a> for rich data, <a href="https://github.com/SignalR/SignalR" target="_blank">SignalR</a> for reverse ajax, or <a href="http://amplifyjs.com/" target="_blank">Amplify</a> for local storage. You could use a javascript pattern to keep you organized. You could write the app with <a href="http://www.typescriptlang.org/" target="_blank">TypeScript</a> which is especially helpful if you come from a static language background or if you want to start using ECMAScript 6 features now. If you want ot learn more about TypeScript, keep an eye out on Pluralsight in December for our TypeScript course (I am co-authoring with <a href="http://twitter.com/danwahlin">Dan Wahlin</a>). If you want to see more about these features, you can check out my <a href="http://www.johnpapa.net/building-single-page-apps-with-knockout-jquery-and-web-api-ndash-the-story-begins" target="_blank">Single Page Apps blog post series</a> and my<a href="http://jpapa.me/spaps" target="_blank"> Code Camper SPA course with Pluralsight</a>.

There are a lot of directions you go from here and by no means are you done once you open this starter template which puts you on a road for your adventure. But that is the fun of a choose your own adventure.

&nbsp;
