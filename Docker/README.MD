# Setup Jenkins Server

## STEP 1: Create a Jenkins Network

`docker network create jenkins`

## STEP 2: Build a Jenkins Image

`docker build -t jenkins-slack-bot-v-2 .`

## STEP 3: Run the Jenkins Image

`docker run \
  --name jenkins-slack-bot-v-2 \
  --restart=on-failure \
  --detach \
  --network jenkins \
  --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client \
  --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 \
  --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  jenkins-slack-bot-v-2`
