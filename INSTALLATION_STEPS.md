# INSTALLATION STEPS.md

## Get install binary
apt update
apt upgrade
apt install curl wget httpd
mkdir /var/www/okd4
cd /var/www/okd4
wget https://github.com/openshift/okd/releases/download/openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz
wget https://github.com/openshift/okd/releases/download/openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz
tar xvfz openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C .
tar xvfz openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C .
