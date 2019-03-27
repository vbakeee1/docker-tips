# docker-tips

# Linux

* Configure locale in ubuntu
```
curl -sL https://raw.githubusercontent.com/prabhatpankaj/ubuntustarter/master/initial.sh | sh
```

* Install Docker
```
sudo su

cd

curl -sSL https://get.docker.com/ | sh
```

* Create the docker group.
```
sudo groupadd docker
```
* Add the user to the docker group.
```
sudo usermod -aG docker $(whoami)
newgrp docker

```
*Log out and log back in to ensure docker runs with correct permissions.
Start docker.
```
sudo service docker start
```
#Mac OS X
```
docker-machine start # Start virtual machine for docker
docker-machine env  # It's helps to get environment variables
eval "$(docker-machine env default)" # Set environment variables
```
* The docker-machine start command outputs the comments to guide the process.
* Editing your hosts file causes that your local machine only looks directly to the IP address specified for a domain. So, you could add the ip address of the docker-machine to the etc\hosts file in your local machine and map the port 80 on your container to the port 80 on the docker-machine.

Example:

* Get docker host ip address
```
docker-machine ip default
192.168.99.100
```
* Add this line to etc/hosts file in your local machine
```
192.168.99.100 domain.com
```
* Check that your machine is resolving the domain.

```
ping domain.com

PING domain.com (192.168.99.100): 56 data bytes
64 bytes from 192.168.99.100: icmp_seq=0 ttl=64 time=0.294 ms
64 bytes from 192.168.99.100: icmp_seq=1 ttl=64 time=0.437 ms
64 bytes from 192.168.99.100: icmp_seq=2 ttl=64 time=0.556 ms
64 bytes from 192.168.99.100: icmp_seq=3 ttl=64 time=0.270 ms

```
* configure Docker in jenkins

Jenkins Docker Plugin Configuration when running jenkins as container

1) First Install Docker Plugin

2) Go to Manage Jenkins -> System Configuration -> Scroll down to botton -> Add Cloud -> Docker

3) If you are running jenkins as container, in the docker host uri field you have to enter unix or tcp address of the docker host. But since you are running jenkins as container, the container cant reach docker host unix port

4) So we have to run another container that can mediate between docker host and jenkins container. It will publich docker host's unix port as its tcp port. Follow the instructions to create socat container https://hub.docker.com/r/alpine/socat/

5)After the creating socat container, you can go back the docker configuration in jenkins and enter tcp://socat-container-ip:2375

6) Test Connection should succeed now


* Docker containers are designed to be ephemeral. To update an existing container, you remove the old one and start a new one. Thus the process that you are following is the correct one.

You can simplify the commands to the following ones:

```
docker-compose up --force-recreate --build
docker image prune -f
```
