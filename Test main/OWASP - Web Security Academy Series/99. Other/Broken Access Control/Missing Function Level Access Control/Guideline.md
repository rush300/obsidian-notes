## Introduction

Missing function level access control is a security vulnerability that occurs when an application does not properly restrict access to certain sensitive functions. This can allow attackers to gain unauthorized access to sensitive information or perform actions that they should not be able to. Function level access control is a fundamental security principle that ensures that only authorized users are able to access sensitive functions or data within an application. This vulnerability is part of the OWASP Top 10 A01:2021 Broken Access Control category and represents one of the most serious web application security risks.

## Description

When an application has insufficient authorization checks for sensitive endpoints, malicious users can execute actions aimed at administrators or privileged users. The impact of this vulnerability will depend on the functionality implemented by the unprotected endpoint, ranging from information disclosure to full system compromise.

For example, an endpoint like `/users`, which allows the retreival of the list of application users, should only be accessible to administrators or users with the corresponding role as per business rules. Hiding this endpoint in the web UI for regular users is not sufficient protection, as attackers can easily discover it and gain access to sensitive information.

Function level access control is typically implemented using RBAC (Role-Based Access Control) techniques. The application defines a set of roles like 'Admin', 'Moderator', 'User', etc. These roles are then checked when trying to access privileged endpoints to ensure the user has the required permissions as per business rules. Failing to check these permissions would allow, for example, a regular 'User' to get access to privileged endpoints aimed for an 'Admin' role.

## Mitigation Techniques

### Use deny by default principle

Except for public endpoints, the "deny by default principle should always be applied. Application endpoints should be restricted by default, and access should be granted explicitly.

### Use least privilege principle

When assigning permissions to users, only the minimum required permissions to carry out the business tasks should be assigned.

### Validate the permissions on every request

The application should validate every request it receives to ensure the user has the proper permissions to access the endpoint. Whenever possible, it is preferred to implement these checks on an application-wide configuration approach rather than individually for each method or class.

### Do not rely on hidden URLs or APIs

Applying a "security by obscurity" approach is not recommended. Hiding privileged endpoints will not protect the application against these vulnerabilities. Attackers can discover the endpoints and get access to privileged actions.

## Pseudocode

In order to properly mitigate missing function level access control vulnerabilities, it is important to ensure that sensitive endpoints contain access control checks to allow only authorized users.

There are public endpoints like `/login` that require no authorization as they should be accessible to anonymous users trying to log into our application.

Endpoints like `/logout` should require users to be authenticated before they can log out of the application.

Finally, other sensitive endpoints that allow access to privileged actions, like getting the list of application users via `/users` endpoint, should require that the user requesting the action has the appropriate role assigned.

### Insecure Code Example

The code snippets below contains some HTTP endpoints for `/login`, `/logout`, and `/users` with the corresponding authorization controls.

```pseudocode
-- "/login"
Define method login with argument request
    -- Handle login operation
End method

-- "/logout"
Define method logout with argument request
    Fetch session from request
    If session is None then
        Return "User is not authenticated!"
    End if

    -- Handle logout operation
End method

-- "/users"
Define method getListOfUsers with argument request
    Fetch session from request
    If session is None then
        Return "User is not authenticated!"
    End if

    -- Return list of users
End method
```

This example is insecure because the application is missing some function level access control checks to ensure that only authorized users can access the privileged endpoint '/users'. Currently, any logged-in user can get the full list of application users.

### Secure Code Example

The code snippets below contain some HTTP endpoints for `/login`, `/logout`, and `/users` with the corresponding authorization controls.

```pseudocode
-- "/login"
Define method login with argument request
    -- Handle login operation
End method

-- "/logout"
Define method logout with argument request
    Fetch session from request
    If session is None then
        Return "User is not authenticated!"
    End if

    -- Handle logout operation
End method

-- "/users"
Define method getListOfUsers with argument request
    Fetch session from request
    If session is None then
        Return "User is not authenticated!"
    End if

    Fetch user from session
    -- Get the user roles from the database
    Call internal.GetUserRoles with argument user
    Save it as userRoles

    If userRoles does not contain "Admin" then
        Call internal.GenerateLogRecord with arguments (user, "The user tried to access a privileged endpoint without authorization")
        Return "User is not authorized!"
    End if

    -- Return list of users
End method
```
This example is secure because the privileged endpoint '/users' requires that users are authenticated and that they have the 'admin' role assigned.

---

## References & Resources

- OWASP:
    - [OWASP Top 10 A01:2021 – Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)
    - [OWASP Cheat Sheet Series - Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)
    - [OWASP ASVS - V4 Access Control](https://github.com/OWASP/ASVS/blob/v4.0.3/4.0/en/0x12-V4-Access-Control.md)
- CWE
    - [CWE-862](https://cwe.mitre.org/data/definitions/862.html)
    - [CWE-280](https://cwe.mitre.org/data/definitions/280.html)