# docker-study
Usefull commands to practice docker (at https://labs.play-with-docker.com) 



###### Checkout git (git is already installed on labs.play-with-docker.com)
```
git -version
git clone https://github.com/spring-guides/gs-spring-boot-docker.git
```
	
###### Install openjdk 8 (Below command(apk) is for Alpine linux as that is default at labs.play-with-docker.com)
```
apk --no-cache add openjdk8 --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community
java -version
```

###### Create docker file
```
vi Dockerfile
```

###### Containt of "Dockerfile" file 
```
FROM openjdk:8-jdk-alpine
VOLUME /tmp
COPY ./gs-spring-boot-docker/complete/target/gs-spring-boot-docker-0.1.0.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```


###### Build fat jar using maven
```
cd gs-spring-boot-docker/complete/
./mvnw clean install
```

###### Build docker image
```
pwd
cd /root
docker build -t sarangmane/test-repo .
```

###### Check image
```
docker images
```

###### Run docker container (output will be attached to console, foreground)
```
docker run -p 8080:8080 --name testapp sarangmane/test-repo
```

###### Delete docker container
```
docker container rm 696bf9bcf317
```

###### Run docker container in background (output will be not be attached to console)
```
docker run -d --rm -p 8080:8080 --name testapp sarangmane/test-repo
```


###### Push image created above to https://hub.docker.com/ (Account required on https://hub.docker.com/)
```
docker login -u=sarangmane
docker tag ca40807a252c sarangmane/test-repo:one-more-spring-boot-app
docker push sarangmane/test-repo:one-more-spring-boot-app
```




###### Run docker container from https://hub.docker.com/ (Account required on https://hub.docker.com/)
```
docker login -u=sarangmane
docker pull sarangmane/test-repo:one-more-spring-boot-app
docker run -d --rm -p 8080:8080 --name testapp sarangmane/test-repo:one-more-spring-boot-app
```
