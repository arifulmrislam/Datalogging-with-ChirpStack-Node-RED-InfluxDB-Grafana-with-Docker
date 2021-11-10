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









