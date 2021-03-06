# SQL Server Checker

SQL checker can be used to verify if the application can connect to SQL Server
using the specified connection sting and whether the application user has
the expected table permissions.

## Usage

```
// Creates a new Health Checker for application TestApp
HealthChecker healthChecker = new HealthChecker("TestApp");

// Creates a SQL Server dependency that will use connection string "MyDatabase"
SqlServerHealthDependency dbDependency = new SqlServerHealthDependency("MyDatabase");

// Adds two table dependencies to the database dependency
dbDependency.AddTableDependency("User", Permission.INSERT | Permission.SELECT | Permission.UPDATE);
dbDependency.AddTableDependency("Address", Permission.INSERT);

// Adds the database dependency to the health checker
healthChecker.AddDependency(dbDependency);

// Run the health checker
HealthData health = healthCheker.CheckHealth();
```
