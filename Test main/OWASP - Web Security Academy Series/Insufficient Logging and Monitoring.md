## Introduction

This vulnerability refers to the lack of proper logging and monitoring mechanisms in an application, which can lead to difficulty in detecting and responding to security incidents, such as unauthorized access, data breaches, or malicious activity. Adequate logging and monitoring are essential for security investigations and incident response, as they provide valuable information about what happened and when, helping organizations to quickly identify and remediate threats.

## Description

When an application fails to properly generate records for logging and monitoring operations, attackers can execute malicious activities within the application without being detected. Without proper logging, organizations may be unable to determine what happened during a security incident, making it difficult to determine the cause, scope, and impact of the incident. Logging must be comprehensive, capturing all relevant information about security-related events, such as authentication attempts, authorization decisions, data access and manipulation, and system configuration changes.

What is insufficient logging and monitoring within an application:

- Key security events, such as logins, failed logins, and high-value transactions, are not recorded in logs.
- The information recorded in the logs is insufficient or unclear.
- Log records are not stored in a secure and appropriate location to ensure their availability and accessibility in case of security incidents.
- Not logging exceptions can decrease the system's visibility and result in a lack of information about what happened. For instance, if an optional service is down, the system should log the fact that it tried to reach the service, failed, and continued so that it can be reviewed later and appropriate actions can be taken. Logging exceptions helps developers to understand how the system is performing, identify issues and bugs, and troubleshoot problems that may arise.

Below are some best practices that can help ensure better logging and monitoring.

## Mitigation techniques

### Provide meaningful information

By providing meaningful information, the logs can help detect, diagnose, and respond to security incidents, as well as support compliance requirements. At a minimum, they should include answers to:

- When did the event happen?
    
    - Include a timestamp in the log entries.
- Where did the event happen?
    
    - Include an application/component identifier to help locate where the event happened.
- Who performed the action?
    
    - Include an identifier of the entity performing the action (user, service, ...).
- What happened?
    
    - Include the type of the event (authentication failure, successful authentication, ...).
    - Include the severity of the event (debug, info, warning, ...). This describes how important or critial is the event.
    - Include a description with additional details.

Logging full stack traces can be useful for troubleshooting and debugging, but there are a few considerations to keep in mind when developing a logging strategy:

- Full stack traces can be very large and can quickly consume a significant amount of storage space. As a result, it may be more practical to log only a subset of the stack trace or to limit the number of full stack traces that are logged.
- Full stack traces can contain sensitive information, such as file paths and function names, that could be exploited by attackers. As a result, it is important to consider whether the potential benefits of logging full stack traces outweigh the security risks.
- Logging full stack traces can clutter up log files, making it more difficult to locate and analyze specific log events. This can be mitigated by logging full stack traces only when necessary (such as during troubleshooting or debugging), and using a different log destination (file, database, ...).

### Generate log records for key events

There is no one-size-fits-all answer to the question of what events to log in an application, as the specific events to be logged will depend on the nature and purpose of the application. However, some general recommendations for which events to log in an application are:

- Any events that relate to security, such as user authentication, authorization, and access control. This includes successful and unsuccessful login attempts, user permissions changes, and any actions that could potentially compromise security.
    
- Any events that are critical to the functioning of the business, such as payment transactions, order processing, and customer account updates.
    
- Any events that indicate an error or exception has occurred, such as system exceptions, unhandled and handled errors, and application crashes.
    

### Use an appropriate log destination

The recommended log destinations for application logging depend on the needs and requirements of the organization and its applications. However, some common log destinations for application logging include:

- Local storage: logs can be stored locally on the same machine as the application, either in a file or a database. This is a simple and straightforward option, but it may not be suitable for larger or distributed systems as there are a few caveats. One of them would be the lack of visibility and monitoring. Another one would be the consideration of disk space and log rotation because log files can quickly consume a large amount of space on a server. Log files can become outdated and take up unnecessary space and excessive logging can also cause performance issues. By implementing log rotation, you can ensure that your log files do not grow indefinitely, freeing up space for new logs, and potentially improve performance by spreading out the logging activity over multiple files. Overall, it is important to implement a log rotation strategy that balances the need for log data with the need to conserve disk space, prevent performance issues, and address security concerns.
    
- Remote storage: logs can be stored on a remote server or in a centralized logging system, such as a log server or log management tool. This allows for easy access to log data from multiple systems and can make it easier to centralize log analysis and reporting.
    

Additionally, and depending on the execution environment, the application can simply send the log events to the stdout. The execution environment will be responsible for collecting the logs and sending them to an appropriate location (like a centralized log collection and management system). Some examples for these execution environments would be:

- In containerized environments, such as Docker, the logs generated by applications running in containers can be collected and managed using a centralized log collection and management system like Fluentd or Logstash.
- In Unix-like systems, the logs can be redirected to the syslog service, which provides a centralized logging mechanism for all applications. The syslog service can be configured to rotate logs, compress old logs, and store them in a specific location.
- In cloud environments, such as Amazon Web Services (AWS) or Google Cloud Platform (GCP), the logs generated by applications running on virtual machines can be collected and managed using a centralized log collection and management system like Amazon CloudWatch Logs or Google Stackdriver Logging.

The choice of log destination will depend on the scale and complexity of the application and the organization's requirements for log storage, analysis, and reporting. When possible, it is recommended to use a combination of log destinations to ensure that logs are stored in multiple locations for redundancy and to meet regulatory or compliance requirements.

### Avoid logging sensitive information

To ensure the protection of sensitive information, it is recommended that certain types of data should not be directly recorded in the logs. Instead, such data should be removed, masked, sanitized, hashed, or encrypted. Examples of data that should be treated in this way include:

- Application source code.
- Session identification values (which may be replaced with hashed values for tracking purposes).
- Credentials like access tokens, authentication passwords, database connection strings, etc.
- Encryption keys.
- Personally identifiable information (PII) like name, medical records, social security number, etc.
- Payment card holder information.

In addition, commercially-sensitive information, information that is illegal to collect, and information that a user has opted out of collecting or not consented to should also be treated in the same manner.

### Implement proactive log monitoring for better security

Implement a proactive monitoring system that can detect and alert on anomalies or suspicious activities in the log data. This can include setting up alerts or triggers for specific events or patterns that indicate potential security breaches, such as repeated failed login attempts or unusual levels of user activity. Regularly reviewing and analyzing log data can also help to identify potential risks or vulnerabilities in the system, and enable prompt response and remediation.

## Pseudocode

Logging and monitoring are an essential part of any application, allowing developers to track and investigate security incidents, errors, etc. When using logging in a programming language, there are some general recommendations to follow:

- Setting appropriate log levels for each log message. For example, logging successful and failed authentication attempts, access to sensitive resources, and other potentially malicious activity can help identify and respond to security incidents.
- Using consistent and meaningful log messages.
- Avoiding logging sensitive information. This includes avoiding logging passwords, user credentials, and other personally identifiable information (PII). If sensitive information must be logged, it should be encrypted or masked to prevent unauthorized access. Additionally, and depending on the business case, another recommended approach could be to set a TTL (Time to live) on logs that could contain PII and also to implement PII filtering when searching logs to avoid information exposure.
- And regularly reviewing and maintaining the logging code.

In addition, it is also a good practice to log in a structured format, such as JSON, to facilitate searching and analysis of logs. This can help identify patterns of suspicious activity or anomalies that may indicate a security breach.

For some languages/frameworks, the native logging solution will be sufficient for these needs. However, in most cases, the use of a specialized third-party library will be required. When selecting a third-party logging library, it is important to consider factors such as the library's functionality, compatibility with the programming language and framework being used, community support, and documentation.

Finally, it is important to ensure that logs are stored securely and not accessible to unauthorized users. This may involve encrypting log files, limiting access to log files, or sending logs to a centralized logging system that is secured and monitored.

### Insecure Code Example

The code snippet below contains a simplified example to log all security-relevant events during the login process.

```pseudocode
Define method login with arguments (username, password)
    -- Code omitted
    -- Perform input validation
    -- Apply rate limiting and anti-automation measures
    -- Fetch 'user' based on input parameters
    -- ...
    If user does not exist then
        Return "Either username or password are incorrect"
    End if

    -- Code omitted for password validation
    -- ... 
    If not validPassword then
        Return "Either username or password are incorrect"
    End if

    -- Code omitted
    -- Persist login information to session

    Set message to "User " + user.userId + " has successfully logged in"
    Call internal.logInfoLevel with argument message

    -- Redirect to main page
    Call internal.RedirectTo with argument page="MainPage"
End method
```

This example is vulnerable to insufficient logging because it is only registering the events when the user successfully logs in. However, it does not log any event when the username or password is incorrect, which would help determine if an enumeration attack is being performed.

### Secure Code Example

The code snippet below contains a simplified example to log all security-relevant events during the login process.

```pseudocode
Define method login with arguments (username, password)
    -- Code omitted
    -- Perform input validation
    -- Apply rate limiting and anti-automation measures
    -- Fetch 'user' based on input parameters
    -- ...
    If user does not exist then
        Set message to "User login failed."
        Call internal.logWarningLevel with argument message
        Return "Either username or password are incorrect"
    End if

    -- Code omitted for password validation
    -- ... 
    If not validPassword then
        Set message to "User login failed: incorrect password for user " + user.userId
        Call internal.logWarningLevel with argument message
        Return "Either username or password are incorrect"
    End if

    -- Code omitted
    -- Persist login information to session

    Set message to "User " + user.userId + " has successfully logged in"
    Call internal.logInfoLevel with argument message

    -- Redirect to main page
    Call internal.RedirectTo with argument page="MainPage"
End method
```

This example is not vulnerable to insufficient logging because it is registering the events when the username is incorrect, when the password is incorrect, and when the user successfully logs in. This log information would help to determine if an attacker is performing username or password enumeration attacks, for example.

---

## References & Resources

- OWASP:
    - [OWASP Top 10 A09:2021 - Security Logging and Monitoring Failures](https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/)
    - [OWASP Cheat Sheet Series - Logging](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)
- CWE
    - [CWE-778](https://cwe.mitre.org/data/definitions/778.html)
    - [CWE-223](https://cwe.mitre.org/data/definitions/223.html)