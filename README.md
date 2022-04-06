# DockerForAOSPBuild

```
# Copy your host gitconfig, or create a stripped down version
$ cp ~/.gitconfig gitconfig
$ docker build --build-arg userid=$(id -u) --build-arg groupid=$(id -g) --build-arg username=$(id -un) -t android-build-trusty .
```

Then you can create a container with:
```
$ docker run --name android-build -v <host computer repos path>:/home/$(id -un)/repos android-build-trusty &
```

This docker file creates a user in the image with the same details of user of host computer when built.

Set password for the created user using following command in the root shell.  To get root shell of the docker container
```
docker exec -it android-build bash
```

You can get the user shell of running container with the following to start your build
```
$ docker exec -it -u 1001:1001 android-build bash
```