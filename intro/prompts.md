## Sample Prompts

1)
```
I need to learn concurrent sequential processing in Go. Provide a list of scenarios I could use in preparation of implementing a task scheduler in Go.
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
Review and explain the following T-SQL stored procedure. 
- Suggest any enhancements that would improve performnce, security, and maintainability.  
- Provide a sample of the improved procedure.

CREATE PROCEDURE GetEmployeeDetailsByDepartment
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
I am a systems architect leading a team of systems engineers. Our environment includes both Go and C# applications and services. I need guidance on planning, designing, and implementing the following tasks:

1. Create a cloud environment using Azure.
2. Set up a web server and a load balancer.
3. Set up a database server.
4. Configure networking (e.g., VPC, subnets, security groups).
5. Implement security measures for the infrastructure.

```