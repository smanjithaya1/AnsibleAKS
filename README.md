# AnsibleAKS

This document explains how to spin up an AKS cluster using ansible and then deploy an example application using ansible into AKS

Pre-requisites:
1. You must have a Azure Account
2. Azure service principal: Create a service principal, making note of the following values: appId, displayName, password, and tenant.
3. You must have a linux VM
4. You must have installed kubectl and ansible installed in the linux VM
5. You must execute these steps from that linux VM
Please Refer: https://docs.microsoft.com/en-us/azure/developer/ansible/aks-configure-clusters

Deployments Steps are as below:

a. Building the AKS Cluster
1. Clone the repo using git clone https://github.com/smanjithaya1/AnsibleAKS.git
2. execute the below commands
  cd AnsibleAKS
  ansible-playbook azure_create_aks.yml
3. The above would spin up the AKS Cluster

b. Below are the steps to deploy the sample azure-vote application:
1.   From the AKS Cluster created in the above step, please connect to the cluster using azure cli
     az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
2.  Verify your connection
     kubectl get nodes
3. Execute the below command to deploy the sample application:
     kubectl apply -f https://github.com/smanjithaya1/AnsibleAKS/blob/main/azure-vote.yaml

