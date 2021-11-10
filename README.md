# Dell-Edge-Computer-Docker-InfluxDB-Grafana-Node-Red-and-ChirpStack
Dell Edge Computer, Docker, InfluxDB, Grafana, Node-Red and ChirpStack

Hi all, there is a very quick guide how to configure a system monitoring for one or more servers using a modern stack of technologies, 
like Node-Red, Grafana, Docker and Telegraf with Influxdb.

<img src= "IMG/Node-Red, Grafana, Docker and Telegraf with Influxdb.png" width=800>

The main goal for this article is to show how to start getting system metrics from your servers quick and easy, 
without spending lot of time for configuring big and complicated monitoring systems. 
Especially if you only need to take care for few Web servers instead of monitoring big company infrastructure with hundreds of devices.

We’ll use Docker, for the quick deployment our monitoring system, also it’ll gives us a freedom to use any software with dependency free and keep our system clean after. 
Topical, you can look at Docker from this side too, as a cross-platform package system.

Also, we’ll use part of Tick stack, namely an Influxdb base to store our metrics and Telegraf, like an agent on remote system, for nice and pretty graphs we’ll take Grafana.

Legend:

Dell Edge Computer,

	By default, it was installed Ubuntu 18.04 LTS. Then I update the latest version ubuntu 20.04.3 LTS.

	sequence from 18.04 to 20.04
  $ sudo apt update
  $ sudo apt upgrade
  $ sudo apt dist-upgrade
  $ sudo apt autoremove
  $ sudo do-release-upgrade -d -f DistUpgradeViewGtk3

	After that I got some error. For this reason, when I try to install or update, it showed below error. 

Error:  

Ubuntu – dpkg: error processing archive /var/cache/apt/archives/cuda-cublas-9-1_9.1.85.3-1_amd64.deb (–unpack)

<img src= "IMG/error.png" width=800>

Solve: 

The "trying to overwrite" error implies that i have conflicting packages in my system. I try overwriting the package (can be a bit risky).

  $sudo dpkg -i --force-overwrite /var/cache/apt/archives/cuda-cublas-9-1_9.1.85.3-1_amd64.deb 

If that doesn't fix it, you can remove the package and re-install it.

  $sudo dpkg -P cuda-cublas
  
Install Docker on Dell server,

At first, we should install docker engine on ubuntu 20.04 LTS. Let’s do it by this command.

  $ sudo apt install docker.io
  $ docker –version
	$ sudo systemctl enable –now docker
	$ sudo systemctl status docker
  
It will show,

<img src= "IMG/Docker on Dell server.png" width=800>

For final check we can run,
	$ sudo docker run hello world
	$ sudo docker ls -a
Manage docker as a non-root user,
	$ sudo groupadd docker
	$ sudo usermod -aG docker $USER (User mean your system username)
	$ newgrp docker
 Verify that you can run docker commands without sudo. 

Finally, install docker composer when we will run docker.yml file. That time we should use docker composer. 

  $ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  
Apply executable permission to the binary:

  $ sudo chmod +x /usr/local/bin/docker-compose
  $ docker-compose --version

Now we will install Influxdb and Grafana both with docker-compose.yml.
At first, we need to create folder for our project, for example /opt/monitoring,

  $ mkdir /opt/monitoring && cd /opt/monitoring
  
Inside directory we need to create docker-compose.yml file with Grafana and Influxdv services:

<img src= "IMG/Yml file.png" width=800>

  $ vi docker-compose.yml
  
<img src= "IMG/compose.yml.png" width=800>

Now we need to create this docker network and volumes:
  $ docker network create monitoring
  $ docker volume create grafana-volume
  $ docker volume create influxdb-volume

Make sure that all created fine,

<img src= "IMG/Make sure that all created fine.png" width=800>








