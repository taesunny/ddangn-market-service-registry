

# Ddangn Market - Service Registry

<img src="https://miro.medium.com/max/700/1*InTRJNvyco3ZAjYdiKYmzw.jpeg" width="150">

- This app is for study Spring Boot and MSA.
- This app is Service Registry using Netflix Eureka.
- Visit ddangn.taesunny.com

## How to register API server to this Service Registry
You can configure other API server to register them into this service registry.
Update API server's application.xml like below.
Set same port of defaultZone url with Service Registry's port.
##### Example
```
eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/
  instance:
    instanceId: ${spring.application.name}:${vcap.application.instance_id:${spring.application.instance_id:${random.value}}}
```

## How to build docker image
You can `image name`, by setting application.yml's app name variable
You can set `tag`, by setting application.yml's app version variable
##### Run command below
```
./gradlew clean jar dockerBuildImage
docker images # check the created image
```

## How to run docker with the created image

##### Run command below
```
docker run -d -p 8761:8761 -it {package path:docker image name}:{set tag used when docker image build}  
docker ps # check the running docker container
```

## Contacts

Taesun Lee - superbsun@gmail.com
