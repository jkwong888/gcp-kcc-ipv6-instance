# gcp-kcc-ipv6-instance

Messing around with GCE instances with IPv6 external IPs on GCP (specifically for automating turn server creation)

This requires [Config Connector](https://cloud.google.com/config-connector/docs/overview) to be installed in your cluster.  I have a sample install on my shared VPC in the [terraform](./terraform) directory, the key is to give the config connector service account the right permissions.  I used the [operator install](https://cloud.google.com/config-connector/docs/how-to/install-other-kubernetes#installing) and then used the [custom resource](./configconnector-operator/configconnector.yaml) to configure it (you can see my project name `jkwng-kubevirt-dev-2` while this actually has nothing to do with kubevirt at all :( )  

there's two resources in here [cc_subnet.yaml](./cc_subnet.yaml) which creates an IPv6 subnet in us-west2, then [cc_vm.yaml](./cc_vm.yaml), that creates a VM with dual stack external IPv4 and IPv6 IP addresses.

