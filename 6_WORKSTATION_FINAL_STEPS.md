# WORKSTATION STEPS.md
Login as root in workstation

## [Workstation] Wait for finalization of the installation
cd /var/www/okd4  <p>

## Verify NODES
export KUBECONFIG=/var/www/okd4/install_dir/auth/kubeconfig <p>
./oc get csr <p>
./oc get csr -o name | xargs ./oc adm certificate approve <p>
./oc get nodes <p>
Note: wait for all the servers in the list
  
##  Wait for installation complete

watch -n5 ./oc get clusteroperators <p>
./openshift-install --dir=install_dir/ wait-for install-complete --log-level=debug <p>
  
