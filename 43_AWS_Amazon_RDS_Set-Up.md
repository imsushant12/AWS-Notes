## Relational Databases Supported by Amazon RDS

Amazon RDS currently supports a variety of popular relational database engines, allowing you to choose the one that best suits your application's needs. Here are some of the options:

* **Popular Open-Source Engines:**
    * MySQL
    * MariaDB
    * PostgreSQL
* **Commercial Database Engines:**
    * Oracle Database
    * Microsoft SQL Server
* **Amazon-Developed Engine:**
    * Amazon Aurora (offers MySQL and PostgreSQL compatibility)

### Creating an RDS Instance
Here's a simplified overview of creating an RDS instance using the AWS Management Console:

1. **Log in** to the AWS Management Console.
2. Go to the **Amazon RDS service**.
3. Click on **"Create database"**.
4. Choose an **Engine** (e.g., MySQL, PostgreSQL).
5. Select a **template** (free tier eligible or production).
6. Configure the **Settings** for your database instance (e.g., Instance Class, Storage, Credentials).
7. **Configure** any additional options like connectivity, security groups, and backups.
8. **Review** your selections and click **"Create database"** to launch your RDS instance.

**Note:** This is a general outline. The specific steps and options might vary depending on the chosen engine and your configuration needs. Please read the official Amazon RDS documentation for more details.

[Click Here for more details](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateDBInstance.html)

### Connecting to Your RDS Instance
Once your RDS instance is up and running, you can connect to it using a database client application that supports your chosen engine (e.g., MySQL Workbench for MySQL). Here's some general information for connecting:

1. **Gather connection details:**
    * **Endpoint:** The hostname or address of your RDS instance.
    * **Port:** The port number used for your database engine (typically 3306 for MySQL).
    * **Username and Password:** The credentials you created during the RDS instance setup.
2. **Configure your client application:**
    * Provide the endpoint address, port, username, and password.
    * Specify the database name you want to connect to within your RDS instance.
3. **Connect!**  Your client application should establish a connection to your RDS database.

**Remember:** Security best practices are crucial.  For enhanced security, consider using secure connection methods and managing user access to your RDS instance. Refer to the AWS documentation for more details on security.

[Click Here for more details](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_BestPractices.Security.html)

## Summary
![image](https://imgur.com/S5JTRGc.png)
