# Kubernetes Proactive Autoscaler

## Introduction
This Kubernetes proactive autoscaler is designed to automatically scale Kubernetes deployments based on predicted computational resources usage (CPU,RAM). 

It utilizes machine learning algorithms and historical system usage data to predict future computational resources needed and then scales the deployment(s) proactively to ensure that the application can handle the increased load.

## Prerequisites

Before using this Kubernetes proactive autoscaler, you will need to have the following prerequisites:
 * A Kubernetes cluster running on Microsoft Azure
 * Service(s) deployed in the "default" namespace that you want to scale
 * [Kubernetes metrics server](https://github.com/kubernetes-sigs/metrics-server) should be enabled on your cluster

## Usage
1) Run the following command to create the namespace in which the proactive autoscaler will run in it:
  ```
 kubectl create namespace proactive-autoscaler
  ```
2) Create an Azure Managed Disk to be used by the metrics database
3) Clone the repository
4) Go the `Kubernetes-Proactive-Autoscaler\yaml` folder
5) Change the pv.yaml diskURI value
6) Change the secrets.yaml values with the values of your cluster
7) Go to the `Kubernetes-Proactive-Autoscaler\` folder and run the following command to apply the Yaml files:
```
 kubectl apply -f yaml
```
## System Architicture 
Our system consists of four components:

* Metrics Fetcher collects current system resource data and stores them
* Predictor analyzes trends in the saved metrics to forecast future resources needs
* Reasoner decides optimal resource allocation according to the current resource usage and the predictor’s forecast
* Scaler executes the reasoners scaling decisions

## Technologies Used
* Kubernetes
* Docker
* Azure cloud Computing platform
* Java
* Python
* [Fabric8 Kubernetes Client](https://github.com/fabric8io/kubernetes-client)
* [xgboost](https://github.com/dmlc/xgboost)


