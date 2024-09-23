# MINIKUBE

STEPS TO INSTALL MINIKUBE 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-  Name your instance and choose ubuntu as OS, Also make a key pair for it

- Choose t3x large as instance type

- In network settings choose ssh,http,https

- Then in configure storage change it to 1x30 GiB gp3

- Then launch your instance,Copy the public ip and open putty paste the ip,Then select ssh --> auth --> credentials then browse for your key

  1 After logging in putty paste this link to install docker

       curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash

2 Then paste the following links,Add your local user to docker group so that your local user run docker commands without sudo.

    sudo usermod -aG docker $USER


    newgrp docker

3 After that run this command

      sudo snap install kubectl --classic
      
4 check the version

      kubectl version --client

5  To download and install minikube binary, run following commands

     curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64   
     sudo install minikube-linux-amd64 /usr/local/bin/minikube
     
6 To verify the minikube version, run

    minikube version

7 Now that Minikube is installed, start a Kubernetes cluster using the following command:

      minikube start --driver=docker

8 # If you encounter root privileges error, run:

    minikube start --driver=docker --force
    
9  Once the minikube has started, verify the status of your cluster, run

     minikube status

10 Use kubectl to interact with your Minikube Kubernetes cluster

    kubectl get nodes
    kubectl cluster-info

11 To deploy a sample nginx deployment, run following set of commands.

     kubectl create deployment nginx-web --image=nginx
     kubectl expose deployment nginx-web --type NodePort --port=80

12 In order to enable Dashboard , run

    minikube addons enable dashboard

13 To start the Kubernetes dashboard run below command

    minikube dashboard
    
14 run this command

    kubectl proxy --address='0.0.0.0' --disable-filter=true &

![image alt](https://github.com/Suhanjuneja/MINIKUBE1/blob/54afbc9168de4b63d7bd9bf8fd7fa80b37149f06/Screenshot%20(147).png)

15 To open the dashboard in browser run this command on your browser change the text wehere it is written server_ip and paste your public ip 

    http://server_ip:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/


![image alt](https://github.com/Suhanjuneja/MINIKUBE1/blob/432326cb77282d3d5072e230d3aa8e181cb59b17/Screenshot%20(148).png)


![image alt](https://github.com/Suhanjuneja/MINIKUBE1/blob/49d0a5a7176b3270a1ba01b88b7810d51a1c0573/Screenshot%20(149).png)
