# Install Microsoft SQL Server Express Via Docker Container On Windows
## Installation

Install Microsoft SQL Server Express by below command. 

```
docker run -d --name <Name> -p 1433:1433 -e sa_password=<Password> -e ACCEPT_EULA=Y microsoft/mssql-server-windows-express
```

Make sure the **Password** follow the default policy, or you will not login server successfully by password that you assign. At least 8 characters long and use three of following four set:

* Uppercase letters
* Lowercase letters
* Base 10 digits
* Symbols
