


## Level 2

### Task 1:

Nautilus project developers are planning to start testing on a new project. As per their meeting with the DevOps team, they want to test containerized environment application features. As per details shared with DevOps team, we need to accomplish the following task:

a. Pull busybox:musl image on App Server 2 in Stratos DC and re-tag (create new tag) this image as busybox:news.

Solution:

![answer1](image.png)

### Task 2:

One of the Nautilus project developers need access to run docker commands on App Server 2. This user is already created on the server. Accomplish this task as per details given below:

User jim is not able to run docker commands on App Server 2 in Stratos DC, make the required changes so that this user can run docker commands without sudo.

Solution: 

- SSH into App Server 2:

```sh
ssh user@AppServer2
```

- Add "jim" to the Docker group:

```sh
sudo usermod -aG docker jim
```

- Inform "jim" to log out and log back in or restart the Docker service:

```sh
exit
```
- Verify as "jim":

```sh
ssh jim@AppServer2
docker ps
```
### Task 3:

One of the Nautilus developer was working to test new changes on a container. He wants to keep a backup of his changes to the container. A new request has been raised for the DevOps team to create a new image from this container. Below are more details about it:

a. Create an image official:xfusion on Application Server 1 from a container ubuntu_latest that is running on same server.

Solution:

![image](https://github.com/user-attachments/assets/e0ccce97-e1b0-4ae6-a7a7-8d14bfa0bf4a)

### Task 4:

One of the Nautilus DevOps team members was working to configure services on a kkloud container that is running on App Server 1 in Stratos Datacenter. Due to some personal work he is on PTO for the rest of the week, but we need to finish his pending work ASAP. Please complete the remaining work as per details given below:


a. Install apache2 in kkloud container using apt that is running on App Server 1 in Stratos Datacenter.


b. Configure Apache to listen on port 8083 instead of default http port. Do not bind it to listen on specific IP or hostname only, i.e it should listen on localhost, 127.0.0.1, container ip, etc.


c. Make sure Apache service is up and running inside the container. Keep the container in running state at the end.

Solution:

![image](https://github.com/user-attachments/assets/45b1cbf2-5acc-4112-9e7c-08a4092c9393)
![image](https://github.com/user-attachments/assets/73a37158-7168-48ba-bdbe-b86d046ca4c4)
![image](https://github.com/user-attachments/assets/38447274-7e01-4de6-b8e9-deb4cf374dac)
![image](https://github.com/user-attachments/assets/03be773d-5667-49f7-ab27-91b966528c17)
![image](https://github.com/user-attachments/assets/4f3fdd84-80e9-4c85-aeee-c6675370fd0e)

### Task 5:

As per recent requirements shared by the Nautilus application development team, they need custom images created for one of their projects. Several of the initial testing requirements are already been shared with DevOps team. Therefore, create a docker file /opt/docker/Dockerfile (please keep D capital of Dockerfile) on App server 3 in Stratos DC and configure to build an image with the following requirements:



a. Use ubuntu as the base image.


b. Install apache2 and configure it to work on 3000 port. (do not update any other Apache configuration settings like document root etc).

Solution:

- SSH into Application Server 3:

```sh
ssh user@AppServer3
```

- Create the directory:

```sh
sudo mkdir -p /opt/docker
```

- Create and edit the Dockerfile:

```sh
sudo nano /opt/docker/Dockerfile
```

- Add the content:

```dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get install -y apache2
RUN sed -i 's/Listen 80/Listen 3000/' /etc/apache2/ports.conf
RUN sed -i 's/:80>/:3000>/' /etc/apache2/sites-enabled/000-default.conf
EXPOSE 3000
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```

- Save and close the file

- Build the Docker image:

```sh
cd /opt/docker
sudo docker build -t custom-ubuntu-apache:latest .
```

![image](https://github.com/user-attachments/assets/96b1e16a-fbe9-4814-a775-e47775c19c8f)

## Miscellaneous

