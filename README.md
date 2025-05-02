# KubeVela Hands-On

This repository is created for hands-on session on KubeVela exercise for Guidewire DevSUmmit 2025. Follow the instructions below.

## Prerequisite

- Sign-up to [Killercoda](https://killercoda.com/)
- Create a Kubernetes playground in Killercoda

### Step 1: Verify the setup

Check if Kubernetes is accessible in the playground by executing following commands

    kubectl get node

Step 2: Install KubeVela cli

    curl -fsSl https://kubevela.io/script/install.sh | bash

verify vela cli is installed

    vela --version

### Step 2: Clone the hands-on repository

    git clone https://github.com/Chaitanyareddy0702/Dev_Summit_Kubevela_HandsOn
    cd Dev_Summit_Kubevela_HandsOn

The repository contains the kubernetes manifests which will be used for the hands-on.
Each directory contains the k8s manifest for each microservice.


### Step 3: Explore the repo

Instructor will explain the contents of repo.

    cd frontend
    ls -l
    cat deployment.yaml
    cat service.yaml
    cat serviceaccount.yaml

Or use killercoda's in-browser IDE to explore the directories

### Step 4: install micro-services

    kubectl apply -f k8s-manifests/redis-cart/*
    kubectl apply -f k8s-manifests/cartservice/*
    kubectl apply -f k8s-manifests/productcatalogservice/*
    kubectl apply -f k8s-manifests/shippingservice/*
    kubectl apply -f k8s-manifests/currencyservice/*
    kubectl apply -f k8s-manifests/adservice/*
    kubectl apply -f k8s-manifests/recommendationservice/*
    kubectl apply -f k8s-manifests/paymentservice/*
    kubectl apply -f k8s-manifests/emailservice/*
    kubectl apply -f k8s-manifests/checkoutservice/*
    kubectl apply -f k8s-manifests/frontend/*
    kubectl apply -f k8s-manifests/loadgenerator/*

### Step 5: Explore kubernetes objects

    kubectl get pod
    get svc
    get deployments

### Step 6: Uninstall all services

    kubectl delete -f k8s-manifests/all.yaml

### Step 7: Install KubeVela controller

    vela install

verify the KubeVela controller is up

    kubectl get pod -n vela-system

### Step 8: Explore KubeVela components

Show all components

    vela def show

explore addons

    vela addon

### Step 9: Install Same services using KubeVela

    vela up application.yaml

check application status

    vela status <application-name>

Understand application.yaml


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