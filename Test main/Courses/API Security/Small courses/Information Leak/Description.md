Hi, I'm Anthony Aragues, the Head of APIsec Labs. In this video, we'll be talking about server information leaks. This is part of our larger series on Server Configuration security.

 A server information leak is anything that advertises your technology stack to random individuals online or your customers. It will do this through headers sent to any client that makes a request to the API or anything else that goes to the server. Sometimes this can also come from appliances or caching or your cloud provider. Anything that sends headers. And these headers are going to be beneficial for somebody to attack you by understanding what technology stack you are on.

 Here's an example we can look at together. I have Chrome opened up with DevTools in the bottom half and in DevTools I'm in Network and then Headers cuz headers is mostly what we're going to be looking at. And with Network opened up, you can see all of the different requests when you go to a webpage.

When you go to a webpage, it will do separate queries for its data, all of its API calls, its images and all that kind of stuff. So you can start browsing through these and then you can see where it went, what it sent, what kind of response headers it got.

And these ones look like it's going to Google ads. I don't know why it says server cafe, but these server response headers are what we're going to be looking at a lot. And especially ones that point to a technology that we can understand. You're not going to see a lot of really interesting ones on things that are hit so often that they have to be cached.

Although I'm not familiar with what this is. I'm going to take this and I'm going to look it up. So we'll say web server. Oh, there you go. It's a Google Web server. All right, so this is exactly what an attacking person is going to do. They're going to find clues in these headers, and they're going to go look them up and see if it's going to get them any closer to attacking the site.

 I find that I get more interesting things if I have an account somewhere. Go ahead and sign in.

Now that I'm logged in, we're going to find some things that are less cacheable. They have to go to servers, they have to go through an API, and that's more the kind of stuff I'm looking for.

Now here I start to see different things, like here's a interesting server I've never heard of called Uvicorn. I did look this up before recording the video just to show you how this process would go. Go ahead and look it up here, and we find out quickly this is an open source python. Web server. So now I have something that I have the source code for. If I'm really savvy, I might find my own issues inside the source code, or I might just find things inside the source code that I can exploit, even though they aren't security issues of themselves.

 The better that you understand the variables, the parameters, the schema of something, the more successful you can attack it. You have the source code that's not that significant on its own. But then now that I know something specific about the server, I'm going to look up the CVE. So I'll say CVE, and we'll get a list of CVEs.

So if you're not familiar with CVEs they are known vulnerabilities. So we can use that server tag to not only find the source code, but now I'm looking up specific vulnerabilities for that server. And the more unique that server is, it's not like a IIS or even Express.js, which definitely has its own vulnerabilities. The more unique it is, the more interesting it is to try to attack because it's not trafficked as much, it's not known as much, and given as much attention.

Being able to find CVEs on something that is fairly significant. And you can expect people to automatically pick up whatever they can learn from the known vulnerabilities and try to apply it to your site that gives off that server tag that says it's running that. Just to illustrate it as a slide. So we went from what we had in DevTools, we had the server tag, which doesn't do your customers any good. There's no reason they need to know what server it's on. And they're probably not opening up DevTools anyways.

 From that, we are able to get source code and known vulnerabilities. Without walking through the entire process I have found many other ones. Here's one with Nginx. Now Nginx has 168 known vulnerabilities. So it's a little more, there's more options there to try and probably less likely that individual options are gonna work, but there's a lot of stuff there to mess around with.

 Nginx is much more popular server. It's used even as a proxy or a cache. That is not as big of a finding as the one that we found before that was a more obscure Python server. But these exist everywhere. You're going to find that people don't protect this, and web servers will often just do this by default. They're going to advertise not only what server they are, but they're going to sometimes tell you what version and that gets even more dangerous.

 So in the format of a quick checklist guide, when you are looking to analyze your headers for server information leaks you want to use A client that is going to access your API. If you have a user interface that accesses the API and everything can be done like I showed in Chrome, that's fine. Or you can use something like Node.Js, it's natural ability to fetch API calls and call different methods. If you have that skillset, that's great. Or something like Postman will work as well. Anything that's going to show the headers and almost everything will if you know where to look.

And one of the key things is making sure that you get past the things that are cached. So a lot of these caching engines, they might also show up as showing their technology header, but it's not nearly as significant. What's going to be more significant is when an attacker knows that they've reached a server, they're no longer in cache-land and have to break out of there somehow. They're going to want to get into directly talking to a server, usually through an API, want to know that their responses are actually getting processed on the server, it's actually hitting SQL, it's hitting data stores and returning a response. Now they've got something that's worth trying to fuzz and inject and see what they can get back.

So the headers that are going to let them know that are the server, anything that says powered by or anything that says version. Any of these type headers are going to be something you simply want to remove.

 The way to deal with this is going to be different per web server, so I looked up a few. Like I said, I've never heard of this Uvicorn. Maybe that's just me being out of the loop on some recent stuff. I looked up how to remove the header for it, and it has a regular option on how to do it. Just when you start it up, it has a server header option. I think every server I've ever seen that has these headers has a way to turn them off very easily because it's not uncommon for people to want to remove this. This has been an issue for a long time.

Nginx, the other example I showed has a line that you put in its conf file just for turning off server token in Express or Node.js you can either run helmet, which handles a lot of basic stuff for you, or you can specifically remove headers from your requests with the remove header function.

I know that IIS and other popular web servers are going to be different. All of them are pretty easy to look up. There's nothing I tried looking up that was difficult to find. Just type in your web server that you're trying to remove the powered by header and it's going to lead you in the right direction.

 On behalf of APIsec Labs and APIsec University, thank you for joining us on this video and I'll see you in the next one.