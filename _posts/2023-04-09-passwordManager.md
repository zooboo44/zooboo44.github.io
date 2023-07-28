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
- ```7/15/2023``` Installed gRPC and successfully built the examples and was able to run them properly
- ```7/22/2023``` Start reading and understanding the gRPC documentation. The [Introduction to gRPC](https://grpc.io/docs/what-is-grpc/introduction/), [Core Concepts](https://grpc.io/docs/what-is-grpc/core-concepts/), and the language specific [Basics tutorial](https://grpc.io/docs/languages/cpp/basics/)
- ```7/23/2023``` Continued to read documentation on how to implement gRPC. Found a more practical example [here.](https://medium.com/@shradhasehgal/get-started-with-grpc-in-c-36f1f39367f4) Ran into some linking errors while building a test project. gRPC uses CMake as a build system so I'm learning more about it. Found [this test project](https://adaickalavan.github.io/portfolio/grpc_c++_with_cmake/#gsc.tab=0) which might help with the linking errors. Looking at the CMakeLists for the server and client programs, it seems he is including a preconfigured gRPC cmake file to handle the build of gRPC. Still need to look into it and fully understand what the CMakeLists is doing.
- ```7/24/2023``` Still having issues linking the gRPC library. I found a youtube video on ["Creating and Linking Static Libraries on Linux with gcc"](https://youtu.be/t5TfYRRHG04). It helped with understanding the linking process and how to link with g++ but I wasn't having any luck with it. I Asked chatGPT to make a CMakeLists.txt file to link gRPC and protobuf but was having issues. I think the best way to fix this issue is to learn more about linking external libraries and about CMake.
- ```7/25/2023``` Still having issues with CMake. Decided to put the project on hold till i learn how to use CMake properly instead of trying to hack together a janky CMakeLists file using chatGPT.
- ```7/26/2023``` Reinstalled Ubuntu on a VM to start from scratch in case my gRPC installation was messed up. 
- ```7/27/2023``` Reinstalled Ubuntu again and installed gRPC properly. Followed the [Get started with gRPC in C++](https://medium.com/@shradhasehgal/get-started-with-grpc-in-c-36f1f39367f4) by Medium.com and was able to build the program. Started making my own server, client, and proto files to understand fully how gRPC works. For now I'm just going to modify the CMakeLists.txt that was in the tutorial as I know for sure it builds. If I can successfully build my test programs I can start the actual project.

# Roadblocks
## Linking errors with gRPC
---
### Problem
- While following the guide [Get started with gRPC in C++](https://medium.com/@shradhasehgal/get-started-with-grpc-in-c-36f1f39367f4) I would get linking errors to the gRPC library. The source code would compile just fine but the linking to external libraries would halt CMake.

### Cause
- Corrupt installation of gRPC library

### Solution
- Reinstall gPRC library, ensure library is installed correctly by following guide previously mentioned to see if that builds properly

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
    - [Using Protocol Buffers in C++ (Youtube)](https://youtu.be/7wWjJ2eYixk)
    - [Getting Started with gRPC (github)](https://github.com/grpc/grpc/tree/master/src/cpp)
        - How to build from source
    - [Introduction to gRPC](https://grpc.io/docs/what-is-grpc/introduction/)
    - [C++ Basics tutorial](https://grpc.io/docs/languages/cpp/basics/)
    - [gRPC Basics (gRPC.io)](https://grpc.io/docs/languages/cpp/basics/)
- C++
    - [Creating and Linking Static Libraries on Linux with gcc](https://youtu.be/t5TfYRRHG04)



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
### Install test
    - ```export MY_INSTALL_DIR=$HOME/install_pkg```
    - ```mkdir -p $MY_INSTALL_DIR```
    - ```export PATH="$MY_INSTALL_DIR/bin:$PATH"```
    - ```sudo apt install -y cmake```
    - ```cmake --version```
    - ```sudo apt install -y build-essential autoconf libtool pkg-config```
    - ```cd install_pkg```
    - ```git clone --recurse-submodules -b v1.56.0 --depth 1 --shallow-submodules https://github.com/grpc/grpc```
    ```
    $ cd grpc
    $ mkdir -p cmake/build
    $ pushd cmake/build
    $ cmake -DgRPC_INSTALL=ON \
        -DgRPC_BUILD_TESTS=OFF \
        -DCMAKE_INSTALL_PREFIX=$MY_INSTALL_DIR \
        ../..
    $ make -j 4
    $ make install
    $ popd
    ```
    - Everythin ran smoothly up till here
    - ``````
    - ``````
    - ``````
    - ``````
    - ``````
    - ``````
    - ``````
    

- Compile ```.proto``` file
    ```
    protoc -I=proto --cpp_out=. --grpc_out=. --plugin=protoc-gen-grpc=`which grpc_cpp_plugin` <your_protobuf_file_name>.proto
    ```
    - ```-I=<path_to_protofile_directory>``` is the path to the ```.proto  ``` file
    - ```--cpp_out=``` is the output for the files that protoc makes for c++
    - ```--grpc_out=``` is the output for the gRPC c++ files that will be included in the .cpp program files
    - ```--plugin=protoc-gen-grpc=`which grpc_cpp_plugin\```` specifies the path to the gRPC plugin. The ```which grpc_cpp_plugin``` part finds the location of the grpc_cpp_plugin executable in your system and provides it as input to the --plugin option
    - ```<your_protobuf_file_name>.proto``` is the name of the ```.proto``` file you wish to compile