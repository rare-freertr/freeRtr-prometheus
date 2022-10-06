# FreeRouter-Prometheus

## Overview FreeRouter
#### freeRouter is a free, open source router os process. it speaks routing protocols, and (re)encapsulates packets on interfaces.


## Requirements
#### To run this experiment, it is necessary to use a Debian-based Linux operating system.

## Update's dashboards

All 26 of Grafana's freeRtr dashboard's have been updated and improved. One of the main differences is that we now have the router name.


## Sensor example universal:

- You can use this universal sensor (copy and paste).

```
sensor ifaces-sw
path interfaces-sw/interface/counter
prefix freertr-ifaces
key name interfaces-sw/interface
command sho inter swsumm
prepend iface_sw_byte_
name 0 ifc=
replace \. _
column 1 name st
column 1 replace admin -1
column 1 replace down 0
column 1 replace up 1
column 2 name tx
column 3 name rx
column 4 name dr
.
exit
```
## freeRtr agent prometheus configuration

```
server prometheus pr
 sensor ifaces-hw
 sensor ifaces-sw
 vrf <PROMETHEUS_VRF>
 exit
```

## Configure Prometheus Server file

```
global:
  scrape_interval: 15s
  scrape_timeout: 10s
  evaluation_interval: 30s
alerting:
  alertmanagers:
  - static_configs:
    - targets: []
    scheme: http
    timeout: 10s
scrape_configs:
- job_name: router
  scrape_interval: 15s
  scrape_timeout: 10s
  metrics_path: /metrics
  scheme: http
  static_configs:
  - targets:
    - <prometheus_agent_ip_1>:9001
    labels:
      node_name: <prometheus_agent_1_node_name>
  - targets:
    - <prometheus_agent_ip_2>:9001
    labels:
      node_name: <prometheus_agent_2_node_name>
```

## Configuration and Install FreeRouter

#### To work the FreeRtr just have java.
#### Consult the freerouter documentation for installing java:

- [FreeRouter](http://www.freertr.org/)

#### Install the latest and greatest Java Runtime Environment (JRE).
```
$ sudo apt-get install --no-install-recommends --no-install-suggests --yes default-jre-headless
```
#### Download the freeRouter jar binary.
```
$ wget http://www.freertr.org/rtr.jar
```


## Experiment Topology

<div style='display: inline-block'>
   <img align="center" alt="Topology" src='img-topology/topology.png' />
</div>
 

 
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

``` 
$ sudo apt install docker.io 
``` 
```
$ sudo apt install docker-compose 
```


## Prometheus Configuration
- [prometheus.yml](https://github.com/Tetzdesen/FreeRouter-Prometheus/blob/main/prometheus/prometheus.yml)
 
 
## Docker Compose file
- [docker-compose.yml](https://github.com/Tetzdesen/FreeRouter-Prometheus/blob/main/docker/docker-compose.yml)

## Start Deploy

```
$ git clone https://github.com/Tetzdesen/FreeRouter-Prometheus.git
$ cd FreeRouter-Prometheus
```

## Move directory prometheus for /etc
```
$ sudo mv prometheus /etc
```

- Check the IP from your interface
```
$ ifconfig
```

- Change the IP in the prometheus.yml file with your preferred text editor

```
$ sudo nano /etc/prometheus/prometheus.yml
```
## Start Docker Container's
```
$ cd docker
$ sudo docker-compose up -d
```
## Check Container's
```
$ sudo docker ps
```
## Run Configuration Router's
### Start Router's Configuration
- R1
```
$ java -jar <path>/rtr.jar routersc topology/r1/r1-hw.txt topology/r1/r1-sw.txt 
```
- R2
```
$ java -jar <path>/rtr.jar routersc topology/r2//r2-hw.txt topology/r2/r2-sw.txt 
```
## Grafana Configuration 
#### Access http://127.0.0.1:3000 
- User: admin 
- Password: freerouter

- Once installed configure Prometheus as Grafana data source.
<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-01" src='img-grafana/img-01.png' />
</div>

</br>

- Fill in all the prometheus server information.
<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-02" src='img-grafana/img-02.png' />
</div>

</br>

- Check the the data source is defined correctly by clicking the "Save & test" button.
<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-03" src='img-grafana/img-03.png' />
</div>

</br>

## Verification

### Verification Prometheus
- Access Prometheus - http://127.0.0.1:9090

- Access Targets

- Verify router's up

<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-04" src='img-grafana/img-05.png' />
</div>

</br>

### Verification Grafana

- Download freeRouter interface bytes dashboard [here.](https://grafana.com/grafana/dashboards/13153-rare-freerouter-interfaces-bytes/)
<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-05" src='img-grafana/img-06.png' />
</div>

</br>

- Access Grafana - http://127.0.0.1:3000


- Import Dashboard RARE/freeRouter 
<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-06" src='img-grafana/img-07.png' />
</div>

</br>

- Dashboard Verify

- R1
<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-07" src='img-grafana/img-001-grafana.png' />
</div>

</br>

- R2
<div style='display: inline-block'>
   <img align="center" alt="Img-Grafana-07" src='img-grafana/img-002-grafana.png' />
</div>

</br>

## Integration AlertManager

- [Integration AlertManager](https://github.com/rare-freertr/freeRtr-prometheus/tree/AlertManager/alertmanager)

## Integration Alerts Grafana
- [Integration Grafana Alerts](https://github.com/rare-freertr/freeRtr-prometheus/tree/main/alert-grafana-rules)


## Dataplane Monitoring
