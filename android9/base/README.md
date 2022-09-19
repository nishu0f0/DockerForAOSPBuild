# DockerForAOSPBuild

Note: This repo is useful in building AOSP repos from android 5.1 to android 8. If you need to build AOSP for android 5.1 please modify the Docker file by commenting java 8 lines and uncommenting java 7 lines. 

## Setup Docker


 Install docker from the link https://docs.docker.com/engine/install/ubuntu/

 Instead you can also install from following commands
 
 ```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin


 ```


 
 Run following command to add current user to docker group. 

```
sudo usermod -a -G docker $(id -un)   
```

Reboot computer for above command to take effect.

The above command removes the necessity for sudo when running docker command.





## Setup image:

Clone this repo and enter the repo in the terminal 
Copy your host gitconfig, or create a stripped down version
```
cp ~/.gitconfig gitconfig
```

Build docker image
```
docker build -t android9-build-env-base .
```


