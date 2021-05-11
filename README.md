# istio-grpc-minikube (Golang)

This is simple implementation of GRPC with Istio.
In this example I have used minikube as local cluster , docker to containerized the application and Istio Service mesh as Gateway and Load-balancer.

for this example I have used following versions
 minikube version: v1.19.0
 docker desktop version 3.3.2 engine version v20.10.5
 istio version 1.9.4
 
 you will need go-compiler installed on your machine to run this example

# setup : 
 I have  used minikube on windows using wsl2 and docker-desktop if you have windows 10 then follow following steps 

step 1:
Install and enable settings for wsl-2 : https://docs.microsoft.com/en-us/windows/wsl/install-win10

step 2:
install the docker desktop for windows and  open the docker dashboard , go to the settings and enable checkbox showing wls2 and enable the ubuntu on docker

step 3:
install the latest version of Ubuntu from MS-store and setup your ubuntu on windows

step 4:
download or fork the code , go to file localtion of the code and on that file location open wsl thorugh vscode or cmd (to open wsl , you just have to type wsl on vscode terminal or cmd)

step 5:
 1. Now run the following command to download and install minikube on same wsl terminal ==>
 curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
 sudo install minikube-linux-amd64 /usr/local/bin/minikube

 2. now run the command "minikube config set driver docker" to set driver as docker
 
 3. now run the command "minikube start --memory=4096 --cpus=4" to start kubernetes cluster

step 5:
now download  the latets version of istio, folder will be created on same file-directory go that folder and install the istio with demo profile and Add a namespace label to instruct Istio to automatically inject Envoy sidecar proxies

you can follow first 5 steps from following link to setup istio :
  https://istio.io/latest/docs/setup/getting-started/

step 6 : 
now copy the folder name istio-yaml from my source code and paste inside istio-1.9.4 folder (I am using 1.9.4 version but in future your version might be different ) 

step 7:
now execute following command to create deployments, services , pods ,gateways (to execute following command you must be inside istio folder with wsl terminal)
  "kubectl apply -f istio-yaml/grpc.yaml"
  
step 8:
now run the following command in the different terminal and keep the process running on that wsl terminal
 "minikube tunnel"
 
step 9 :
now you have setup the istio , time to run client run 
open new terminal and got to localtion of client folder in source code and run the command "go run client.go"
you will get the output 

Thank you

note : If you encounter any error then feel free to mail me on "rupeshspund@gmail.com"
