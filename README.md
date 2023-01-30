# JDBC
Setting Up the JDBC

"https://learn.microsoft.com/en-us/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver16"

Download the JDBC File from the MSSQL site : "https://go.microsoft.com/fwlink/?linkid=2221563"

Step 1:
forName() is a method which dynamically load the driver's class file into memory, and automatically registers it.

Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");

Step 2:
Create a Database and insert data so we can try our JDBC connection.

Step 3:
Add to the modules of the project the .jar files that were downloaded from the microsoft link. Be sure to add them all to the module section even though you should only add the one corresponding to the java version you are using.

Step 4:
Connection String == Connection URL is where we set the database server and name so that the jdbc know on which database we are talking about.
We are using here Windows Authentication so we can use "integratedSecurity = true" which means no need for a user and a password to log into the database.
In Addition, encrypt = false to disable SSL connection but it is bad to use it in production mode. Good to know that we are in an educational environment.

String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=ApplicationDistribue;integratedSecurity=true;encrypt=false;";

Step 5:
If you are using MSSQL, consider adjusting some of the settings info with the Configuration app of Microsoft SQL server.
Enable TCP/IP properties and make sure that Listen All is enabled + in the IP Addresses tab, that IPAll to have the TCP Port set to 1433.
Consider also to add the "mssql-jdbc_auth-11.2.3.x64.dll" file in the bin of the jdk of Java in Program Files so that the JDK can recognises MSSQL.

Step 6:
Create a query and execute it in the program to display data from the database

ResultSet rs = st.executeQuery( "SELECT * FROM personnes" );

Step 7:
Don't forget to close the connection by using the .close() method.
