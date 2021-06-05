# WORKSTATION STEPS.md
Login as root in workstation

## [Workstation] Verify Nodes
export KUBECONFIG=/var/www/okd4/install_dir/auth/kubeconfig <p>
./oc get csr <p>
./oc get csr -o name | xargs ./oc adm certificate approve <p>
./oc get nodes <p>

## [Workstation] Wait for terminate the bootsrap
./openshift-install --dir=install_dir/ wait-for bootstrap-complete --log-level=debug <p>

 
