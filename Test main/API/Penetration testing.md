API penetration testing requires a well-developed scope, or an account
of the targets and features of what you are allowed to test, that ensures the
client and tester have a mutual understanding of the work being done.
Scoping an API security testing engagement comes down to a few factors:
your methodology, the magnitude of the testing, the target features, any
restrictions on testing, your reporting requirements, and whether you plan
to conduct remediation testing.

## Threat Modeling an API Test
There are three basic pen-
etration testing approaches: black box, gray box, and white box.

Black box testing models the threat of an opportunistic attacker—
someone who may have stumbled across the target organization or its API.
In a truly black box API engagement, the client would not disclose any
information about their attack surface to the tester. You will likely start your
engagement with nothing more than the name of the company that signed
the SOW. From there, the testing effort will involve conducting reconnais-
sance using open-source intelligence (OSINT) to learn as much about the
target organization as possible. You might uncover the target’s attack sur-
face by using a combination of search engine research, social media, public
financial records, and DNS information to learn as much as you can about
the organization’s domain. The tools and techniques for this approach are
covered in much more detail in Chapter 6. Once you’ve conducted OSINT,
you should have compiled a list of target IP addresses, URLs, and API end-
points that you can present to the client for review. The client should look
at your target list and then authorize testing.
A gray box test is a more informed engagement that seeks to reallocate
time spent on reconnaissance and instead invest it in active testing. When
performing a gray box test, you’ll mimic a better-informed attacker. You will
be provided information such as which targets are in and out of scope as
well as access to API documentation and perhaps a basic user account. You
might also be allowed to bypass certain network perimeter security controls.
Bug bounty programs often fall somewhere on the spectrum between
black box and gray box testing. A bug bounty program is an engagement
where a company allows hackers to test its web applications for vulnerabili-
ties, and successful findings result in the host company providing a bounty
payment to the finder. Bug bounties aren’t entirely “black box” because
the bounty hunter is provided with approved targets, targets that are out
of scope, types of vulnerabilities that are rewarded, and allowed types
of attacks. With these restrictions in place, bug bounty hunters are only
limited by their own resources, so they decide how much time is spent on
reconnaissance in comparison to other techniques. If you are interested in
learning more about bug bounty hunting, I highly recommend Vickie Li’s
Bug Bounty Bootcamp (https://nostarch.com/bug-bounty-bootcamp).
In a white box approach, the client discloses as much information as
possible about the inner workings of their environment. In addition to
the information provided for gray box testing, this might include access to
application source code, design information, the software development kit
(SDK) used to develop the application, and more. White box testing models
the threat of an inside attacker—someone who knows the inner workings of
the organization and has access to the actual source code. The more infor-
mation you are provided in a white box engagement, the more thoroughly
the target will be tested.

The most effective way to model a threat for a client is to conduct a
survey with them. The survey will need to reveal the client’s scope of expo-
sure to attacks, their economic significance, their political involvement,
whether they are involved in any supply chains, whether they offer essential
services, and whether there are other potential motives for a criminal to want
to attack them. You can develop your own survey or put one together from
existing professional resources like MITRE ATT&CK (https://attack.mitre.org)
or OWASP (https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_
Sheet.html).

## Which API Features You Should Test##
One of the main goals of scoping an API security engagement is to discover
the quantity of work you’ll have to do as part of your test. As such, you must
find out how many unique API endpoints, methods, versions, features,
authentication and authorization mechanisms, and privilege levels you’ll
need to test. The magnitude of the testing can be determined through
interviews with the client, a review of the relevant API documentation, and
access to API collections. Once you have the requested information, you
should be able to gauge how many hours it will take to effectively test the
client’s APIs.

## API Authenticated Testing
Determine how the client wants to handle the testing of authenticated and
unauthenticated users. The client may want to have you test different API
users and roles to see if there are vulnerabilities present in any of the dif-
ferent privilege levels. The client may also want you to test a process they
use for authentication and the authorization of users. When it comes to
6
Chapter 0Hacking APIs (Early Access) © 2022 by Corey Ball
API weaknesses, many of the detrimental vulnerabilities are discovered
in authentication and authorization. In a black box situation, you would
need to figure out the target’s authentication process and seek to become
authenticated

