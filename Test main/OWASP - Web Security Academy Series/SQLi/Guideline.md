## Introduction

SQL injection is a type of attack that involves inserting malicious code into a SQL statement, via input fields in an application, in order to gain unauthorized access to or manipulate a database. An SQL injection (SQLi) attack can prove extremely harmful to any application. SQL injection has been known worldwide for more than 20 years. However, attackers still use this technique to hack any organization's system through basic coding manipulation. SQLi provides attackers with unauthorized access to critical data. Attackers can access usernames, passwords, credit card details, and important personal information. This hacking technique has been behind several high-profile data breaches during the past few years. Moreover, the most alarming thing about SQLi is that hackers can maintain a backdoor into the system, which leads to constant data breaches over an extended period and remains hidden.

## Description

To better understand SQLi attacks, let's look at an example:
```sql
String query = "SELECT account_balance FROM user_data WHERE user_name = '" + request.getParameter("customerName") + "'";
```
The `customerName` parameter is being fetched from the user request and concatenated with the SQL query without being properly validated or sanitized. As a result, an attacker could inject malicious input, such as `tom' or '1'='1`, into the `customerName` parameter, which would modify the SQL query in a way that allows the attacker to access the account balances for all users.

There are several types of SQL injection attacks, which can vary in complexity and impact. Some common types of SQL injection attacks include:

- `Tautology attacks`: These attacks involve injecting a tautology, or a logical statement that is always true, into a query to bypass authentication or access restricted data.
- `Union-based attacks`: These attacks involve injecting a UNION operator into a query to combine the results of multiple queries, potentially allowing the attacker to access data from multiple tables or databases.
- `Error-based attacks`: These attacks involve injecting syntax errors or other invalid input into a query to cause the database to generate error messages, which can reveal sensitive information about the structure or content of the database.
- `Blind SQL injection attacks`: These attacks involve injecting input into a query that causes the database to perform a specific action, such as a delay or a change in output, without revealing the results of the query. This type of attack can be more difficult to detect as it does not generate error messages or other visible signs of compromise.
- `Inferential SQL injection attacks`: These attacks involve injecting input into a query that causes the database to perform a specific action, such as a delay or a change in output, which the attacker can observe and use to infer the results of the query. This type of attack can be used to extract sensitive information from a database without revealing the results of the query.
- `Second-order SQL injection attacks`: Occurs when an attacker can insert malicious data into a database and then subsequently cause the application to retrieve and execute that malicious data as if it were a legitimate SQL statement.

SQL injection vulnerabilities occur when software developers create dynamic database queries using string concatenation that includes input from untrusted sources, such as user input or already existing data in the database containing malicious code. This can allow attackers to inject malicious input that modifies the logic of the executed query, potentially allowing them to access sensitive data or perform unauthorized actions.

To prevent these types of vulnerabilities, developers can take one or both of the following steps:

- Stop writing dynamic queries using string concatenation
- Prevent user-supplied input that contains malicious SQL from affecting the logic of the executed query.

Let's explore the mitigation techniques to achieve the two goals above.

## Mitigation Techniques

### Use of prepared statements with parameterized queries

This is the **recommended** mitigation technique to protect against SQLi attacks. Prepared Statements (with Parameterized Queries) should be used instead of dynamic queries. There are two concepts to consider in this mitigation technique:

- `Prepared statements` are a feature of the database management system and ensure that an attacker is not able to change the intent of a query, even if SQL commands are inserted.
- `Parameterized queries` are a technique for writing database queries in which placeholders are used to specify the location of user input, and the input is passed as separate parameters. This approach helps to prevent SQL injection vulnerabilities by separating the code and data in the query and by ensuring that user input is properly validated and sanitized before it is included in the query.

To properly implement this mitigation technique, use prepared statements with parameterized queries.

This technique should also be used to protect against _Second-order SQL injection attacks_, where an attacker is able to insert malicious data into a database, and then subsequently cause the application to retrieve and execute that malicious data as if it were a legitimate SQL statement. The SQL query using the data stored into the database should also use prepared statements with parameterized queries to prevent injection attacks.

### Use parameterized stored procedures

A stored procedure is a precompiled collection of SQL statements that can be executed on a database server. By using stored procedures, it's possible to encapsulate SQL statements and pass parameters to them rather than concatenating raw SQL strings in the code. This can make it more difficult for an attacker to inject malicious input into the SQL statements, because the attacker would have to modify the stored procedure itself in order to exploit it.

The difference between prepared statements and stored procedures is that the SQL code for a stored procedure is defined and stored in the database itself and then called from the application.

### Validating and sanitizing user input

Prepared statements can help protect against SQL injection attacks by allowing the separation of data being input into the database from the SQL command being used to insert it. However, prepared statements do not provide any protection against other types of injection attacks or against invalid data.

Therefore, it is still important to validate user input to ensure that it is of the correct type and format and does not contain any malicious code. This can help prevent issues such as:

- Storing invalid or incorrect data in a database.
- Displaying unexpected or malformed data to users.
- Causing errors or unexpected behavior in an application.

For example, if it's expected that a user will input a number, it should be verified that the input is actually a number before using it in a SQL query or storing it in a database.

In summary, while prepared statements can help protect against SQL injection attacks, they should not be relied on as the sole means of input validation and protection against injection attacks. It is important to validate user input and use other security measures as well.

## Java

In Java, native database access is primarily achieved through the [Java Database Connectivity (JDBC) API](https://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/), which allows developers to interact with a wide range of databases using SQL queries. While JDBC provides a powerful and flexible way to manage data, it can also expose applications to SQL injection attacks if not used properly. SQL injection is a common security vulnerability where attackers can manipulate SQL queries by injecting malicious code through user inputs. These attacks can lead to unauthorized data access, data manipulation, or even complete control over the database.

By following the recommendations below, you can significantly decrease the likelihood of such attacks:

- **Validate and Sanitize User Input**: always validate and sanitize user input before using it in SQL queries. Apply appropriate constraints on input length, data type, format, and allowed characters. Be cautious when using data from untrusted sources like user input, cookies, or HTTP headers. Additionally, there are some special characters that have particular meanings when used with the `LIKE` statement in SQL. The some common special characters are `%`, `_`, and `\`. If these characters are present in the `searchTerm` provided by the user, they could potentially change the behavior of the `LIKE` statement, as they would be interpreted as wildcards instead of literal characters. To avoid this, you should escape these characters in the `searchTerm` before using them in the query.

```java
// user input is stored in searchTerm
String escapedSearchTerm = searchTerm.replace("\\", "\\\\").replace("%", "\\%").replace("_", "\\_");

if (escapedSearchTerm.length() > 100) {
    throw new IllegalArgumentException("Search term must be at most 100 characters.");
}
```
**Use Prepared Statements (with parameterized queries)**: prepared statements help avoid SQL injection by separating the SQL query structure from its parameters, making it harder for an attacker to inject malicious code. Use the PreparedStatement class in JDBC to create and execute parameterized queries. When using prepared statements, the SQL query is precompiled with placeholders for the parameters. These placeholders are then replaced with actual parameter values when the query is executed. Since the query structure is already defined and compiled, the database engine can't be tricked into executing a different query or interpreting the parameter values as SQL code.

```java
// user input is stored in searchTerm

String query = "SELECT * FROM contacts WHERE message LIKE ?";
PreparedStatement preparedStatement = connection.prepareStatement(query);
String escapedSearchTerm = searchTerm.replace("\\", "\\\\").replace("%", "\\%").replace("_", "\\_");
preparedStatement.setString(1, "%" + escapedSearchTerm + "%");
ResultSet resultSet = preparedStatement.executeQuery();
```
- In this example, the `?` is a placeholder for the `escapedSearchTerm` parameter. When you call `preparedStatement.setString(1, "%" + escapedSearchTerm + "%")`, the `escapedSearchTerm` is safely bound to the placeholder, and any special characters within the `escapedSearchTerm` are escaped and quoted as necessary. This process ensures that the database engine interprets the `escapedSearchTerm` strictly as data, not as SQL code, preventing SQL injection attacks.
    
- **Use Parameterized Queries in Stored Procedures**: implementing stored procedures can help improve the organization and efficiency of your database operations. However, it is the use of parameterized queries within stored procedures that can help prevent SQL injection attacks. By encapsulating SQL code within the database and separating it from the application code, stored procedures can provide a structured and reusable approach to handling database operations. When using stored procedures, it's crucial to pass parameters safely, similar to how you would with prepared statements, in order to mitigate the risk of SQL injection attacks. Remember that using stored procedures alone does not guarantee complete protection against SQL injection attacks; it's the proper handling of user input and parameter passing that makes the difference.

```java
DELIMITER //
CREATE PROCEDURE find_contacts_by_message(IN search_term VARCHAR(255))
BEGIN
    SELECT * FROM contacts WHERE message LIKE CONCAT('%', REPLACE(REPLACE(REPLACE(search_term, '\\', '\\\\'), '%', '\\%'), '_', '\\_'), '%');
END //
DELIMITER ;
```
```java
import java.sql.*;

public class StoredProcedureExample {
    public static void main(String[] args) {
        // Code omitted
        // Fetch dbURL, user, password

        try (Connection connection = DriverManager.getConnection(dbUrl, user, password)) {
            String searchTerm = "example";

            // Validate and sanitize searchTerm here

            // Call the stored procedure
            CallableStatement callableStatement = connection.prepareCall("{call find_contacts_by_message(?)}");
            callableStatement.setString(1, searchTerm);
            ResultSet resultSet = callableStatement.executeQuery();

            // Process the result set
            while (resultSet.next()) {
                int id = resultSet.getInt("id");
                String message = resultSet.getString("message");
                System.out.println("Contact ID: " + id + ", Message: " + message);
            }
        } catch (SQLException e) {
            // Handle the SQLException
        }
    }
}
```
- In the Java code above, we use `CallableStatement` to call the `find_contacts_by_message` stored procedure. The `searchTerm` is passed as a parameter, and the stored procedure returns a result set of contacts with messages containing the search term. The `CallableStatement` separates the SQL code from the parameters, making it difficult for an attacker to inject malicious code through user input. This approach, combined with input validation and sanitization, helps mitigate the risk of SQL injection attacks.
    

### Insecure Code Example

This code snippet will search for all Contacts containing a search term in the Message field.

```java
// Contact.java
public class Contact {
    private long id;
    private String message;

    public Contact(long id, String message) {
        this.id = id;
        this.message = message;
    }

    // Getters and setters
}

// Database.java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class Database {
    // Code omitted
    // Fetch database url, user, password

    public List<Contact> findBySearchTerm(String escapedSearchTerm) {
        String query = "SELECT * FROM contacts WHERE message LIKE '%" + escapedSearchTerm + "%'";
        List<Contact> contacts = new ArrayList<>();

        try (Connection connection = DriverManager.getConnection(url, user, password)) {
            Statement statement = connection.createStatement();
            ResultSet resultSet = statement.executeQuery(query);

            while (resultSet.next()) {
                long id = resultSet.getLong("id");
                String message = resultSet.getString("message");
                contacts.add(new Contact(id, message));
            }
        } catch (SQLException e) {
            // Log the error if needed
            throw e;
        }

        return contacts;
    }
}

// ContactController.java
import java.util.List;

public class ContactController {
    private final Database database;

    public ContactController() {
        this.database = new Database();
    }

    public void search(String searchTerm) {
        // Code omitted
        // searchTerm input validation as per business rules

        String escapedSearchTerm = searchTerm.replace("\\", "\\\\").replace("%", "\\%").replace("_", "\\_");

        try {
            List<Contact> contacts = database.findBySearchTerm(escapedSearchTerm);

            for (Contact contact : contacts) {
                System.out.println("Contact ID: " + contact.getId() + ", Message: " + contact.getMessage());
            }
        } catch (SQLException e) {
            // Handle the SQLException
        }
    }
}
```

The provided example is vulnerable to SQL injection because it directly concatenates the user input (`searchTerm`) into the SQL query string without any validation or parameterization. This allows an attacker to potentially inject malicious SQL code through the `searchTerm` input, which could compromise the security and integrity of the database.

### Secure Code Example

This code snippet will search for all Contacts containing a search term in the Message field.

```java
// Contact.java
public class Contact {
    private long id;
    private String message;

    public Contact(long id, String message) {
        this.id = id;
        this.message = message;
    }

    // Getters and setters
}

// Database.java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class Database {
    // Code omitted
    // Fetch database url, user, password

    public List<Contact> findBySearchTerm(String escapedSearchTerm) {
        String query = "SELECT * FROM contacts WHERE message LIKE ?";
        List<Contact> contacts = new ArrayList<>();

        try (Connection connection = DriverManager.getConnection(url, user, password)) {
            PreparedStatement preparedStatement = connection.prepareStatement(query);
            preparedStatement.setString(1, "%" + escapedSearchTerm + "%");
            ResultSet resultSet = preparedStatement.executeQuery();

            while (resultSet.next()) {
                long id = resultSet.getLong("id");
                String message = resultSet.getString("message");
                contacts.add(new Contact(id, message));
            }
        } catch (SQLException e) {
            // Log the error if needed
            throw e;
        }

        return contacts;
    }
}

// ContactController.java
import java.sql.SQLException;
import java.util.List;

public class ContactController {
    private final Database database;

    public ContactController() {
        this.database = new Database();
    }

    public void search(String searchTerm) {
        // Code omitted
        // searchTerm input validation as per business rules

        String escapedSearchTerm = searchTerm.replace("\\", "\\\\").replace("%", "\\%").replace("_", "\\_");

        try {
            List<Contact> contacts = database.findBySearchTerm(escapedSearchTerm);

            for (Contact contact : contacts) {
                System.out.println("Contact ID: " + contact.getId() + ", Message: " + contact.getMessage());
            }
        } catch (SQLException e) {
            // Handle the SQLException
        }
    }
}
```

The provided example is safe against SQL injection because it uses prepared statements with parameterized queries to handle user input. The prepared statements separate the SQL query structure from its parameters, ensuring that user input is treated strictly as data and not as SQL code.

---

## References & Resources

- OWASP:
    - [OWASP Top 10 A03:2021 – Injection](https://owasp.org/Top10/A03_2021-Injection/)
    - [OWASP Cheat Sheet Series - SQL Injection Prevention](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
- CWE
    - [CWE-20](https://cwe.mitre.org/data/definitions/20.html)
    - [CWE-89](https://cwe.mitre.org/data/definitions/89.html)