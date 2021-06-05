#

# 3 # Verify NODES
$ export KUBECONFIG=/var/www/okd4/install_dir/auth/kubeconfig
$ ./oc get csr
$ ./oc get csr -o name | xargs ./oc adm certificate approve
$ ./oc get nodes

# 3 #  WAIT BOOTSTRAP

$ ./openshift-install --dir=install_dir/ wait-for bootstrap-complete --log-level=debug
$ watch -n5 ./oc get clusteroperators
$ ./openshift-install --dir=install_dir/ wait-for install-complete --log-level=debug
