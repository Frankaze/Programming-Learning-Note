# Install Microsoft SQL Server Express Via Docker Container On Windows
## Installation

Switch your Docker into Windows containers. Install Microsoft SQL Server Express via following command. 

```
docker run -d --name <Name> -p 1433:1433 -e sa_password=<Password> -e ACCEPT_EULA=Y microsoft/mssql-server-windows-express
```

Make sure the **Password** follow the default policy, or you will not login server successfully by using password that you assign. At least 8 characters long and use three of following four sets:

* Uppercase letters
* Lowercase letters
* Base 10 digits
* Symbols

## Find Out IP Address Of Server
Use the below command to find out the IP address of server in Docker container.
```
docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <Name>
```

## Restore Database By SQL Server Management Studio
Using Docker volume to move database backup file into container. 
```
docekr run -it <Name> -v <Local Folder Path>:<Container Folder Path>
```
Or add volume mapping when installing SQL Server via following command. 
```
docker run -d --name <Name> -p 1433:1433 -e sa_password=<Password> -e ACCEPT_EULA=Y -v <Local Folder Path>:<Container Folder Path> microsoft/mssql-server-windows-express
```
It will be able to access backup file when you restore database on SSMS.
