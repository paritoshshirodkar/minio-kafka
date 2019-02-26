# Steps to setup Apache Kafka to capture Minio bucket events


### Setup mc client


```
mkdir /home/mclient
docker export $(docker create shri4u/mc) | tar -C /home/mclient/ -xvf -
mv /home/mclient/mc /usr/local/bin/
```


### Setup Minio 
```
mkdir /mnt/config
mkdir /mnt/data
copy attached config file to /mnt/config
```
```git
git clone https://github.com/wurstmeister/kafka-docker.git
```




#### Install docker-compose (if you have not done it already)
```
apt install docker-compose
```
####  Update docker-compose.yml and change ADVERTISE_HOST to local machine IP


```
docker-compose up –d
```


### Setup Kafka 
```
 docker run -it shri4u/kafkacat bash
```


#### Test your Kafka setup


##### Setup Kafka Producer with topic test


###### The IP is your machine IP and port number can be checked using : docker ps –a (the port number is corresponding to your shri4u/kafkacat container)


```
kafkacat -P -b 10.0.2.15:32768 -t test
```


##### Setup Kafka Consumer with topic test
```
kafkacat -C -b 10.0.2.15:32768 -t test
```