# Spring Boot

mvn clean
mvn compile
mvn package
docker image build . -t my-spring-boot-demo-docker:windows11
docker image tag my-spring-boot-demo-docker:windows11 vlad0x/my-spring-boot-demo-docker:windows11
docker image push vlad0x/my-spring-boot-demo-docker:windows11

# React

yarn build

docker build . -t dockerized-react:windows11 -f Dockerfile-PROD

docker image tag dockerized-react:windows11 vlad0x/dockerized-react:windows11
docker image push vlad0x/dockerized-react:windows11