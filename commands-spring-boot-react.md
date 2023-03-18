# Build and Deploy Instructions

Follow the steps below to build and deploy the Spring Boot and React applications.

## Spring Boot

1. Clean the project:

mvn clean

2. Compile the project:

mvn compile

3. Package the project:

mvn package

4. Build the Docker image:

docker image build . -t my-spring-boot-demo-docker:windows11

5. Tag the Docker image:

docker image tag my-spring-boot-demo-docker:windows11 vlad0x/my-spring-boot-demo-docker:windows11

6. Push the Docker image:

docker image push vlad0x/my-spring-boot-demo-docker:windows11

# React

1. Build the project:

yarn build

2. Build the Docker image for production:

docker build . -t dockerized-react:windows11 -f Dockerfile-PROD

3. Tag the Docker image:

docker image tag dockerized-react:windows11 vlad0x/dockerized-react:windows11

4. Push the Docker image:

docker image push vlad0x/dockerized-react:windows11