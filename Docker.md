


## Level 2

### Question 1:

Nautilus project developers are planning to start testing on a new project. As per their meeting with the DevOps team, they want to test containerized environment application features. As per details shared with DevOps team, we need to accomplish the following task:

a. Pull busybox:musl image on App Server 2 in Stratos DC and re-tag (create new tag) this image as busybox:news.

![answer1](image.png)

### Question 2:

One of the Nautilus project developers need access to run docker commands on App Server 2. This user is already created on the server. Accomplish this task as per details given below:

User jim is not able to run docker commands on App Server 2 in Stratos DC, make the required changes so that this user can run docker commands without sudo.

Answer: 

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

## Miscellaneous

