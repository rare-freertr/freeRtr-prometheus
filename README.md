# FreeRouter-Prometheus
Documentation prometheus integration with FreeRouter:
- [FreeRouter](http://www.freertr.net/)
 
</br>
 
## Configuration and Install FreeRouter
To work the FreeRtr just have java
 
 
Linux </br> </br>
apt-get install default-jre-headless --no-install-recommends
</br>
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
- [R3](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/topology/r3)
- [R4](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/topology/r4)
 
## Dependencies and technologies
![Badge](https://img.shields.io/static/v1?label=DOCKER&message=DOCKER&color=blue&style=for-the-badge&logo=DOCKER)
![Badge](https://img.shields.io/static/v1?label=Prometheus&message=Prometheus&color=blue&style=for-the-badge&logo=PROMETHEUS)
![Badge](https://img.shields.io/static/v1?label=GRAFANA&message=Grafana&color=blue&style=for-the-badge&logo=GRAFANA)
- [Docker](https://react-pdf.org/)
- [Docker-Compose](https://docs.docker.com/compose/)
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/grafana/)
## Install Docker and docker-compose
<code> sudo apt install docker.io </code>  </br>
<code> sudo apt install docker-compose </code>
 
## Prometheus Configuration
- [prometheus.yml](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/prometheus)
 
 
## Docker Compose file
- [docker-compose.yml](https://github.com/Tetzdesen/FreeRouter-Prometheus/tree/main/prometheus)
 
## Run configuration
### Start Router's Configuration
<code>  </code>
<code> java -jar <path>/rtr.jar routersc <path>/r1-hw.txt <path>/r1-sw.txt  </code>   

<code>  </code>
<code> java -jar <path>/rtr.jar routersc <path>/r1-hw.txt <path>/r1-sw.txt  </code>   


<code>  </code>
<code> java -jar <path>/rtr.jar routersc <path>/r1-hw.txt <path>/r1-sw.txt  </code>     

<code>  </code>
<code> java -jar <path>/rtr.jar routersc <path>/r1-hw.txt <path>/r1-sw.txt  </code>  

