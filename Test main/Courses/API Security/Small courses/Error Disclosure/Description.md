Hi, I'm Anthony Aragues and in this video we're gonna be talking about Error Disclosure, or you can also think about it as air handling with a security mindset.

 

An Error Disclosure is when you have too much information in your error messages that are sent to a user's machine. It doesn't necessarily have to show up in a UI, but anything that's sent to a browser that a malicious actor can take and use to better understand what your system is in order to attack it is gonna be called an Error Disclosure. Now, handling errors is necessary as a developer, and you want to intentionally error and error out actually pretty often and early so that things that are done maliciously don't work.

But when you do that error, you wanna make sure that you're not giving away information that's going to make it easier to attack your system. This means that you're gonna want to have separate error messages for your developers to debug what's going on with the system than you're going to send to your customers.

 

Here's a good example of a bad error message. From a user interface perspective, we have a bad error message and bad. It gives away too much information. If you tell somebody that there's an invalid email address when they are typing in emails, then they know that if when they get a, the right email address is gonna give a different error, they can enumerate the users or the email addresses that are allowed.

This is a little different than what I'm talking about with Error Disclosure. This is actually going to be more commonly seen inside of your JavaScript console for your browser or if you are attacking from a development standpoint, like using Postman or you know, just your own little node JS scripts, then the error below is what is going to be seen by somebody who's consuming the API.

Now, interesting enough is these actually both came from the same interface. So one is the interface of the UI. I put in some SQL injection code and it's just going to never send it back to the API. So they did some decent protection here making sure that there's only a valid email address that's going to get sent to the API from a UI.

But if I'm writing something to the API, I don't have to respect anything that the UI said. When you are coding for the API, you need to keep in mind people could bypass the UI. Not everybody's going to use that UI, especially if they're going to be attacking your business logic or trying to get at your data.

They're gonna go directly to the API, and in this case, it's not doing the same thing. It's not very, it's not nearly as good about handling the SQL injection information. No, it didn't allow it to go through, but what it returned, Starts giving me information as to building a picture of what's behind the interface.

And in this case it told me that it's at least running Spring framework, which means that it's running Java and I can start to understand the code stack and probably some things that are associated with that because we know that certain ecosystems have. Common components and you know, this is the type of thing that you would not want to display to somebody as an error message because this isn't going to help any legitimate users, this is only going to help somebody who's thinking about it maliciously and trying to attack your system.

 

Well, it's good to understand how this typically happens. It's actually pretty simple. A common development practice is to do, try and catch blocks. In a try and catch block, you can catch the error and print it out.

And I've got two examples here, very common ones. So in Python, you've gotta try accept, and in node JS you have the try catch. In both cases, it's very common to just print the error out or return the error. And even if you don't explicitly do the try except and then send it back, a lot of systems will do this by default. If you have an uncut error, it will by default take the exception and send it back. So at least when you are intentionally doing it like this, you have more control. Where you don't have to print it out, you don't have to send it back to the user, you could log it instead. And that is probably a better option just so that it doesn't go back to the users.

So try catch block, good thing to do, gives you control over what succeeds and what doesn't. And, you know, catches a lot of things that are unexpected, but probably not a good idea to send the, the exception error back to whoever's consuming the API. Because it's going to help more than just your, your development people trying to debug it.

So as an example of why it's not a good idea to put your technology information in your error messages here we have a CVE specifically for that Spring framework that we found earlier. You know, this is the kind of thing that a malicious person's going to do, once they understand your tech stack, they're going to go look for common vulnerabilities for that tech stack and, and then also, like I said before, trying to build out what other technologies are probably in that ecosystem and then look for the vulnerabilities within those.

 

And that brings us to the general concept of everything that you're doing. You want to try to think of how can it be used maliciously. So here's another live example that I grabbed just using my own little framework with node js. It's an example of a generic error message, so this is directly against the API.



 I tried doing the same SQL injection code for Postgres. And it comes back and just says, you know, something's wrong. You, you might want to check the email ID. It'll do this no matter what I put in. And that's a good thing. And so this was for a forgot password. And it's not telling me if it wasn't the database, not in the database, it's just, hey, there's an error. If I was attacking this site, this isn't gonna help me at all. And so this is more like the example of what you want to achieve.

 

Something a little more fun and maybe not as applicable to an api. It was the brand approach. I've been seeing this a little more in the past few years and I really enjoy it. This is GitHub's 404 error. Something to note is that GitHub will give you this error even if the page exists, but you're not allowed access to it, which I like because if you don't have access to it, you don't need to know if it exists or not. So there's no reason for them to give you that information.

They are treating it from a security mindset that if you don't need to know, they're just gonna tell you it doesn't exist. But they do it with some style. You have the, the Octocat with the Star Wars name. It's pretty fun.

 

So as a quick summary. Some things that you definitely want to do is you want to error early. That's going to keep malicious attacks from progressing too far because it's going to hit something early on. Fail, send an error, hopefully a generic error that is going to keep them from getting any deeper or understanding the system better.

You wanna make sure that you include useful information for your developers and your support team, but that information should remain not visible to your customers. You might end up with an ID that ties them together and that's fine.

What you definitely do not want to do is bypass error. If you have a try-catch block with an exception you generally will want to stop on that exception. Unless it's a known one and anything else, you should stop execution.

You don't want to dev expose development information to your customers. It doesn't help them. It helps people who are attacking your system. Hopefully you've found some useful information here. Maybe some things to think about as you're developing or understanding how to correct something that already exists. There's a lot of opportunities for exceptions to make it through the cracks whenever they're found.