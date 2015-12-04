Before each node in hdfs started, the node scheduler need to download jre first.  
The default path of download url is:  
https://downloads.mesosphere.io/java/jre-7u76-linux-x64.tar.gz  
To reduce the download time, I download it to local machine, and use nginx as download server  


###Start nginx
```sh
cd ~/docker_campus/hdfs
wget https://downloads.mesosphere.io/java/jre-7u76-linux-x64.tar.gz
docker-compose -f docker-compose-nginx.yml up
```
now use brower to visit http://192.168.2.36 to check whether the nginx is started  


###Compile hdfs  
download mesosphere/hdfs  
modify the mesos-site.xml  
then recompile it:  

```sh
$ cd ~
$ git clone https://github.com/mesosphere/hdfs.git
$ cd ~/hdfs
$ vi ~/hdfs/conf/mesos-site.xml
<property>
    <name>mesos.hdfs.jre-url</name>
    <description>The jre download by mesos container</description>
    <value>http://192.168.2.36/jre-7u76-linux-x64.tar.gz</value>
</property>
$ docker run -it --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3.3.3-jdk-7 ./bin/build-hdfs 
```

###Start hdfs
To exec the hdfs, we need an enviroment include jdk and mesos, so I build an image  

```sh
docker build -t mesos_jdk:0.24.1_1.7 .  
```
then we can boot hdfs by using this image 

```sh
docker run -it -v "$PWD"/hdfs-mesos-0.1.5:/hdfs-mesos-0.1.5 --net host --workdir /hdfs-mesos-0.1.5 mesos_jdk:0.24.1_1.7 bin/hdfs-mesos
```

