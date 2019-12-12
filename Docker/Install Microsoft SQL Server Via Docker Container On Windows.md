# Install Microsoft SQL Server Express Via Docker Container On Windows
## Installation

Switch your Docker into Windows containers. Install Microsoft SQL Server Express via following command.

```
docker run -d --name <Name> --ip <Container NAT IP> -p 1433:1433 -e sa_password=<Password> -e ACCEPT_EULA=Y microsoft/mssql-server-windows-express
```
For example:
```
docker run -d --name mssql --ip 172.17.131.152 -p 1433:1433 -e sa_password=P@55w0rD -e ACCEPT_EULA=Y 
microsoft/mssql-server-windows-express
```

Please note that assign a **static IP address** to container, otherwise IP address of container will be dynamic and changed after you restart container.  

Make sure the **Password** follow the default policy, or you will not login server successfully by using password that you assign. At least 8 characters long and use three of following four sets:

- Uppercase letters
- Lowercase letters
- Base 10 digits
- Symbols

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
docker run -d --name <Name> --ip <Container NAT IP> -p 1433:1433 -e sa_password=<Password> -e ACCEPT_EULA=Y -v <Local Folder Path>:<Container Folder Path> microsoft/mssql-server-windows-express
```

For example:
```
docker run -d --name mssql --ip 172.17.131.152 -p 1433:1433 -e sa_password=P@55w0rD -e ACCEPT_EULA=Y 
-v C:/DockerVolume/mssql/backup/:C:/backup/ microsoft/mssql-server-windows-express
```

It will be able to access backup file when you restore database on SSMS.
