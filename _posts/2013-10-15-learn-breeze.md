---
layout: post
title: Learn Breeze
date: 2013-10-15 14:26
author: John
comments: true
categories: [breeze, javascript, pluralsight, SPA, Uncategorized]
---
It is no secret that I am a huge fan of <a href="http://breezejs.com" target="_blank">Breeze </a>as I use it as a core component in my web applications and I use them extensively in my SPA courses. And now the first in depth training on Breeze has hit <a href="http://pluralsight.com" target="_blank">Pluralsight</a>. My friend Brian Noyes recently published his <a href="http://jpapa.me/noyesbreeze" target="_blank">Building Data-Centric Single Page Apps with Breeze</a> course and it truly is tremendous!

Brian's course covers the full gamut of what Breeze can do for you, such as formulating rich queries on the client side (filtering, sorting, and paging) that get executed on the server side, saving changes in batches, and validating changes on the client side. In modules 7 & 8 Brian dives into validation and shows how Breeze can automatically create some client validation rules for things like type checking, required fields and string length. He then shows how you can use other built in client validation rules such as phone, email, and regular expression checking as well as creating custom validation rules. The course covers Breeze, which works with Knockout/Durandal and Angular. Brian uses Knockout, but the Breeze concepts and syntax is all the same either way you want to go.

<h3>Validation</h3>
The following code snippet shows how you can hook up built-in validation rules as your Breeze EntityManager is initialized when your main page/app loads:
<pre class="prettyprint linenums">
var app = app || {};

function initValidation(em) {
    // Add phone validation rule 
    var store = em.metadataStore;
    var userType = store.getEntityType("User");
    var phoneProp = userType.getProperty("phone");
    phoneProp.validators.push(breeze.Validator.phone());

    // Add email, credit card, and URL validators
    userType.getProperty("email").validators.push(breeze.Validator.email());
    userType.getProperty("creditCard").validators.push(breeze.Validator.creditCard());
    userType.getProperty("webSite").validators.push(breeze.Validator.url());

    var userKeyValidator = breeze.Validator.makeRegExpValidator(
        "userKeyVal", 
        /^[A-Za-z0-9]{8}-[A-Za-z0-9]{4}-[A-Za-z0-9]{4}-[A-Za-z0-9]{4}-[A-Za-z0-9]{12}$/, 
        "%displayName% '%value%' is not a valid GUID");

    userType.getProperty("userKey").validators.push(userKeyValidator);

};

app.em = new breeze.EntityManager("breeze/ValDemo");

app.em.fetchMetadata().then(function () { initValidation(app.em); });
</pre>

Here you can see the demo app running with a validation error <a href="http://toastrjs.com" target="_blank">toastr</a> alert highlighting the error. By using the manual validation invocation that is demonstrated in module 8, you can block dismissing the dialog if there are any validation errors. You can also do async server calls to execute server validation rules, get back the errors and act on them or display them on the client side, all also discussed and demonstrated in the validation modules.
<img src="http://www.johnpapa.net/wp-content/uploads/2013/10/val-demo-image.jpg" alt="val-demo-image" width="600" height="447" class="aligncenter size-full wp-image-21931" />

This year (2013) I will be releasing a course that shows how to use many of these concepts in a powerful SPA built with Angular and Breeze. So I recommend watching Brian's course in preparation for my upcoming one!

