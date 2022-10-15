# DPDK Monitoring

## Requirements
#### To run this experiment, it is necessary to use a Debian-based Linux operating system with freeRouter installing.



## Converting to Dataplane DPDK
```
write
test hwext path /rtr/rtr- dataplane p4dpdk
reload cold
(just press y)
```

## Configure sensors interfaces bytes
```
!
sensor ifaces-hw
    path interfaces-hw/interface/counter
    prefix freertr-ifaces
    prepend iface_hw_byte_
    command sho inter hwsumm
    name 0 ifc=
    key name interfaces-hw/interface
    replace \. _
    column 1 name st
    column 1 replace admin -1
    column 1 replace down 0
    column 1 replace up 1
    column 2 name tx
    column 3 name rx
    column 4 name dr
    exit
!
sensor ifaces-sw
    path interfaces-sw/interface/counter
    prefix freertr-ifaces
    prepend iface_sw_byte_
    command sho inter swsumm
    name 0 ifc=
    key name interfaces-sw/interface
    replace \. _
    column 1 name st
    column 1 replace admin -1
    column 1 replace down 0
    column 1 replace up 1
    column 2 name tx
    column 3 name rx
    column 4 name dr
    exit
!
```

## Configure server prometheus

```
server prometheus router
 sensor ifaces-hw
 sensor ifaces-sw
 vrf inet
 exit
!
```