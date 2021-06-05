# INSTALLATION STEPS.md

## Get install binary
apt update <p>
apt upgrade <p>
apt install curl wget httpd  <p>
mkdir /var/www/okd4  <p>
cd /var/www/okd4  <p>
wget https://github.com/openshift/okd/releases/download/openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz <p>
wget https://github.com/openshift/okd/releases/download/openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz <p>
tar xvfz openshift-client-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C . <p>
tar xvfz openshift-install-linux-4.5.0-0.okd-2020-10-15-235428.tar.gz -C . <p>
