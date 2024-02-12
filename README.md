# Jenkins in Docker

To run this template execute :

1. Create jenkins network

```bash
docker network create jenkins
```

2. Build the official image

```bash
docker build -t jenkins-oceanblue-2.426.3 .
```

3. Start the docker container using the docker compose file

```bash
docker compose up -d
```

## Configuring Docker

1. Install Docker Plugin
2. Visit Dashboard > Manage Jenkins > Configure Clouds
3. Add New Cloud > Docker
4. Set Docker Host URI `tcp://docker:2376`
5. Click on the “Add” drop down and create an “X.509 Client Certificate”.
6. Obtain Client Key, Client Certificate, Server CA Certificate using the below command

```bash
docker exec jenkins-docker cat /certs/client/key.pem
docker exec jenkins-docker cat /certs/client/cert.pem
docker exec jenkins-docker cat /certs/server/ca.pem
```

7. Configuring Docker Slaves/Agents
8. Set Docker Agent templates Labels as `jenkins-agent`
9. Set name as `jenkins-agent`
10. Set Docker Image as `jenkins/agent:latest-jdk11`
11. Set Remote File System Root as `/home/jenkins/agent`
12. Click Save and Complete
