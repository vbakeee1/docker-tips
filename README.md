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
*The docker-machine start command outputs the comments to guide the process.
