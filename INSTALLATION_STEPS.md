# INSTALLATION STEPS.md

## [Workstation] Get install binary
apt update <p>
apt upgrade <p>
apt install curl wget httpd  <p>
mkdir /var/www/okd4  <p>
cd /var/www/okd4  <p>
wget https://github.com/openshift/okd/releases/download/openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz <p>
wget https://github.com/openshift/okd/releases/download/openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz <p>
wget https://builds.coreos.fedoraproject.org/prod/streams/stable/builds/32.20201104.3.0/x86_64/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz <p>
wget https://builds.coreos.fedoraproject.org/prod/streams/stable/builds/32.20201104.3.0/x86_64/fedora-coreos-32.20201104.3.0-metal.x86_64.raw.xz.sig <p>
tar xvfz openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C . <p>
tar xvfz openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C . <p>

## [Workstation] Review config files
  
