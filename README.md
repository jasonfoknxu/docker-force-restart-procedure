# Docker Force Restart Procedure 

**(For Ubuntu/Debian based OS)**

This document provides a simple guide on how to force restart a Docker container that is frozen or not responding.

## Step 1: Confirm the Container Status

Before attempting to restart the container, please confirm that it is running and check its status using the following command:

```sh
sudo docker ps -a
```

Identify the container ID and the status of the container. If the status is already "exited" or "dead", you may not need to continue for the following steps. 

---

## Step 2: Try to Restart the Container

Try to restart the container using the following command:

```sh
sudo docker restart <Container ID>
```

**OR**

```sh
sudo docker stop <Container ID>
sudo docker start <Container ID>
```

If you are using `Docker Compose`, you can use the following command to restart the container:

```sh
sudo docker compose restart <Container ID>
```

**OR**

For `Docker Compose`, you can also `cd` to the root directory of your container project and try the following command:

```sh
sudo docker compose down
sudo docker compose up
```

---

## Step 3: Try to Kill the Container Process

If the restart command still does not respond, you can try to kill the process of the container by the following steps:

1. First, Identify the `Process ID (PID)` of the container

```sh
ps aux | grep <Container ID>
```

2. Then, use the following command to kill the process:

```sh
sudo kill -9 <Process ID>
```

---

## Step 4: Try to Restart the Docker Service

Finally, if the above steps do not work, you can try to restart the whole Docker service using the following command:

```sh
sudo systemctl restart docker.socket docker.service
```

⚠️ Please note that this will `Affect ALL Docker Containers` running on the system. ⛔

---

## Remark

By following the steps outlined in this document, you should be able to force restart a Docker container that is frozen or not responding on an Ubuntu/Debian based OS. Remember to always backup any important data before attempting to restart a container, as the restart process may cause data loss.

---