---
layout: post
title: Inside the ASP.NET Single Page Apps Template
date: 2012-12-16 00:56
author: John
comments: true
categories: [html5, javascript, knockout, mvvm, SPA, Uncategorized, visual studio 2012, web api]
---
The Single Page App (SPA) template is now available in the <a href="http://www.asp.net/vnext" target="_blank">ASP.NET and Web Tools 2012.2 (Release Candidate)</a>. This <a href="http://www.johnpapa.net/insidespatemplate/" target="_blank">SPA template has been updated since its beta release which I blogged about here</a>. Kudos to Mads Kristensen for spearheading this at Microsoft. I've been a big fan of SPA and of Mads for a while. I was thrilled to see some of my feedback (from my previous post/review) make it into this template. This post contains a complete walk through of all of the key pieces on the server and client side.
<h2>What is the Intention of the Template?</h2>
Since the beta release of the SPA template, there are a ton of small revisions that I believe make a huge difference for the better. The intent of this template appears to be to provide a great starting place for building a basic SPA with 1 view. If you want to move on from here to provide other features such as multiple views and sharing of data across those views, you can do that by pulling in other libraries like Sammy.js or Breeze.js (or choose your own favorites). The point here is that the template is a SPA sample. If you are new to SPA, and many folks are, I recommend starting with this template as a sample. Then move on to build your own, using this as a starter model.
<h2>What has changed since beta?</h2>
The biggest change is in better Separation of Concerns (SoC) and Knockout intellisense (tooling). You can check out my previous post to see what was included in the beta version of this SPA template, here. Mostly its the same overall, however the biggest changes are subtle ones. These changes make it easier for you to start with this template and be able to move beyond it by adding more of "anything". More views, more viewmodels, more libraries, more features. What are these subtle changes? Mostly they are in how the code is organized using modules. I'll explain more below, but here is a high level list of what's new:
<ul>
	<li><a href="http://www.johnpapa.net/knockout-intellisense-in-visual-studio-2012/" target="_blank">Knockout.js intellisense in HTML (refer to this post)</a></li>
	<li>Better separation of ViewModel and Model modules</li>
	<li>The Revealing Module Pattern (for modules)</li>
</ul>
<h2>Using the Template</h2>
Create a new MVC 4 Web Application and then choose the Single Page Application template.
<a href="http://www.johnpapa.net/inside-the-asp-net-single-page-apps-template/spatemplate/" rel="attachment wp-att-10471"><img class="aligncenter size-large wp-image-10471" title="spatemplate" alt="" src="http://www.johnpapa.net/wp-content/uploads/2012/12/spatemplate-600x542.png" width="600" height="542" /></a>
<h2>The View</h2>
The code below comes form the index.cshtml view inside of the Views/Home folder of the sample app. Notice it starts off with a quick check to make sure the user is authenticated. If they are not, it shows a login page (not shown below), but if they are authenticated the page displays the available Todo lists. This is a simple way to add some authentication to your app using some built in ASP.NET features.
<pre class="prettyprint">@if (@User.Identity.IsAuthenticated)
{

}</pre>
Inside of the if statement is all of the HTML and the bindings for the View. The sample below shows the HTML and Knockout bindings that begin to display all of the TodoLists. .
<pre class="prettyprint linenums">
<button data-bind="click: addTodoList">Add Todo list</button>

<section id="lists" data-bind="foreach: todoLists, 
        visible: todoLists().length">
    <article class="todoList">
        <header>
            <form data-bind="validate: true">
                <input class="required" type="text" 
                    data-bind="value: Title,
                    selected: IsEditingListTitle, 
                    blurOnEnter: true" />
            </form>
       </header>
       <a class="deletelist" href="#" 
           data-bind="click: $parent.deleteTodoList">X</a>

       <!-- SHOW TODO Items for each list here -->

       <p class="error" data-bind="visible: ErrorMessage,
           text: ErrorMessage"></p>
    </article>
</section>
</pre>
At the bottom of the View is where the JavaScript bundles are located. The bundles, created using ASP.NET's optimization features, are only retrieved if the user is authenticated. Then Knockout is loaded, jquery validation, and finally all of the custom scripts. The custom scripts are your viewmodel, model, datacontext and custom binding handlers (in the todo bundle). It's important that your scripts come last, since they likely rely on the other 3rd party scripts being loaded first.
<pre class="prettyprint linenums">@if (@User.Identity.IsAuthenticated)
{
    @section scripts {
        @Scripts.Render("~/bundles/knockout")
        @Scripts.Render("~/bundles/jqueryval")
        @Scripts.Render("~/bundles/todo")
    }
}</pre>
<h2>The Scripts</h2>
All JavaScript is contained within the Scripts folder. All custom scripts (ones you would write specific to your app) are contained within the app folder. I was glad to see this simple change to the template as I find it vastly easier to find my custom scripts without having to search through all of the scripts (including the 3rd party ones). It also makes it easier to bundle them (just grab that folder) or to automate static code analysis on that specific folder.
<a href="http://www.johnpapa.net/inside-the-asp-net-single-page-apps-template/12-15-2012-6-22-29-pm/" rel="attachment wp-att-10601"><img class="aligncenter size-full wp-image-10601" title="app folder" alt="" src="http://www.johnpapa.net/wp-content/uploads/2012/12/12-15-2012-6-22-29-PM.png" width="257" height="409" /></a>
Notice that there are only 5 custom scripts in this app.
<ul>
	<li><code class="keyword">ajaxLogin.js</code> manages auth</li>
	<li><code class="keyword">todo.bindings.js</code> contains the custom Knockout binding handlers</li>
	<li><code class="keyword">todo.datacontext.js</code> contains all remote data calls and data management</li>
	<li><code class="keyword">todo.model.js</code> defines the client side models</li>
	<li><code class="keyword">todo.viewmodel.js</code> is the glue between the View, Models and datacontext</li>
</ul>
<h2>Data Binding with Knockout</h2>
Notice some interesting data binding features, that use Knockout.js. You can create a list using Knockout's click binding which calls the addTodoList method. This method binding invokes the addTodoList method on the JavaScript ViewModel.
<pre class="prettyprint"><button data-bind="click: addTodoList">Add Todo list</button></pre>
The ViewModel also exposes a todoLists property which will be iterated over using Knockout's foreach binding. Notice the entire section is visible only if there are any todo's (using Knockout's  visible binding). It's often a good idea to use the visible binding to hide and show DOM elements instead of adding and removing them. DOM manipulation is very expensive in browsers, while hiding and show is often much faster.

You could bind the visible binding to any expression that is truthy or falsey, like this: <code>visible: todoLists().length</code>

Once inside of the view, another foreach binding is used to iterate of each todo lists's todos. Here the checked binding checks or unchecks a  checkbox, the value binding displays the values for INPUT type="text" elements, the visible binding shows or hides an error message (for validation , and the click binding calls the $parent.deletTodo method. $parent is a feature in Knockout that let's you go up one (or more) levels in the datacontext hierarchy. In this case the binding is to a single todo item. The deleteTodo  happens on the parent level (at the Todos list level), so to get there we have to reference $parent to get back up to that level first, and then delete it. You can learn more about <a href="http://knockoutjs.com/documentation/binding-context.html" target="_blank">$parent at the Knockout site</a> or in <a href="http://jpapa.me/komvvm" target="_blank">my Knockout course at Pluralsight</a>.
<pre class="prettyprint linenums">
<ul data-bind="foreach: Todos">
    <li>
        <input type="checkbox" data-bind="checked: IsDone" /> 
        <input type="text" data-bind="value: Title,
            disable: IsDone, blurOnEnter: true" />
        <a href="#" data-bind="click: $parent.deleteTodo">X</a>
    </li>
</ul>
</pre>
<h2>Custom Binding Handlers for Knockout</h2>
Also included are a few custom Knockout binding handlers, located in the <code class="keyword">/scripts/app/todo.bindings.js</code> file. I like how these are organized together so you can easily pull them in when needed and possibly find them to reuse them in another project.
<ul>
	<li>validate - invokes jQuery validation on an element</li>
	<li>selected - selects (or unselects) a DOM element based on the bound property's value</li>
	<li>blurOnEnter - loses focus when the user clicks the ENTER key</li>
	<li>placeHolder - a shim for the HTML5 placeholder for older browsers</li>
</ul>
The key here is not that actual binding handlers but rather that they show you a simple way to extend Knockout's binding structure to add your own features. I do this in my <a href="http://jpapa.me/spaps" target="_blank">Code Camper SPA course</a> to create simple handlers like escape (which performs an action when the ESCAPE key is pressed) and more complex handlers for thing s like a custom starRating control.
<h2>JavaScript Models</h2>
The Models in the new SPA template (contained in <code class="keyword">todo.model.js</code>)have a lot of great changes in them. In fact, the JavaScript is where most of the changes are. It starts with the Immediately Invoked Function Execution (IIFE) concept. IIFE wrap the entire model with a function and execute it immediately (thus the term IIFE). The code below shows the model is wrapped in function which accepts 2 parameters. These parameters are its outside dependencies: Knockout and the datacontext module (I'll get to the datacontext shortly).

Inside of the IIFE are constructor functions that create the TodoItem and TodoList objects on the client (the models). The code below shows just the TodoItem for brevity, but the real code in the template also has the TodoList.

The TodoItem function is a constructor for an object that has properties for the Todo model (Title, IsDone, TodoItemId, etc) that are mapped from the DTO passed from the Web API. It also has some additional members that are not derived form the server nor the DTO such as a save method and a ErrorMessage property. The ErrorMessage property is an observable that can be set to display validation information about the object. The save method defers the save to a method in the datacontext module (more on that in a moment) which returns a promise.
<pre class="prettyprint linenums">(function (ko, datacontext) {

    datacontext.TodoItem = TodoItem;
    datacontext.TodoList = TodoList;

    function TodoItem(data) {
        var self = this;
        data = data || {};

        // Persisted properties
        self.TodoItemId = data.TodoItemId;
        self.Title = ko.observable(data.Title);
        self.IsDone = ko.observable(data.IsDone);
        self.TodoListId = data.TodoListId;

        // Non-persisted properties
        self.ErrorMessage = ko.observable();

        self.save = function () { 
            return datacontext.saveChangedTodoItem(self); };

        // Auto-save when these properties change
        self.IsDone.subscribe(self.save);
        self.Title.subscribe(self.save);
    };
})(ko, todoApp.datacontext);</pre>
This version of the model in the latest SPA template is cleaner the the previous one because it mostly handles the members of the model. It leaves things like saving and deleting to the datacontext module. In other words, the models just know about their data but not how to get or save their data. I say "mostly" because this model still has a save method, even though it defers it to the datacontext. What would I do? In my code I tend to move that logic to the datacontext. Models know about their properties and datacontext knows how to manage the data. In this simple 1 page and 1 view sample, it's not a big deal. But when you get to larger apps, this separation can make a positive difference. I'll be exploring that in my upcoming <a href="http://www.pluralsight.com" target="_blank">Pluralsight</a> course on SPA fundamentals (date TBD).

Overall I like this form of the models much better than the previous version of the template. It practices better separation of concerns by keeping the models and viewmodels in different files and separates the logic between the viewmodel, models and datacontext much more cleanly. I addressed this in my previous post about the beta version of this SPA template and they've addressed my biggest concerns by doing this separation.
<h2>JavaScript ViewModels</h2>
The sample comes with a ViewModel named todoListViewModel (shown below). Think of it as “The View’s Model”. The View needs data. The models store the data. But the data is not in the format the view needs it in. So the ViewModel pulls the data from the models together and presents it in a way that the View requires. This is also known as the Model-View-ViewModel pattern (MVVM).
The ViewModel also adds additional features such as awareness of the the models, reference to the client side data services (todo.datacontext.js) for getting and saving data in the models, and validation/error information. It's the presentation logic for the View.
<pre class="prettyprint linenums">window.todoApp.todoListViewModel = (function (ko, datacontext) {
    var todoLists = ko.observableArray(),
        error = ko.observable(),
        addTodoList = function () {
            var todoList = datacontext.createTodoList();
            todoList.IsEditingListTitle(true);
            datacontext.saveNewTodoList(todoList)
                .then(addSucceeded)
                .fail(addFailed);

            function addSucceeded() {
                showTodoList(todoList);
            }
            function addFailed() {
                error("Save of new TodoList failed");
            }
        },
        showTodoList = function (todoList) {
            todoLists.unshift(todoList); 
            // Insert new TodoList at the front
        },
        deleteTodoList = function (todoList) {
            todoLists.remove(todoList);
            datacontext.deleteTodoList(todoList)
                .fail(deleteFailed);

            function deleteFailed() {
                showTodoList(todoList); 
                // re-show the restored list
            }
        };

    datacontext.getTodoLists(todoLists, error); // load TodoLists

    return {
        todoLists: todoLists,
        error: error,
        addTodoList: addTodoList,
        deleteTodoList: deleteTodoList
    };

})(ko, todoApp.datacontext);

// Initiate the Knockout bindings
ko.applyBindings(window.todoApp.todoListViewModel);</pre>
What changed here? This module also now implements an IIFE that wraps the entire module. The module is executed and set to a variable <code class="keyword">todoApp.todoListViewModel</code>.

In my post on the previous version of the template I pointed out that this template could benefit from using the Revealing Module Pattern. Well, in this new template the viewmodel uses the Revealing Module Pattern to help hide internal logic and expose the members that should be accessible externally. You can think of it as a way to hide private members and expose a public API. The public API is easily found by looking at lines 33-38 in the return statement. The todoListViewModel exposes an object with 4 members:
<ul>
	<li><code class="keyword">todoLists</code> is an observableArray of todo lists</li>
	<li><code class="keyword">error</code> shows error information relative to the viewmodel</li>
	<li><code class="keyword">addTodoList</code> adds a new todo list</li>
	<li><code class="keyword">deleteTodoList</code> deletes an existing todo list</li>
</ul>
So the big changes in the ViewModel are the IIFE, the Revealing Module Pattern, some camelCase cleanup on the names, and removal of the models (now in <code class="keyword">todo.model.js</code>).

This file wraps up by binding the viewmodel to the current page using Knockout's <code class="keyword">applyBindings</code> method. In a small app this is fine, but in a larger app I like to consolidate all of my <code class="keyword">applyBindings</code> method calls that link a View to a ViewModel in a single location (usually a bindings module). Why? Because then I can easily find all of my view to viewmodel bindings and I can streamline things like transitions and other common logic. (I do this in my SPA course at Pluralsight today.) But again, this is a perfectly fine way of doing it too.

I find the viewmodel to be very clean. I love how it does one thing well, and it doesn't try to define models nor does it try to figure out how to load or save data.
<h2>DataContext</h2>
The <code class="keyword">todo.datacontext.js</code> (formerly in the old template this was todoList.dataAccess.js) contains a module that manages all data http requests. When the viewmodel(s) need to perform actions on data, it can defer all of those to the datacontext (save, delete, fetch, etc). Both my course’s SPA and this sample follow this separation of data services, which I really like so it keeps the ajaxian plumbing out of my viewmodels.

Again, this module uses the IIFE and creates a module, this time named <code class="keyword">todoApp.datacontext</code>. Notice is also uses the Revealing Module Pattern to expose just the members that are needed externally. This makes it simple to figure which method you need because methods like <code class="keyword">getTotoLists</code> and <code class="keyword">saveNewTodoList</code> are easily found and the internal logic is easily ignored.
<pre class="prettyprint linenums">window.todoApp.datacontext = (function (ko) {
    var datacontext = {
        getTodoLists: getTodoLists,
        createTodoItem: createTodoItem,
        createTodoList: createTodoList,
        saveNewTodoItem: saveNewTodoItem,
        saveNewTodoList: saveNewTodoList,
        saveChangedTodoItem: saveChangedTodoItem,
        saveChangedTodoList: saveChangedTodoList,
        deleteTodoItem: deleteTodoItem,
        deleteTodoList: deleteTodoList
    };

    return datacontext;

    // Removed additional internal logic for breviity. 
    // See full template for details

})(ko);</pre>
If you go back and look at the old template, I think you'll agree that this version is considerably cleaner. Does it function the same, of course it does. But the big difference is that this code is easier to test, easier to read, and easier to expand upon.
<h2>Entity Framework DbContext</h2>
On the server they toss a very simple sample DbContext at you based on Entity Framework. You can obviously swap in and out whatever you want here.
<pre class="prettyprint linenums">public class TodoItemContext : DbContext
{
    public TodoItemContext()
        : base("name=DefaultConnection")
    {
    }

    public DbSet TodoItems { get; set; }
    public DbSet TodoLists { get; set; }
}</pre>
<h2>Server Side Models</h2>
The template comes with a series of models and Data Transfer Objects (DTO's). It's interesting that they decided to use both models and DTO's which are intended to be vessels for the models' data to send to the client.  This does offer more separation of models from DTO's but I'm not sure I'd have gone this route with a template. I'd instead start with the models and not add the DTO's til I actually needed one. (Or possibly I'd use a projection, but that's a tale for another time.)

<a href="http://www.johnpapa.net/wp-content/uploads/2012/11/todo-models.png"><img class="aligncenter size-full wp-image-8581" title="todo models" alt="" src="http://www.johnpapa.net/wp-content/uploads/2012/11/todo-models.png" width="189" height="130" /></a>
<h2>Web API Controllers</h2>
The template comes with a TodoListController and a TodoController.  They both have the [Authorize] attribute on the web api method calls, which is a good practice. The TodoListController has several methods for CRUD including a GetTodoLists (which gets all of the todo lists). It returns an IEnumerable (though with the new features it would be more interesting to return an IQueryable). Notice the code below retrieves the  Todo entities and then creates the Todo DTO's from them, before returning them to the caller. Pretty straightforward. Of course, they also have the CUD method from CRUD (Create, Update and Delete).

The only big change here is that the return type is now an IEnumerable.
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
The key takeaway here is how simple it is to set up your database, Entity Framework and API controllers to get you rock and rolling very quickly. It's a very scaled down version of what I did in my Code Camper SPA and a great starting point. So what do you do with this part of the demo? I'd start by deciding how you want your Entity Framework code to look and if you want to use it as your repository and Unit of Work or you want your own Repo and UoW on top of EF (what I did in Code Camper). Both are good choices. Next I'd decide on your structure for your Controllers. I like Separation of Concerns (SoC) and recommend making your controllers responsible for pushing and pulling data. This means making sure you don't add business logic to this layer. For that, I like the Controller to call a business manager layer who is responsible for handling all the heavy thinking. Finally, decide if you want or need custom DTO's ... I start without them and only add them if I see a need.
<h2>Should I Use This Template?</h2>
Yes, if you are new to SPA and are looking for a way to ease into it, this is a great choice. It gets you going quickly and provides a good foundation for you to build on. The key here is to not use this as law, but use it instead as guidelines from which you can deviate where it makes sense for you. Some deviations will be to use your own choice of libraries instead of what they (or I) prefer. Some choices will be to decide to use different separation concepts like how I prefer my models to not have a “Save” method. The goal of this template seems to be to give folks a place to start and provide them enough information to choose their own adventure beyond that. I believe it hits that mark and I recommend using this template for that purpose.
<h2>Choose Your Own Adventure</h2>
Once you get beyond a single page with a single view, you might want more features. For example, you want 1, 2, or more of these features:
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
	<li>Work with a static typed language like TypeScript</li>
</ul>
You can add in your own custom libraries or pull in 3rd party libraries such as Sammy for navigation, Breeze for rich data, SignalR for reverse ajax, or Amplify for local storage. There are a lot of directions you go from here and by no means are you done once you open this starter template which puts you on a road for your adventure. But that is the fun of a choose your own adventure.
<h2>How Do I Take This Further?</h2>
OK, so you want some of those features? You can start by looking at <a href="http://jpapa.me/spaps" target="_blank">my existing end to end SPA Pluralsight course</a>. Or if you want TypeScript you can keep an eye out later this month at Pluralsight for our TypeScript course (I am co-authoring with Dan Wahlin). I'll also be producing a course for Pluralsight in the beginning of 2013 on how to get started with this SPA template, aimed at SPA beginners. I'll walk through all of the pieces of the template, explain them, why they exist, how the work together, and discuss how to expand upon them.
