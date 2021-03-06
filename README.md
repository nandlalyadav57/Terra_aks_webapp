# Terra_aks_webapp

**Project setup**

Refer : https://ny55.blogspot.com/2021/05/deploy-kubernetes-cluster-using.html

Prerequisites:

1.An Azure account
2.Git 
3.Azure CLI
4.Terraform CLI





**az login**


**git clone https://github.com/nandlalyadav57/terra_aks_webapp.git**




Need to run terraform init. This would download any plugins that the Azure provider depends on.


$ **terraform init**





Created a variable for it earlier. if you have an ssh key pair you can skip this step
$ ssh-keygen -t rsa -b 4096




Export the key into an environment variable.
$ **export TF_VAR_ssh_key=$( cat ~/.ssh/id_rsa.pub)**






Before we actually create our infrastructure its always a good idea to see what exactly Terraform would be creating luckily Terraform has a command for that
$ **terraform plan**



If every thing looks good we can apply our configuration using:
$ **terraform apply**






Once the resources have been provisioned head over to your azure dashboard a look
Go to your newly build AKS Cluster  (Check details by clicking on connect from Azure Dashboard)

**az account set --subscription 95798dc6-679a-4a59-914e-6dsdgfsd74**


**aks get-credentials --resource-group kubernetes-resource-group --name yourcluster**



**kubectl get nodes -o wide**


Now Let's deploy a simple web application which is using redis

**kubectl create namespace myvote**


**kubectl apply -f azure-vote.yaml -n myvote **


or use this:



**kubectl apply -f https://raw.githubusercontent.com/nandlalyadav57/terra_aks_webapp/main/azure-vote.yaml?token=AIAXGZX4NW7UPQUMDVTWWNLASTZEE -n myvote **



**kubectl get all -n myvote**




To manually change the number of pods in the azure-vote-front deployment, 
use the kubectl scale command. The following example increases the number of front-end pods to 5:




**kubectl scale --replicas=5 deployment/azure-vote-front -n myvote**



kubectl get all -n myvote

kubectl autoscale command to autoscale the number of pods in the azure-vote-front deployment. 
If average CPU utilization across all pods exceeds 50% of their requested usage



**kubectl autoscale deployment azure-vote-front --cpu-percent=50 --min=3 --max=10  -n myvote ** 


https://ny55.blogspot.com/2021/05/deploy-kubernetes-cluster-using.html





 
