# docker-tips

# Linux
The Post-installation steps for Linux documentation reveals the following steps:

* Create the docker group.
```
sudo groupadd docker
```
* Add the user to the docker group.
```
sudo usermod -aG docker $(whoami)
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
