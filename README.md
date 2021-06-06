# openshift-okd-v4-install

# Review: https://www.openshift.com/blog/openshift-4-bare-metal-install-quickstart

# Notes
- Installation going to be throwgh console and boot iso
- Boostrap node is going to be reinstalled in a master node
- All the servers and workstation with access direct to the internet 
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
option httpchk GET /healthz <p>
http-check expect string ok <p>
server master0 192.168.1.1:6443 check <p>
server master1 192.168.1.2:6443 check <p>
server master2 192.168.1.3:6443 check <p>
server master3 192.168.1.4:6443 check <p>

## 2 - frontend machine-config-server (192.168.1.30)

    bind *:22623

    default_backend machine-config-server

    mode tcp

    option tcplog
backend machine-config-server <p>
balance source <p>
mode tcp <p>
option httpchk GET /healthz <p>
http-check expect string ok <p>   
server master0 192.168.1.1:22623 check <p>
server master1 192.168.1.2:22623 check <p>
server master2 192.168.1.3:22623 check <p>
server master3 192.168.1.4:22623 check <p>
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

Healthcheck:  http://<server>:1936/healthz <p>
String: ok  <p>

## 4 - frontend ingress-https (192.168.1.31)

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

Healthcheck: http://<server>:1936/healthz <p>
String: ok <p>
    
# DNS
server1.example.com.	3600	IN	  A	192.168.1.1 <p> 
server2.example.com.	3600	IN	  A	192.168.1.2 <p> 
server3.example.com.	3600	IN	  A	192.168.1.3 <p> 
server4.example.com.	3600	IN	  A	192.168.1.4 <p> 
server5.example.com.	3600	IN	  A	192.168.1.5 <p> 
server6.example.com.	3600	IN	  A	192.168.1.6 <p> 
server7.example.com.	3600	IN	  A	192.168.1.7 <p>
workstation.example.com.	3600	IN	  A	192.168.1.11 <p> 
 <p> 
openshift-lab4.example.com.		3600	IN	A	192.168.1.30 <p> 
api.cloud-lab4.example.com.		3600	IN	A	192.168.1.30 <p> 
api-int.cloud-lab4.example.com.	3600	IN	A	192.168.1.30 <p> 
*.apps.cloud-lab4.example.com.	3600	IN	A	192.168.1.31 <p> 
bootstrap.cloud-lab4.example.com.	3600	IN	CNAME   server1.example.com. <p> 
master0.cloud-lab4.example.com.	3600	IN	CNAME   server1.example.com. <p> 
master1.cloud-lab4.example.com.	3600	IN	CNAME	server2.example.com. <p> 
master2.cloud-lab4.example.com.	3600	IN	CNAME   server3.example.com. <p> 
master3.cloud-lab4.example.com.	3600	IN	CNAME   server4.example.com. <p> 
worker0.cloud-lab4.example.com.	3600	IN	CNAME   server5.example.com. <p> 
worker1.cloud-lab4.example.com.	3600	IN	CNAME	server6.example.com.  <p> 
worker2.cloud-lab4.example.com.	3600	IN	CNAME	server7.example.com. <p> 
etcd-0.cloud-lab4.example.com.	3600	IN	CNAME   server1.example.com. <p> 
etcd-1.cloud-lab4.example.com.	3600	IN	CNAME	server2.example.com. <p> 
etcd-2.cloud-lab4.example.com.	3600	IN	CNAME   server3.example.com. <p> 
etcd-3.cloud-lab4.example.com.	3600	IN	CNAME   server4.example.com. <p> 
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-0.cloud-lab4.example.com. <p> 
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-1.cloud-lab4.example.com. <p> 
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-2.cloud-lab4.example.com. <p> 
_etcd-server-ssl._tcp.cloud-lab4.example.com. 3600 IN SRV 0 10 2380 etcd-3.cloud-lab4.example.com.  
    
## INSTALL
1_WORKSTATION_STEPS.md <p>
2_BOOTSTRAP_STEPS.md <p>
3_SERVERS_STEPS.md <p>
4_WORKSTATION_STEPS.md <p>    
5_TRANSFORM_BOOTSTRAP_MASTER.md <p>
6_WORKSTATION_FINAL_STEPS.md <p>    
