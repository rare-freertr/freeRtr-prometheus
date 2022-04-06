# FreeRouter-Prometheus

## About FreeRouter

freeRouter is a free, open source router os process.
it speaks routing protocols, and (re)encapsulates packets on interfaces.

</br>

## Configuration and Install FreeRouter

#### To work the FreeRtr just have java.
#### Consult the freerouter documentation for installing java:

- [FreeRouter](http://www.freertr.net/)

</br>

## FreeRouter topology
</br>
<div style='display: inline-block'>
   <img align="center" alt="Python" src='img-topology/topology.png' />
</div>
 
</br>
 
## Topology Configuration
- [R1](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/topology/r1)
- [R2](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/topology/r2)
 
## Dependencies and technologies
![Badge](https://img.shields.io/static/v1?label=DOCKER&message=DOCKER&color=blue&style=for-the-badge&logo=DOCKER)
![Badge](https://img.shields.io/static/v1?label=Prometheus&message=Prometheus&color=blue&style=for-the-badge&logo=PROMETHEUS)
![Badge](https://img.shields.io/static/v1?label=GRAFANA&message=Grafana&color=blue&style=for-the-badge&logo=GRAFANA)
- [Docker](https://www.docker.com/)
- [Docker-Compose](https://docs.docker.com/compose/)
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/grafana/)
## Install Docker and docker-compose
</br>

``` 
sudo apt install docker.io 
``` 
```
sudo apt install docker-compose 
```
</br>

## Prometheus Configuration
- [prometheus.yml](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/prometheus)
 
 
## Docker Compose file
- [docker-compose.yml](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/prometheus)
 
## Start Docker Container's
```
cd docker
sudo docker-compose up -d
```
## Check Container's
```
sudo docker ps
```
## Run Configuration 
### Start Router's Configuration
- R1
```
   java -jar <path>/rtr.jar routersc topology/r1/r1-hw.txt topology/r1/r1-sw.txt 
```
- R2
```
   java -jar <path>/rtr.jar routersc topology/r2//r2-hw.txt topology/r2/r2-sw.txt 
```
## Grafana Configuration 
### Access http://127.0.0.1:3000 
- User: admin 
- Password: freerouter

### Once installed configure Prometheus as Grafana data source:

## Grafana Configuration Dashboard's
### Import Dashboard 
## Tests Ping