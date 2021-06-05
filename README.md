# openshift-okd-v4-install

# Review: https://www.openshift.com/blog/openshift-4-bare-metal-install-quickstart

# Notes
- Installation going to be throwgh console and boot iso
- Boostrap node is going to be reinstalled in a master node
- IPs are an example

# Hardware
## 1 Workstation for installation (SO Unbutu)
CPU: 2 cores
Mem: 2Gb
Disk: 20gb
## 1 Boostrap --> Master
CPU: 4 cores
Mem: 16Gb
Disk: 500gb
## 3 Masters
CPU: 4 cores
Mem: 16Gb
Disk: 500Gb
## 3 Workers
CPU: 8 cores
Mem: 32Gb
Disk: 500Gb

# Vips
## 1 - frontend openshift-api-server (192.168.1.30)

    bind *:6443

    default_backend openshift-api-server

    mode tcp

    option tcplog
backend openshift-api-server <p>
balance source <p>
mode tcp <p>
server bootstrap 192.168.1.4:6443 check <p>
server master0 192.168.1.1:6443 check <p>
server master1 192.168.1.2:6443 check <p>
server master2 192.168.1.3:6443 check <p>

## 2 - frontend machine-config-server (192.168.1.30)

    bind *:22623

    default_backend machine-config-server

    mode tcp

    option tcplog
backend machine-config-server <p>
balance source <p>
mode tcp <p>
server bootstrap 192.168.1.4:22623 check <p>
server master0 192.168.1.1:22623 check <p>
server master1 192.168.1.2:22623 check <p>
server master2 192.168.1.3:22623 check <p>
## 3 - frontend ingress-http (192.168.1.31)

    bind *:80

    default_backend ingress-http

    mode tcp

    option tcplog
backend ingress-http <p>
balance source <p>
mode tcp <p>
server worker0 192.168.1.5:80 check <p>
server worker1 192.168.1.6:80 check <p>
server worker2 192.168.1.7:80 check <p>
## 3 - frontend ingress-https (192.168.1.31)

    bind *:443

    default_backend ingress-https

    mode tcp

    option tcplog
backend ingress-https <p>
balance source <p>
mode tcp <p>
server worker0 192.168.1.5:443 check <p>
server worker1 192.168.1.6:443 check <p>
server worker2 192.168.1.7:443 check <p>

# DNS
server1.example.com.	3600	IN	  A	192.168.1.1
server2.example.com.	3600	IN	  A	192.168.1.2
server3.example.com.	3600	IN	  A	192.168.1.3
server4.example.com.	3600	IN	  A	192.168.1.4
server5.example.com.	3600	IN	  A	192.168.1.5
server6.example.com.	3600	IN	  A	192.168.1.6
server7.example.com.	3600	IN	  A	192.168.1.7

openshift-lab4.example.com.		3600	IN	A	192.168.1.30
api.cloud-lab4.example.com.		3600	IN	A	192.168.1.30
api-int.cloud-lab4.example.com.	3600	IN	A	192.168.1.30
*.apps.cloud-lab4.example.com.	3600	IN	A	192.168.1.31
bootstrap.cloud-lab4.example.com.	3600	IN	CNAME   server4.example.com.
master0.cloud-lab4.example.com.	3600	IN	CNAME   server1.example.com.
master1.cloud-lab4.example.com.	3600	IN	CNAME	server2.example.com.
master2.cloud-lab4.example.com.	3600	IN	CNAME   server3.example.com.
master3.cloud-lab4.example.com.	3600	IN	CNAME   server4.example.com.
worker0.cloud-lab4.example.com.	3600	IN	CNAME   server5.example.com.
worker1.cloud-lab4.example.com.	3600	IN	CNAME	server6.example.com. 
worker2.cloud-lab4.example.com.	3600	IN	CNAME	server7.example.com.
etcd-0.cloud-lab4.example.com.	3600	IN	CNAME   server1.example.com.
etcd-1.cloud-lab4.example.com.	3600	IN	CNAME	server2.example.com.
etcd-2.cloud-lab4.example.com.	3600	IN	CNAME   server3.example.com.
etcd-3.cloud-lab4.example.com.	3600	IN	CNAME   server4.example.com.
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-0.cloud-lab4.example.com.
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-1.cloud-lab4.example.com.
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-2.cloud-lab4.example.com.
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-3.cloud-lab4.example.com.  
    
## VIEW INSTALLATION_STEPS.md
