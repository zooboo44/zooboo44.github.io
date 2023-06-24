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
./configure
```

# Progress/What I've learned
- Learned about sockets and how servers and clients connect to each other


# Roadblocks

# Resources
- Sockets
    - [Creating a TCP Server in C++ [Linux / Code Blocks]](https://youtu.be/cNdlrbZSkyQ)
    - [Unix Socket](https://www.tutorialspoint.com/unix_sockets/what_is_socket.htm)
    - [Sockets tutorial](https://www.linuxhowtos.org/C_C++/socket.htm)
    - [Group chat application](https://youtu.be/KEiur5aZnIM)

- PostgreSQL
    - [Install and configure Libpqxx](https://github.com/jtv/libpqxx/blob/master/BUILDING-configure.md)
- User Accounts
    - [General User Account structure](https://robertheaton.com/2019/08/12/programming-projects-for-advanced-beginners-user-logins/)
