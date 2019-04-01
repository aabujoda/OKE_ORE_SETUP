# How to setup and configure OKE and ORE environment:

This is a step by step tutorial to setup an enviroment to work with Oracle Kubernetes Engine and Oracle Regsitery. The tutorial is a collection of oracle offical documentations that are available online. You should follow the steps in order to prepare your environment. If have already worked with Oracle OCI CLI as a part of other OCI activities, the first step might not be required for you. You can go directly to the second step and start intalling Kubectl.

1. To setup **_OCI_** **_Cli_** in your laptop, please follow the steps [here](https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/cliinstall.htm?tocpath=Developer%20Tools%20%7CCommand%20Line%20Interface%20(CLI)%20%7C_____1)

2. To install **_Kubectl_** on your laptop, follow the steps [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). 
For oracle linux you can directly use the following command:
   ```
   yum install -y kubectl
   ```

3. To deploy a Kubernetes cluster on OCI, follow step number 2 [here](https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-full/index.html#DefineClusterDetails)

4. To configure **_Kubectl_** with OKE configuration file, follow the step number 3 in the documentation [here](https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-full/index.html#DownloadthekubeconfigFilefortheCluster)

5. To configure OKE to access ORE registery

   1. Generate an auth token for your user account:      
   
      1. In the top-right corner of the Console, open the User menu (), and then click User Settings.
     
         ![alt text](https://github.com/aabujoda/OKE_ORE_SETUP/blob/master/oci-console-settings.png) 
    
      2. On the Auth Tokens page, click Generate Token.
    
         ![alt text](https://github.com/aabujoda/OKE_ORE_SETUP/blob/master/oci-console-settings.png)
 
      3. Enter "Tutorial auth token" as a friendly description for the auth token and click Generate Token. The new auth token is displayed.

      4. Copy the auth token immediately to a secure location from where you can retrieve it later, because you won't see the auth token again in the Console. This token will be your docker password for the next step

      5. Close the Generate Token dialog.

   2. [configure kubectl to use oracle registery through secret configuration](https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-and-registry/index.html#CreateaSecretfortheTutorial)
   
       To enable Kubernetes to pull an image from Oracle Cloud Infrastructure Registry when deploying an application, you need to create a Kubernetes secret. The secret includes all the login details you would provide if you were manually logging in to Oracle Cloud Infrastructure Registry using the docker login command, including your auth token.
       
       1. In a terminal window, enter the following command:

       
           ```
           $ kubectl create secret docker-registry ocirsecret --docker-server=<region-code>.ocir.io --docker-username='<tenancy-name>/<oci-username>' --docker-password='<oci-auth-token>' --docker-email='<email-address>'
           ```
           where:
           
               
             * ocirsecret is the name of the secret you're creating, and that you'll use in the manifest file to refer to the secret. For the purposes of this tutorial, you must name the secret ocirsecret. When you've completed the tutorial and are creating your own secrets for your own use, you can choose what to call your secrets. 
               
             * &lt;<region-code&lt;> is the code for the Oracle Cloud Infrastructure Registry region you're using. For example, fra for the frankfurt region
             * ocir.io is the Oracle Cloud Infrastructure Registry name.
               <tenancy-name> is the tenancy containing the repository from which the application is to pull the image. For example, acme-dev
               
             * <oci-username> is the username to use when pulling the image. The username must have access to the tenancy specified by tenancy-name. For example, jdoe@acme.com. If your tenancy is federated with Oracle Identity Cloud Service, use the format /oracleidentitycloudservice/<oci-username>.
               
             * <oci-auth-token> is the auth token of the user specified by oci-username. For example, k]j64r{1sJSSF-;)K8
               
             * <email-address> is an email address. An email address is required, but it doesn't matter what you specify. For example, jdoe@acme.com
       
         2. Example for kubectl to use the registery: 

            ```
            kubectl create secret docker-registry ocirsecret --docker-server=fra.ocir.io --docker-     username='tenancy1/oracleidentitycloudservice/john.smith@oracle.com' --docker-password='xrczDCLn.7(we3H.6cmiuwz' --docker-email='john.smith@oracle.com'
            ```
