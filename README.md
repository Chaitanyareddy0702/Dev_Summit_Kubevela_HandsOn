# KubeVela Hands-On

This repository is created for hands-on session on KubeVela exercise for Guidewire DevSUmmit 2025. Follow the instructions below.

## Prerequisite

- Sign-up to [Killercoda](https://killercoda.com/) using your personal Google account or GitHub account or Email-id.
- Navigate to "Playgrounds" by clicking on the "Playgrounds" tile.
- Open the "Kubernetes 1.32" playground by clicking on the "Kubernetes 1.32" tile.
- This should open the Kubernetes playground environment in Killercoda

### Step 1: Verify the setup

Check if Kubernetes is accessible in the playground by executing following commands

    kubectl get node

Step 2: Install KubeVela cli

    curl -fsSl https://kubevela.io/script/install.sh | bash

verify vela cli is installed

    vela version

### Step 2: Clone the hands-on repository

    git clone https://github.com/Chaitanyareddy0702/Dev_Summit_Kubevela_HandsOn
    cd Dev_Summit_Kubevela_HandsOn

The repository contains the kubernetes manifests which will be used for the hands-on.
Each directory contains the k8s manifest for each microservice.


### Step 3: Explore the repo

Instructor will explain the contents of repo.

    cd k8s-manifests/frontend
    ls -l
    cat deployment.yaml
    cat service.yaml
    cat serviceaccount.yaml
    cd ../..

Or **use killercoda's in-browser IDE to explore the directories**

### Step 4: install micro-services

    kubectl apply -f k8s-manifests/redis-cart

check the pod and services are up

    kubectl get pod
    kubectl get svc

Install rest of the services

    kubectl apply -f k8s-manifests/cartservice
    kubectl apply -f k8s-manifests/productcatalogservice
    kubectl apply -f k8s-manifests/shippingservice
    kubectl apply -f k8s-manifests/currencyservice
    kubectl apply -f k8s-manifests/adservice
    kubectl apply -f k8s-manifests/recommendationservice
    kubectl apply -f k8s-manifests/paymentservice
    kubectl apply -f k8s-manifests/emailservice
    kubectl apply -f k8s-manifests/checkoutservice
    kubectl apply -f k8s-manifests/frontend
    kubectl apply -f k8s-manifests/loadgenerator

Watch pods

    kubectl get po -w

### Step 5: Explore kubernetes objects

    kubectl get pod
    kubectl get svc
    kubectl get deployments

### Step 6: Access the service

Use Killercoda's "Traffic/port" functionality to access the Boutique app.

- Click on the "Menu" icon on the top right corner
- Find the port number of the frontend loadbalancer service `k get svc frontend-external`, look for "PORT(S)" column. Where you should see something like `80:31088/TCP`. In this case `31088` is the port number which wil be used later in the steps below.
-  Find the option "Traffic/Port" and click on it
-  This will redirect to an new webpage, where you will have to enter the port number of the service "frontend external" which we determined in above step. (31088 in above the illustration)
-  This should open a new page rendering the Boutique app.

### Step 6: Uninstall all services

    kubectl delete -f k8s-manifests/ -R

### Step 7: Install KubeVela controller

    vela install

verify the KubeVela controller is up

    kubectl get pod -n vela-system

### Step 8: Explore KubeVela components

Show all commands

    vela -h

explore addons

    vela addon list

explore components/traits and other defs

    vela def list

### Step 9: Install Same services using KubeVela

    vela up -f kubevela/application.yaml

check application status

    vela status microservices-demo

Access the service by following these steps
- Click on the "Menu" icon on the top right corner
- Find the port number of the frontend loadbalancer service `k get svc frontend`, look for "PORT(S)" column. Where you should see something like `80:31088/TCP`. In this case `31088` is the port number which wil be used later in the steps below.
- Find the option "Traffic/Port" and click on it
- This will redirect to an new webpage, where you will have to enter the port number of the service "frontend external" which we determined in above step. (31088 in above the illustration)
- This should open a new page rendering the Boutique app.

#### Understand application.yaml

Understand in detail what is component, trait, policy, workflow etc.

Understand which component and traits are used in current application.


### Step 10: Explore Vela UX

Enable Vela UX addon

    vela addon enable velaux

Port forward the VelUX port

    kubectl apply -f vela-ux/velaux-service.yaml

Configure KillerCoda to access the port externally

- Click on Traffic/Ports in Killercoda.
- In the Custom Ports section, enter the NodePort number of the service you created (31313).
- Click on Access to open the VelaUX.
- When prompted enter following credentials to login `Username: admin` `Password: VelaUX12345`