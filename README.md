# bWAPP Writeup

## Introduction

This README.md file is prepared for documenting a writeup on bWAPP (buggy web application). bWAPP is a deliberately insecure web application used for learning and teaching web application security. It's an excellent resource for understanding common web vulnerabilities and practicing techniques to exploit and mitigate them.

## Setup Instructions

To set up bWAPP, you'll need Docker installed on your machine. Follow these steps:

### 1. Running bWAPP in Docker

Run the following command to pull and start the bWAPP container:

```shell
docker run -d -p 80:80 raesene/bwapp
```

### 2. Get the IP Address of the Docker Container

Before running bWAPP, you need to know the IP address of the Docker container. Use this command to retrieve it:

```shell
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' [CONTAINER_ID]
```

### 3. Accessing bWAPP

After starting the Docker container, access bWAPP using the following URL, replacing [IP] with the IP address obtained from the previous step:

```web
http://[IP]/install.php
```