# Postfix Catch All Docker Container


Sets up a postfix email server that catches all emails received on port 25.
Latest image can be found @ [Docker Hub](https://hub.docker.com/r/frouk/postfix_catch_all/)

### How to Install
Build docker image
```
docker build --tag email_server_image .
```
Run docker image
```
docker run -td -p 25:25 --name email_server_container email_server_image
```

### Test
Telnet to container at port 25
```
telnet localhost 25
```
Then type
```
MAIL FROM:<test@example.com>
RCPT TO:test@example.com
DATA
SUBJECT: test

Test email content

.
```

### Read emails
Attach to running container
```
docker exec -it email_server_container /bin/bash
```
View contents of /var/mail/recipient
```
cat /var/mail/recipient
```