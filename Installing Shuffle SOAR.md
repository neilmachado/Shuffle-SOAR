# Installing Shuffle SOAR 

Shuffle SOAR (Security Orchestration, Automation, and Response) is a powerful platform designed to streamline and automate various security operations processes. This guide will walk you through the installation process of Shuffle SOAR on your system.
Prerequisites
Before proceeding with the installation, ensure that the following prerequisites are met:

Docker and Docker Compose: Make sure you have Docker and Docker Compose installed on your system. Docker is a containerization platform that allows you to package and run applications in isolated environments, while Docker Compose is a tool for defining and running multi-container Docker applications.
System Resources: Shuffle SOAR requires a minimum of 2GB of RAM to run smoothly. Ensure that your system meets this requirement.

## Step 1: Verify Docker and Docker Compose Installation
Ensure that you have Docker and Docker Compose installed and properly configured on your system. If you haven't installed them yet, refer to the official documentation for installation instructions specific to your operating system:

- Install Docker Engine
- Install Docker Compose

## Step 2: Download Shuffle SOAR
To download the Shuffle SOAR repository, follow these steps:
```
git clone https://github.com/Shuffle/Shuffle
cd Shuffle
```
These commands will clone the Shuffle SOAR repository from GitHub and navigate into the project directory.

## Step 3: Fix Prerequisites for the Opensearch Database (Elasticsearch)
Shuffle SOAR utilizes Opensearch (formerly known as Elasticsearch) as its database solution. Before proceeding, you need to set up the necessary prerequisites for Opensearch:
```
mkdir shuffle-database                    # Create a database folder
sudo chown -R 1000:1000 shuffle-database  # IF you get an error using 'chown', add the user first with 'sudo useradd opensearch'

sudo swapoff -a                           # Disable swap
```
The first command creates a directory called shuffle-database where Opensearch will store its data.
The second command changes the ownership of the shuffle-database directory to the user with UID 1000 and the group with GID 1000. This step is necessary for Opensearch to function properly. If you encounter an error while running the chown command, you can create a new user called opensearch using sudo useradd opensearch and then change the ownership accordingly.
The third command disables swap on your system, which is a recommended configuration for Opensearch to work optimally.

## Step 4: Run Docker Compose
Once you've completed the previous steps, you can start the Shuffle SOAR application using Docker Compose:
```
docker-compose up -d
```
This command will start the Shuffle SOAR application and all its dependent services in the background (-d flag stands for "detached mode").
## Step 5: Recommended Configuration for Opensearch
To ensure that Opensearch works well with Shuffle SOAR, it's recommended to increase the maximum virtual memory map count on your system:

```
sudo sysctl -w vm.max_map_count=262144     
```
This command increases the maximum number of memory map areas a process can have, which improves Opensearch's performance.
After completing these steps, Shuffle SOAR should be up and running on your system, ready for you to start automating and orchestrating your security operations processes.
