# Deploy apps into EKS cluater with Helm

## 1. Create Folder Structure for files and helm template
  
  a. Create your Kubenetes Cluster - use EKSCTL for this demo

  b. helm create myawesomeapp

  c. show and explain the folder structure
 
  d. Delete the helm default value.yml content as we will create our own

  e. delete the sample helm nginx template and create your own manifest files instead. e.g deployment, service etc

## 2. Install Helm
  a. Download your desired version  "https://github.com/helm/helm/releases"

  b. Unpack it (tar -zxvf helm-v3.0.0-linux-amd64.tar.gz)

  c. Find the helm binary in the unpacked directory, and move it to its desired destination (mv linux-amd64/helm /usr/local/bin/helm)

## 3. Install Helm Chart

  a. helm install myawesomeapp-release myawesomeapp
  
  NOTE: Run this command in the parent working directory
  
  b. kubectl get pods
  
  c. kubectl get svc to get the IP to access the application

## 4. Create Helm template for your manifest and put values in values.yml file e.g

    {{ .Values.boboApp }}
    {{ .Values.namespace }}
    {{ .Values.image.name}}:{{ .Values.image.tag}}

## 5. Once Templating is done, Upgrade your Helm Release using below Command, ensure to attach --values flag since templating has been enabled

  a. helm upgrade myawesomeapp-release myawesomeapp --values <pathTovalues.yaml> e.g myawesomeapp/values.yaml 

