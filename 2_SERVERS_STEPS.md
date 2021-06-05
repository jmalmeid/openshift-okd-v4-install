# SERVERS STEPS
Console of the servers
Boot ISO: https://builds.coreos.fedoraproject.org/prod/streams/stable/builds/32.20201104.3.0/x86_64/fedora-coreos-32.20201104.3.0-live.x86_64.iso
Review the version: https://getfedora.org/en/coreos/download?tab=metal_virtualized&stream=stable

# Config Boot
When is booting Press TAB <p>
Choose the correct server <p>
Change #CHANGE_DNS# with the correct <p>
If you have 2 nics you have repeat the ip <p>  

ip=192.168.1.1::192.168.1.254:255.255.255.0:server1.example.com:ens192:none  nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/bootstrap.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz

ip=192.168.1.2::192.168.1.254:255.255.255.0:server2.example.com:ens192:none  nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/master.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz

ip=192.168.1.3::192.168.1.254:255.255.255.0:server3.example.com:ens192:none nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/master.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz

ip=192.168.1.4::192.168.1.254:255.255.255.0:server4.example.com:ens192:none nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/master.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz


ip=192.168.1.5::192.168.1.254:255.255.255.0:server5.example.com:ens192:none nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/worker.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz

ip=192.168.1.6::192.168.1.254:255.255.255.0:server5.example.com:ens192:none nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/worker.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz

ip=192.168.1.7::192.168.1.254:255.255.255.0:server5.example.com:ens192:none nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/worker.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz
