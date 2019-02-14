# How to setup OKE and ORE environment on OCI:
1. To setup oci cli in your laptop, please follow the steps [here](https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/cliinstall.htm?tocpath=Developer%20Tools%20%7CCommand%20Line%20Interface%20(CLI)%20%7C_____1)

2. To install Kubectl on your laptop, follow the steps [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl).

3. To deploy an a Kubernetes cluster on OCI, follow the steps [here](https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-full/index.html#DefineClusterDetails)

4. To configure Kubectl with OKE configuration file, follow the steps [here](https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-full/index.html#DownloadthekubeconfigFilefortheCluster)

5. To configure OKE to access ORE registery
  1. [configure auth token for your user account](https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/registry/index.html#GetanAuthToken)
  2. [configure kubectl to use oracle registery through secret configuration](https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-and-registry/index.html#CreateaSecretfortheTutorial)

6. To configure docker to access ORE
