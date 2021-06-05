# openshift-okd-v4-install

# Review: https://www.openshift.com/blog/openshift-4-bare-metal-install-quickstart

Installation going to be throwgh console and boot iso

# Hardware
##- 1 Workstation for installation (SO Unbutu)
CPU: 2 cores
Mem: 2Gb
Disk: 20gb
##- 1 Boostrap
CPU: 2 cores
Mem: 8Gb
Disk: 100gb
##- 3 Masters
CPU: 4 cores
Mem: 16Gb
Disk: 500Gb
##- 3 Workers
CPU: 8 cores
Mem: 32Gb
Disk: 500Gb

# Vips
##1- frontend openshift-api-server

    bind *:6443

    default_backend openshift-api-server

    mode tcp

    option tcplog
backend openshift-api-server
balance source
mode tcp
server bootstrap 192.168.1.96:6443 check
server master0 192.168.1.97:6443 check
server master1 192.168.1.98:6443 check
server master2 192.168.1.99:6443 check
##2- frontend machine-config-server
bind *:22623
default_backend machine-config-server
mode tcp
option tcplog


backend machine-config-server
balance source
mode tcp
server bootstrap 192.168.1.96:22623 check
server master0 192.168.1.97:22623 check
server master1 192.168.1.98:22623 check
server master2 192.168.1.99:22623 check 

