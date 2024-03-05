
Hi, I'm Anthony Aragues with APIsec Labs. In this video, we will cover CORS also known as Cross Origin Resource Sharing. It's one of the most common vulnerabilities we find and not often well understood. CORS is just a set of suggestions for how browsers are allowed to serve content. Those suggestions come from where the content is provided.

So if you have an API server, it's on your API server that's going to say how people are allowed to use that content. And it's the browsers that have to respect it, courses will define what is allowed to be called from where.

So the what can be end points and methods, things like post and git and you know things of that nature and where it can be called from. So your UI that is intended to call an API is going to be allowed by that API.

But then if somebody else tries to point to your API because you don't know - that you can block that - because it's not on the allowed list and you can do that for individual endpoints and some end points. You might allow very free and open access to as long as you know, that that's not going to be protected or it can be misused.



CORS is a pretty basic security configuration for a web server. It can feel like it gets in the way sometimes, especially when you're doing development and your local host is not allowed to communicate with an API - like you're developing a new UI and you want to communicate with the production API, which is pretty common scenario. If that production API doesn't allow you to use it from local host and you're gonna get these CORS errors and it just feels like it's in the way - those restrictions are good for when you don't want people to impersonate you, you don't want people to use your branding or your intellectual property, or for them to set up different scenarios where unsuspecting users think that they are going to your site, but they're going to a different one using the data for your site and your API through theirs and CORS can help you protect against this stuff.



It's key to understand that CORS is not going to protect you from direct attacks.

So I drew up this diagram to show you that if a malicious system is going to talk directly to your API, it can ignore CORS because CORS sits in the browser and it sends signals to the browser and the browser has to respect it.

So if somebody's directly attacking your API, they, they're not gonna respect anything that it says that you can or can't do with their content. It's only the browsers that are going to respect this at all. And that's why this is specifically for the scenarios of your unsuspecting users going to a malicious site or mixed use site and using your API or your content in a way that you wouldn't normally approve of.



So how do we get into these situations? I kind of alluded to it before, but I've been in this situation many times where you, you're creating something new, you have a new product, a new API - you run into the CORS error and it's usually the "allow origin" error.

You then go search Stack Overflow or something for "how do I get past as error?" Very common, you just copy and paste an error. And one of the first things that comes up, one of the most common responses in the search engines is to just OK.

You know, for something like node JS express to install this little thing called COR - the very first example is to just allow everything. If you do that, you automatically get past the error, you probably forget about it. And the thing makes it all the way to production and the these protections are never put back in place.

So if you're running into this issue because of a security scanner or a security audit of some sort - this is likely the root cause and understanding this root cause could help you understand how to prevent it in the future. 



It can help to show things in a couple of different ways. So here's something I cooked up in order to show one of the common misuses of a site that course can help you with. Let's assume everything in a blue server is something that is protected and expected, and everything in the red server is something malicious - if you end up going to a malicious site, which is why the whole screen is red, it points to an API such as one that you want to protect. If that API has the access control "allow origin" header as a wild card, this star which I show over the servers, then that server is going to allow that transaction to happen.



So in the same scenario, the API server now has an access control allow origin of blue dot com. So it's specifying that only blue dot com is allowed to access this API or anything on the server. So when a user ends up going to the malicious site and it tries to make a call to the API on blue dot com, it's blocked because the browser is not gonna allow them to make that mix, make that request from red dot com.



Here's a slightly different scenario where the roles are reversed - for whatever reason you have content on red dot com that is embedded in the site for blue dot com. There's a number of reasons this could happen, whether the site was compromised or there's ways that were easy to inject content. A lot of older content management systems would allow this and didn't really check for it and it's been abused heavily. So for whatever reason, your users are going to your site and there is a bad element within that site that is pointing them to a malicious server. If you don't set the Cross Origin Resource policy, then it's going to allow this. 



So if you set the Cross Origin Resource policy to same site, then when your user goes to your site and it reaches that content that's trying to go to the malicious site, it's not going to get there. It's going to be blocked at the browser, based on your header that you set for the Cross Origin Resource policy. This is what you want. 



Here's a solution to the same framework that we did the stock overflow issue with. But in this resolution by applying this library called helmet instead of the other one called cos - this one will automatically apply a lot of security configurations for you to be best standards and it will get you past most of the basic things. It does include CORS - it goes beyond that a little bit, and I would recommend express starting with this if you have an Express JS application. It will save you some headaches in the future and plug up a lot of common holes that you may have created.