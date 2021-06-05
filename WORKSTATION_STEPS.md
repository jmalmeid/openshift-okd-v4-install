# WORKSTATION STEPS.md
Login as root in workstation

## [Workstation] Install HTTPD
apt update <p>
apt upgrade <p>
apt install curl wget httpd  <p>
mkdir -p /var/www/okd4/install_dir  <p>
chown -R apache:apache /var/www/okd4 <p>
cp okd4.conf /etc/httpd/conf.d/okd4.conf <p>
systemctl enable httpd <p>
systemctl start httpd <p>

## [Workstation] Get install binary
cd /var/www/okd4  <p>
wget https://github.com/openshift/okd/releases/download/openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz <p>
wget https://github.com/openshift/okd/releases/download/openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz <p>
wget https://builds.coreos.fedoraproject.org/prod/streams/stable/builds/32.20201104.3.0/x86_64/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz <p>
wget https://builds.coreos.fedoraproject.org/prod/streams/stable/builds/32.20201104.3.0/x86_64/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz.sig <p>
tar xvfz openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C . <p>
tar xvfz openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C . <p>

## [Workstation] Review config files

Edit install-config.yaml <p>
Edit cluster-network-03-config.yml

## [Workstation] Prepare files
cd /var/www/okd4  <p>
rm -rf install_dir <p>
mkdir install_dir <p>
cp install-config.yaml install_dir/. <p>
./openshift-install create manifests --dir=install_dir/ <p>
sed -i 's/mastersSchedulable: true/mastersSchedulable: False/' install_dir/manifests/cluster-scheduler-02-config.yml <p>
cp cluster-network-03-config.yml install_dir/manifests/cluster-network-03-config.yml <p>
./openshift-install create ignition-configs --dir=install_dir/ <p>
cp fedora-coreos* install_dir/.  <p>
chown -R apache:apache . <p>

## [Workstation] Test http
curl http://<worksation ip>/okd4/master.ign

  
