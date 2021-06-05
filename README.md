# openshift-okd-v4-install

# Review: https://www.openshift.com/blog/openshift-4-bare-metal-install-quickstart

Installation going to be throwgh console and boot iso

# Hardware
## 1 Workstation for installation (SO Unbutu)
CPU: 2 cores
Mem: 2Gb
Disk: 20gb
## 1 Boostrap
CPU: 2 cores
Mem: 8Gb
Disk: 100gb
## 3 Masters
CPU: 4 cores
Mem: 16Gb
Disk: 500Gb
## 3 Workers
CPU: 8 cores
Mem: 32Gb
Disk: 500Gb

# Vips
## 1 - frontend openshift-api-server

    bind *:6443

    default_backend openshift-api-server

    mode tcp

    option tcplog
backend openshift-api-server <p>
balance source <p>
mode tcp <p>
server bootstrap 192.168.1.6:6443 check <p>
server master0 192.168.1.1:6443 check <p>
server master1 192.168.1.2:6443 check <p>
server master2 192.168.1.3:6443 check <p>

## 2 - frontend machine-config-server

    bind *:22623

    default_backend machine-config-server

    mode tcp

    option tcplog
backend machine-config-server <p>
balance source <p>
mode tcp <p>
server bootstrap 192.168.1.6:22623 check <p>
server master0 192.168.1.1:22623 check <p>
server master1 192.168.1.2:22623 check <p>
server master2 192.168.1.3:22623 check <p>
## 3 - frontend ingress-http

    bind *:80

    default_backend ingress-http

    mode tcp

    option tcplog
backend ingress-http <p>
balance source <p>
mode tcp <p>
server worker0 192.168.1.4:80 check <p>
server worker1 192.168.1.5:80 check <p>
server worker2 192.168.1.6:80 check <p>
## 3 - frontend ingress-https

    bind *:443

    default_backend ingress-https

    mode tcp

    option tcplog
backend ingress-https <p>
balance source <p>
mode tcp <p>
server worker0 192.168.1.4:443 check <p>
server worker1 192.168.1.5:443 check <p>
server worker2 192.168.1.6:443 check <p>
    
# DNS
    
    
## VIEW INSTALLATION_STEPS.md
