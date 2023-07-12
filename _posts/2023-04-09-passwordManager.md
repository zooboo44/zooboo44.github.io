---
title: C++ Password Manager
categories: Programming
---

# Background
- I want to create a server/clientpassword manager that is built in C++ and will use a SQL Database that will store encrypted secrets
- Goal
    - Create a password manager from scratch in C++ to learn how to use sockets
    - Connect to a database
    - Utilize makefiles
    - Create a docker image
    - Encrypt/decrypt user input
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

# Timeline/What I've learned
- [X] ```6/16/2023``` Create a client and server programs that can communicate with each other
    - Manually created a server and client program that communicated through sockets
- [X] ```6/30/2023``` Connected a test server program to a Postgres database
    - Still need to learn how to properly parse data from the database, insert, remove, modify, etc. So far I just have a solid connection to the database in which I can perform queries
- ```7/7/2023``` After thinking about how the client is going to envoke different functions on the server side, I started looking into creating an API for the server. So far I have kind of settled on gRPC that enhances the functionality of ProtoBuf (from my understanding) I still need to do a lot more digging but I'm going to explore this path and see if it's a right fit for this project

# Roadblocks

# Resources
- Sockets
    - [Creating a TCP Server in C++ [Linux / Code Blocks]](https://youtu.be/cNdlrbZSkyQ)
    - [Unix Socket](https://www.tutorialspoint.com/unix_sockets/what_is_socket.htm)
    - [Sockets tutorial](https://www.linuxhowtos.org/C_C++/socket.htm)
    - [Group chat application](https://youtu.be/KEiur5aZnIM)

- PostgreSQL
    - [Install and configure Libpqxx](https://github.com/jtv/libpqxx/blob/master/BUILDING-configure.md)
    - [Configure PostgreSQL to allow remote connection](https://www.bigbinary.com/blog/configure-postgresql-to-allow-remote-connection)
- User Accounts
    - [General User Account structure](https://robertheaton.com/2019/08/12/programming-projects-for-advanced-beginners-user-logins/)
- gRPC
    - [Protocol Buffers Crash Course (Youtube)](https://youtu.be/46O73On0gyI)
    - [Using Protocol Buffers in C++](https://youtu.be/7wWjJ2eYixk)
    - [Getting Started with gRPC (github)] (https://github.com/grpc/grpc/tree/master/src/cpp)
        - How to build from source
    - [gRPC Basics (gRPC.io)](https://grpc.io/docs/languages/cpp/basics/)



# PUT IN REPOSITORY README
# PostgreSQL
## Server Installation
```
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'\
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -\
sudo apt update\
sudo apt-get install postgresql
```

## PgAdmin Web Installation
```
sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'\
sudo apt install pgadmin4-web\
#Create initial PgAdmin account
sudo /usr/pgadmin4/bin/setup-web.sh\
```
- Log into PgAdmin ```127.0.0.1\pgadmin4```
- Open PgAdmin in your browser, create an account, and login.
- Then right-click 'Servers' (top left of GUI, under 'Browser').
    - Under 'General', give your server a name (I used postgresql-local).
    - Under 'Connection', supply a host (127.0.0.1), port (5432), and username (postgres)


## Configure PostgreSQL to allow remote connection
- Allow other IPs to connect to SQL Server
```
vim /etc/postgresql/15/main/postgresql.conf
```
- Replace ```listen_addresses = 'localhost'``` with ```listen_addresses = '*'```
- Open ```pg_hba.conf``` and add the following entry
```
host    all             all              0.0.0.0/0                       md5
host    all             all              ::/0                            md5
```
- Restart postgresql server ```sudo systemctl restart postgresql.service```



## Connector
- Download ```libpq``` library

```
Arch
yay -S postgresql-libs

Ubuntu
sudo apt install libpq-dev
```
- Download ```libpqxx``` library
```
wget https://github.com/jtv/libpqxx/archive/refs/tags/7.7.5.tar.gz
```
- Extract
```
tar xvfz libpqxx-4.0.tar.gz
```
- Configure
```
cd libpqxx-4.0
./configure --enable-static
```
- Make
```
make && make install
```

# gRPC
###