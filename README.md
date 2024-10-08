# MINIKUBE

# What is MINI KUBE

Minikube is a tool that allows you to run a local Kubernetes cluster on your machine. It's particularly useful for developers who want to experiment with Kubernetes without needing a full-fledged cloud setup. Minikube creates a single-node cluster inside a virtual machine (or as a container) on your local system, making it easy to deploy, manage, and test applications in a Kubernetes environment.

Here are some key features of Minikube:

- Local Development: You can easily test and develop applications that will run in Kubernetes.

- Multiple Drivers: Supports various virtualization drivers like VirtualBox, VMware, and Docker, so you can choose the one that works best for your environment.

- Add-ons: Minikube comes with several built-in add-ons that can be enabled or disabled as needed, such as metrics-server, Ingress controllers, and more.

- Easy Setup: Quick to install and set up, allowing you to get a Kubernetes environment running in minutes.

STEPS TO INSTALL MINIKUBE 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-  Name your instance and choose ubuntu as OS, Also make a key pair for it

- Choose t3x large as instance type

- In network settings choose ssh,http,https

- Then in configure storage change it to 1x30 GiB gp3

- Then launch your instance,Copy the public ip and open putty paste the ip,Then select ssh --> auth --> credentials then browse for your key

![image alt](https://github.com/Suhanjuneja/MINIKUBE1/blob/e7c324f39b9c4efffb5a0d9ddfaed3362d31e65e/Screenshot%20(135).png)

![image alt](https://github.com/Suhanjuneja/MINIKUBE1/blob/e747651ffe778afffb76551a8e4609c45ec59606/Screenshot%20(136).png)

  1 After logging in putty paste this link to install docker

       curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash

![image alt](https://github.com/Suhanjuneja/MINIKUBE1/blob/f0dd08e4872ccfda55878c5916e7c69d642c879e/Screenshot%20(140).png)

2 Then paste the following links,Add your local user to docker group so that your local user run docker commands without sudo.

    sudo usermod -aG docker $USER


    newgrp docker

![image alt](https://github.com/Suhanjuneja/MINIKUBE1/blob/e40dcf788358329c9c8be1baa71a36a347a1d965/Screenshot%20(145).png)

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
