## Sample Prompts

1)
```
Provide a list of scenarios where concurrent programming is useful in Go. Include small code snippets to illustrate each scenario.
```

2)
```
Provide a link to the Go documentation that explains how to use goroutines and channels.
```

3)
```
Summarize the key points at the link in your previous response.
```

4)
```
Summarize the example at this link: https://go.dev/doc/effective_go#parallel and provide a sample code snippet that demonstrates the concepts discussed in the article.
```

5)
```
What types of NoSql databases are recommended to use in a service implemented in the Go language? Identify the drivers and libraries that are commonly used to connect to these databases in Go.
```

6)
```
Review the following T-SQL stored procedure. 
- Suggest any enhancements that would improve performnce and security, and maintainability.  
- Provide a sample of the improved procedure.

CREATE PROCEDURE GetEmployeeDetailsByDepartmentName
    @DepartmentName NVARCHAR(MAX)
AS
BEGIN
    -- No error handling
    -- Dynamic SQL introduces SQL injection vulnerability
    DECLARE @Query NVARCHAR(MAX)
    SET @Query = 'SELECT e.id, e.HourlyRate, d.DepartmentName 
                  FROM HourlyEmployees e, Departments d 
                  WHERE e.id = d.EmployeeID 
                  AND d.DepartmentName = ''' + @DepartmentName + ''''

    EXEC(@Query) -- Executes the dynamic SQL
END
```

7)
```
 Generate a sample JSON array of 10 rows of sample data based on the following criteria:
- The data should include the following keys: 
employee ID (unique and random in the range 1 to 100),
department name (randomly assigned to one of the following departments: HR, Engineering, Sales),
first name,
last name,
hourly rate ($25.00 to $75.00, standard deviation of $7.65)

```

8)
```
Help me create a 'nUnit'  test for a C# class 'Corp.Employees'.
The class has a method 'HighEarners' that returns a vector of employees who earn more than 100,000.
The employee class has a name and a salary. The method should return a vector of employees who earn more than 100,000.
Edge cases:
The test should include a test case where the vector is empty, and another where the vector has one employee. In both cases, the method should return an empty vector.

The test code should be in a separate file and should use the nUnit framework.
```

9)
```
Modify the Employees class to include a HighEarners method that accepts a function expression (lambda) strategy in the form: (double) => boolean.
Update the unit test class EmployeesTests to test the modified HighEarners method.
``` 

10)
```
Help me create an 'MSTest' unit test  for a C# class 'NLP.WordMix'  that contains a public, static method 'palindrome'.
The method takes a string as an argument and returns true if the string can be read the same from right to left or left to right.
Details:
- The method should be case-insensitive
- The method should not consider spaces or punctuation
Examples:
- bob => true
- kayak => true 
- car => false
- A Santa at NASA => true
- go hang a salami I'm a lasagna hog => true

Include the code for the class and the test class that checks if a string is a palindrome. The class should be case-insensitive and ignore spaces and punctuation. Include unit tests for the class using MSTest.
```

11)
```
Create a C# class that represents the unit tested in step 10. The class should include a method that checks if a string is a palindrome. The method should be case-insensitive and ignore spaces and punctuation. Include unit tests for the class using MSTest.
```

12)
```
I am a systems architect leading a team of systems engineers. Our environment includes both Go and C# applications and services. I need advice and guidance on planning these tasks:

1. Create a cloud environment using Azure.
2. Set up a web server and a load balancer.
3. Set up a database server.
4. Configure networking (e.g., VPC, subnets, security groups).
5. Identify security measures for the infrastructure.

```