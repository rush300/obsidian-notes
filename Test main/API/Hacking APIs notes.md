> [!IMPORTANT]- Broken Object Level Authorization
> One of the most prevalent vulnerabilities in APIs is broken object level authorization (BOLA). BOLA vulnerabilities occur when an API provider allows an API consumer access to resources they are not authorized to access. If an API endpoint does not have object-level access controls, it won’t perform checks to make sure users can only access their own resources. When these controls are missing, User A will be able to successfully request User B’s resources.

> [!IMPORTANT]- Broken User Authentication
> Broken user authentication refers to any weakness within the API authentication process. These vulnerabilities typically occur when an API provider either doesn’t implement an authentication protection mechanism or implements a mechanism incorrectly.

> [!IMPORTANT]- Excessive Data Exposure
> Excessive data exposure is when an API endpoint responds with more information than is needed to fulfill a request. This often occurs when the provider expects the API consumer to filter results; in other words, when a consumer requests specific information, the provider might respond with all sorts of information, assuming the consumer will then remove any data they don’t need from the response. When this vulnerability is present, it can be the equivalent of asking someone for their name and having them respond with their name, date of birth, email address, phone number, and the identification of every other person they know.

> [!IMPORTANT]- Lack of Resources and Rate Limiting
> One of the more important vulnerabilities to test for is lack of resources and rate limiting. Rate limiting plays an important role in the monetization and availability of APIs. Without limiting the number of requests consumers can make, an API provider’s infrastructure could be overwhelmed by the requests. Too many requests without enough resources will lead to the provider’s systems crashing and becoming unavailable—a denial of service (DoS) state.

> [!IMPORTANT]- Broken Function Level Authorization
> BFLA is similar to BOLA, except instead of an authorization problem involving accessing resources, it is an authorization problem for performing actions. For example, consider a vulnerable banking API. When a BOLA vulnerability is present in the API, you might be able to access the information of other accounts, such as payment histories, usernames, email addresses, and account numbers. If a BFLA vulnerability is present, you might be able to transfer money and actually update the account information. BOLA is about unauthorized access, whereas BFLA is about unauthorized actions.
> The easiest way to discover BFLA is to find administrative API documentation and send requests as an unprivileged user that test admin functions and capabilities.

> [!IMPORTANT]- Mass Assignment
> Mass assignment occurs when an API consumer includes more parameters in their requests than the application intended and the application adds these parameters to code variables or internal objects. In this situation, a consumer may be able to edit object properties or escalate privileges.

> [!IMPORTANT]- Security Misconfigurations
> Security misconfigurations include all the mistakes developers could make within the supporting security configurations of an API. If a security misconfiguration is severe enough, it can lead to sensitive information exposure or a complete system takeover. For example, if the API’s supporting security configuration reveals an unpatched vulnerability, there is a chance that an attacker could leverage a published exploit to easily “pwn” the API and its system.





 




