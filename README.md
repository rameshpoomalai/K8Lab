# K8Lab

This lab is to kick start your journey IBM Container Service, You can find instructions to execute and supporting files in this repo

# Steps:
1. Create Cluster on IBM cloud: Login with ibm cloud credentionals and create service Containers in Kubernetes Clusters from service catalog. Please refer below link.
https://console.bluemix.net/docs/containers/container_index.html#container_index
 
2. Set up IBM Cloud CLI : Command line interface to manage applications, containers, infrastructures, services
https://console.bluemix.net/docs/cli/reference/bluemix_cli/get_started.html#getting-started
verify by using command like bx help
 
3. Install and Set Up kubectl: kubectl, a Kubernetes command-line tool, to deploy and manage applications on Kubernetes.
There are multiple to option to install kubectl. I have used option "Install kubectl binary via curl".
https://kubernetes.io/docs/tasks/tools/install-kubectl/
 
4. Install the container service plugin.
bx plugin install container-service -r Bluemix

5. Gain access to your cluster
Log in to your IBM Cloud account. I have created cluster in sydney region(au-syd)
bx login -a https://api.au-syd.bluemix.net
bx cs region-set ap-south

6. Set the context for the cluster in in your CLI.
Get the command to set the environment variable and download the Kubernetes configuration files.
bx cs cluster-config <Your_Cluster_Name>

7. Set the KUBECONFIG environment variable. Copy the output from the previous command and paste it in your terminal. The command output should look similar to the following.
export KUBECONFIG=/Users/ibm/.bluemix/plugins/container-service/clusters/<your_cluster_name>/kube-config-mel01-your_cluster_name.yml
 
8. Verify that you can connect to your cluster by listing your worker nodes.
kubectl get nodes

9. Download the nginx.yaml and Run below command. 
kubectl create -f nginx.yaml
 
10. bx cs workers <your_cluster_name_created_under_ibm_cloud>
The output will be similar to as below. 
The ip marked i bold is cluster IP in my case.
 
    ID                                                 Public IP      Private IP
    kube-mel01-paedbc7786e21c450e813eadc69ebaf43b-w1   168.1.149.16   10.118.243.226
 
 
11. You can access nginx application by below url.
http://<your_cluster_ip>:30090
