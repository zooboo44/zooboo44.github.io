---
title: C++ Password Manager
categories: Programming
---

# Background
- I want to create a server/clientpassword manager that is built in C++ and will use a SQL Database that will store encrypted secrets
- Features
    - Server/Client Architecture
    - Password Protected Access
    - Encrypted secrets
    - Portable
    - Docker Image
    - Organizations/Team sharing
    - Multithread to handle socket connections
    - SSL
    - logging (client IPs, actions, false attempts, etc.)
- Goal
    - Create a password manager from scratch in C++ to learn how to use sockets
    - Connect to a database
    - Utilize makefiles
    - Create a docker image
    - Encrypt/decrypt user input

# Timeline
- [ ] Create a client and server programs that can communicate with each other
- [ ] Parse json data to setup environment on start
- [ ] Multithread server connections
- [ ] Connect the server to a database
- [ ] Structure how the database is going to be setup to hold the usernames and passwords
- [ ] Be able to retrieve the usernames and passwords
- [ ] Encrypt passwords that are stored in the database

# MySQL
### MySQL Server Installation
- [Install MySQL Server with apt](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#apt-repo-fresh-install)
    ```
    sudo dpkg -i /PATH/version-specific-package-name.deb
    sudo apt-get install mysql-server
    ```
- Start Service
    ```
    $> systemctl [start | stop | status] mysql
    ```
### Postinstallation Setup and Testing
- Configure the sql server (change root password, remove test user, allow/disallow remote login by root user)
    ```
    mysql_secure_installation
    ```
- If this ```Failed! Error: SET PASSWORD has no significance for user 'root'@'localhost' ...``` error occurs when trying to set the root password [follow these steps](https://www.nixcraft.com/t/mysql-failed-error-set-password-has-no-significance-for-user-root-localhost-as-the-authentication-method-used-doesnt-store-authentication-data-in-the-mysql-server-please-consider-using-alter-user/4233)

# Progress/What I've learned
- Learned about sockets and how servers and clients connect to each other
- How to include and link external libraries


# Roadblocks

# Resources
- Sockets
    - [Creating a TCP Server in C++ [Linux / Code Blocks]](https://youtu.be/cNdlrbZSkyQ)
    - [Unix Socket](https://www.tutorialspoint.com/unix_sockets/what_is_socket.htm)
    - [Sockets tutorial](https://www.linuxhowtos.org/C_C++/socket.htm)
    - [Group chat application](https://youtu.be/KEiur5aZnIM)
- MySQL Database
    - [Connect to database](https://dev.mysql.com/doc/connector-cpp/1.1/en/connector-cpp-examples-complete-example-1.html)
    - [Connect to database video](https://youtu.be/cSZvq7Kv6_0)
- User Accounts
    - [General User Account structure](https://robertheaton.com/2019/08/12/programming-projects-for-advanced-beginners-user-logins/)
