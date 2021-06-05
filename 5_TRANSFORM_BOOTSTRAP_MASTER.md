
# BOOTSTRAP STEPS
Console on server1 (bootstrap ) <p>
Boot ISO: https://builds.coreos.fedoraproject.org/prod/streams/stable/builds/32.20201104.3.0/x86_64/fedora-coreos-32.20201104.3.0-live.x86_64.iso  <p>
Review the version: https://getfedora.org/en/coreos/download?tab=metal_virtualized&stream=stable <p>

# Config Boot
When is booting Press TAB <p>
Choose the correct server <p>
Change #CHANGE_DNS# with the correct <p>
If you have 2 nics you have repeat the ip <p>  

ip=192.168.1.1::192.168.1.254:255.255.255.0:server1.example.com:ens192:none  nameserver=#CHANGE_DNS# coreos.inst.install_dev=/dev/sda coreos.inst.ignition_url=http://192.168.1.11/okd4/master.ign coreos.inst.image_url=http://192.168.1.11/okd4/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz
 <p>
