KubeCtl Installations in Ec2- Ubuntu [https://www.youtube.com/watch?v=UG8wKB-CUZQ]
------------------------------------

		1.Install kubectl binary with curl on Linux
		
			curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
		
		2.Make the kubectl binary executable.
			
			chmod +x ./kubectl
		
		3.Move the binary in to your PATH.
		
			sudo mv ./kubectl /usr/local/bin/kubectl
		
		4.Test to ensure the version you installed is up-to-date:
			
			kubectl version --client

Docker Installations:
---------------------
	sudo apt-get update && \
    sudo apt-get install docker.io -y
	
Minikube Installations:
-----------------------	

		1.Install Minikube via direct download 
		
			curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
		&& chmod +x minikube
		
		2.Minikube executable to your path:
		
			sudo mkdir -p /usr/local/bin/
			sudo install minikube /usr/local/bin/
			
			sudo apt-get install -y conntrack
			minikube start --vm-driver=none
			minikube status
		
		3. To clear minikube's local state:
			
			minikube stop
			minikube delete
		
		
Examples for run our first container:
-------------------------------------

		1.Pods Creations:
		-----------------
			root@ip-172-31-38-126:~# kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080
			pod/hello-minikube created
		
			root@ip-172-31-38-126:~# kubectl get pod
			NAME             READY   STATUS              RESTARTS   AGE
			hello-minikube   0/1     ContainerCreating   0          10s
		
			root@ip-172-31-38-126:~# kubectl get pods
			NAME             READY   STATUS    RESTARTS   AGE
			hello-minikube   1/1     Running   0          16s
		
		2.Deployments:
		--------------
		
			root@ip-172-31-38-126:~# kubectl create deployment hello-minikube --image=gcr.io/google_containers/echoserver:1.4
			deployment.apps/hello-minikube created
		
		
			root@ip-172-31-38-126:~# kubectl get deployments
			NAME             READY   UP-TO-DATE   AVAILABLE   AGE
			hello-minikube   1/1     1            1           48s
		
		3.Running as services:
		----------------------
		
			root@ip-172-31-38-126:~# kubectl expose deployment hello-minikube --type=NodePort --port=8080
			service/hello-minikube exposed
			
			root@ip-172-31-38-126:~# kubectl get services
			NAME             TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
			hello-minikube   NodePort    10.109.145.248   <none>        8080:32006/TCP   16s
			kubernetes       ClusterIP   10.96.0.1        <none>        443/TCP          8m4s
			root@ip-172-31-38-126:~#

