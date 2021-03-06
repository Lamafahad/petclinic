# Petclinic
## [spring-petclinic-rest](https://github.com/spring-petclinic/spring-petclinic-rest) and [spring-petclinic-angular](https://github.com/spring-petclinic/spring-petclinic-angular) in dockerfiles

This uses the standard linux 'make' system. Requires docker and make, nothing else. You don't even need that really, because in the root of this repo is a Dockerfile that can build and run both of these for you without having make installed on the host system. As always, docker is all you really need to get anything done:

```
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock bryandollery/petclinic
```

That command pulls an image from hub.docker and runs it, sharing the docker-socket so that it can issue docker commands. The container then downloads this repo, pulls the other two petclinic images (client & server) from docker, and runs them together using docker-compose. If you do this instead:

```
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock bryandollery/petclinic cbuild
```

It'll not pull the containers from hub.docker, rather it will build these containers locally for you, then run the two container using docker-compose.

The [PetClinic](http://localhost:8081/petclinic/index.html) is served locally on port 8081

