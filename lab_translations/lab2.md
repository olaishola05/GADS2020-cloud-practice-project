# Google Cloud Fundamentals: Getting Started with GKE

## Overview

In this lab, you create a Google Kubernetes Engine cluster containing several containers, each containing a web server. You place a load balancer in front of the cluster and view its contents.

## Objectives

In this lab, you learn how to perform the following tasks:

-   Provision a Kubernetes cluster using Kubernetes Engine.

-   Deploy and manage Docker containers using kubectl.

## Step 1:

Enable the following APIs from Google Cloud console

In the GCP Console, on the Navigation menu, click APIs & Services.

Scroll down in the list of enabled APIs, and confirm that both of these APIs are enabled:

-   Kubernetes Engine API
-   Container Registry API

## Step 2:

Export the zone into a variable

`export MY_ZONE=us-central1-a`

Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster webfrontend and configure it to run 2 nodes:

`gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2`

Check your installed version of Kubernetes using the kubectl version command:

`kubectl version`

Check the lists of nodes running

`gcloud container clusters list`

## Run and deploy a container

`kubectl create deploy nginx --image=nginx:1.17.10`

View the pod running the nginx container:

`kubectl get pods`

Expose the nginx container to the Internet:

`kubectl expose deployment nginx --port 80 --type LoadBalancer`

View the new service:

`kubectl get services`

Open a new web browser tab and paste your cluster's external IP address into the address bar. The default home page of the Nginx browser is displayed.

Scale up the number of pods running on your service:

`kubectl scale deployment nginx --replicas 3`

Confirm that Kubernetes has updated the number of pods:

`kubectl get pods`

Confirm that your external IP address has not changed:

`kubectl get services`

Return to the web browser tab in which you viewed your cluster's external IP address. Refresh the page to confirm that the nginx web server is still responding.
