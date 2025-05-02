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

    kubectl apply -f redis-cart/*
    kubectl apply -f cartservice/*
    kubectl apply -f productcatalog
    shipping
    currency
    ad
    reccomendation
    payment
    email
    checkout
    frontend
    loadgenerator

### Step 5: Uninstall all services

    kubectl delete -f all.yaml

### Step 5: Explore kubernetes objects

    kubectl get pod
    get svc
    get deployments

### Step 6: Install KubeVela controller

    vela install

verify the KubeVela controller is up

    kubectl get pod -n vela-system

### Step 7: Explore KubeVela components

Show all components

    vela def show

explore addons

    vela addon

### Step 8: Install Same services using KubeVela

    vela up application.yaml

check application status

    vela status <application-name>

Understand application.yaml


### Step 9: Explore Vela UX
