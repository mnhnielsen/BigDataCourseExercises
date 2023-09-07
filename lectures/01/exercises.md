# Lecture 01 - Kubernetes fundamentals

## Introduction to the instructors

### Nicklas Marc Pedersen

- 9th semester Software Engineering student
- Writing Master's thesis with Jakob as my supervisor
- Been instructor / supervisor for different courses
  - Instructor in Operating Systems and Distributed Systems for 3th semester Software Engineering
  - Supervisor in semester projects for 2nd and 3th semester Software Engineering

### Anders Launer Bæk-Petersen

![Anders Launer Bæk-Petersen](https://avatars.githubusercontent.com/u/28479232?v=4)
- PhD Fellow ~ Center for Energy Informatics University of Southern Denmark
    - Transferable AI Model Development Framework for Smart Energy Systems
- Industry for 4,5 years
    - Machine Learning Engineer ~ Energinet
    - Data Scientist ~ Esoft R&D
    - Research Assistant ~ Technical University of Denmark
- Master of Science in Mathematical Modelling and Computation ~ Technical University of Denmark 
- Bachelor of Science in Robot Systems ~ University of Southern Denmark 
- LinkedIn ~ [linkedin.com/in/anderslaunerbaek](https://www.linkedin.com/in/anderslaunerbaek/)

## Subject and objective for these exercises

The exercises for the first lecture are to introduce and refresh the necessary components and terminology of Kubernetes. The below-mentioned material has been sourced from [https://kubernetes.io/docs/tutorials/kubernetes-basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/) and familiarizing with this content will be sufficient for progressing along the exercises. 

The objective of this lecture is to provide the foundation for future exercise sessions and for the semester project.


## Brief introduction to Kubernetes

Kubernetes was one of the answers to moving from pure virtualization towards infrastructure as a service and being the convenient abstraction for decoupling applications and the underlying hardware.

We recommend watching the documentary [Kubernetes: The Documentary [PART 1]](https://youtu.be/BE77h7dmoQU?si=qohxiWDd52EpPoHP) and [Kubernetes: The Documentary [PART 2]](https://youtu.be/318elIq37PE?si=_Pjgstj7w_9OlsUf) to get context and history of the preliminary enablers for Kubernetes. 

### [Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

Kubernetes is a cluster orchestration system that enables the deployment of containerised applications on virtualised hardware or bare metal hardware. 

> Kubernetes is a production-grade, open-source platform that orchestrates the placement (scheduling) and execution of application containers within and across computer clusters.
*[kubernetes.io - Cluster Diagram. (Accessed: 04 September 2023)](https://kubernetes.io/docs/tutorials/kubernetes-basics/create-cluster/cluster-intro/)*

The diagram below illustrates the core components of a Kubernetes cluster. The Kubernetes cluster consists of one or multiple nodes that execute the application processes and control plane resource that coordinates the application activities across the nodes.


![Kubernetes Cluster](https://d33wubrfki0l68.cloudfront.net/283cc20bb49089cb2ca54d51b4ac27720c1a7902/34424/docs/tutorials/kubernetes-basics/public/images/module_01_cluster.svg)
*Image from [kubernetes.io - Cluster Diagram. (Accessed: 04 September 2023)](https://d33wubrfki0l68.cloudfront.net/283cc20bb49089cb2ca54d51b4ac27720c1a7902/34424/docs/tutorials/kubernetes-basics/public/images/module_01_cluster.svg)*


### [Using kubectl to Create a Deployment](https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/)


A Kubernetes deployment is the recipe for running your application. The control plane will constantly monitor the state of the application and provide self-healing actions if the current application instance is unresponsive.

![ Deploying your first app on Kubernetes](https://d33wubrfki0l68.cloudfront.net/8700a7f5f0008913aa6c25a1b26c08461e4947c7/cfc2c/docs/tutorials/kubernetes-basics/public/images/module_02_first_app.svg)
*Image from [kubernetes.io - Deploying your first app on Kubernetes. (Accessed: 04 September 2023)](https://d33wubrfki0l68.cloudfront.net/8700a7f5f0008913aa6c25a1b26c08461e4947c7/cfc2c/docs/tutorials/kubernetes-basics/public/images/module_02_first_app.svg)*

`kubectl` is the CLI for Kubernetes and the CLI can be used to create a deployment of containerized applications or manage already deployed applications, fetch logs from the application, and much more.

### [Viewing Pods and Nodes](https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/)
#### Pods

A Kubernetes Pod is an abstraction generated by a Kubernetes deployment. The Pod behaves as a logical host and is hosting one or multiple containerized applications as illustrated in the figure below.

![Pods overview](https://d33wubrfki0l68.cloudfront.net/fe03f68d8ede9815184852ca2a4fd30325e5d15a/98064/docs/tutorials/kubernetes-basics/public/images/module_03_pods.svg)
*Image from [kubernetes.io - Pods overview. (Accessed: 04 September 2023)](https://d33wubrfki0l68.cloudfront.net/fe03f68d8ede9815184852ca2a4fd30325e5d15a/98064/docs/tutorials/kubernetes-basics/public/images/module_03_pods.svg)*

#### Nodes
A Kubernetes node can be described as a worker within the Kubernetes cluster. The node is managed by the control plane and can host several different Pods as illustrated in the figure below.
![Node overview](https://d33wubrfki0l68.cloudfront.net/5cb72d407cbe2755e581b6de757e0d81760d5b86/a9df9/docs/tutorials/kubernetes-basics/public/images/module_03_nodes.svg)
*Image from [kubernetes.io - Node overview. (Accessed: 04 September 2023)](https://d33wubrfki0l68.cloudfront.net/5cb72d407cbe2755e581b6de757e0d81760d5b86/a9df9/docs/tutorials/kubernetes-basics/public/images/module_03_nodes.svg)*


### [Using a Service to Expose Your App](https://kubernetes.io/docs/tutorials/kubernetes-basics/expose/expose-intro/)


Each Kubernetes Pod has a different IP address as seen in the figure above. These IP addresses are local to the cluster and not accessible from outside the cluster. For some applications, we need to have an abstraction, which maps external traffic to the deployment (Pod) of interest. The Pods have a lifecycle and their IP address change due to rescheduling to another node.

![Services and Labels](https://d33wubrfki0l68.cloudfront.net/7a13fe12acc9ea0728460c482c67e0eb31ff5303/2c8a7/docs/tutorials/kubernetes-basics/public/images/module_04_labels.svg)
*Image from [kubernetes.io - Services and Labels. (Accessed: 04 September 2023)](https://d33wubrfki0l68.cloudfront.net/7a13fe12acc9ea0728460c482c67e0eb31ff5303/2c8a7/docs/tutorials/kubernetes-basics/public/images/module_04_labels.svg)*

A Kubernetes Service is the abstraction we need to provide a loosely coupling Pods and external traffic. There are multiple types of Services: 
- ClusterIP
- NodePort
- LoadBalancer
- ExternalName

Get full definitions here: [Overview of Kubernetes Services](https://kubernetes.io/docs/tutorials/kubernetes-basics/expose/expose-intro/)

> A Kubernetes Service is an abstraction layer which defines a logical set of Pods and enables external traffic exposure, load balancing and service discovery for those Pods. 
*[kubernetes.io - Using a Service to Expose Your App. (Accessed: 04 September 2023)](https://kubernetes.io/docs/tutorials/kubernetes-basics/expose/expose-intro/)*

## Exercises

### Exercise 1 - Kubernetes setup

You need a working Kubernetes cluster to solve the exercises for this lecture and the following lectures. The choice of distribution should technically not matter, but we recommend you use minikube because the exercises will assume you use that.

To install minikube, go to their [getting started](https://minikube.sigs.k8s.io/docs/start/) page and follow the instructions. Note: If you are on Windows we suggest you install using [chocolatey](https://chocolatey.org/install#individual) because it can be used to install other tools that will be used for the exercises.

The tool used to communicate with a Kubernetes cluster is called "kubectl". It is also installed with minikube and can be used using `minikube kubectl -- <command>`. You can also just [install kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).

Once minikube is installed, you can start and stop it using `minikube start` and `minikube stop`. If you use Docker Desktop, you may notice that it has created a container and a volume called "minikube".

### Exercise 2 - Deploy "Hello World" application

The first thing you will be doing with the Kubernetes cluster is to deploy a hello world application. The application can be found on GitHub [paulbouwer/hello-kubernetes](https://github.com/paulbouwer/hello-kubernetes). A yaml file to deploy the application can be found [here](./hello-kubernetes.yaml).

The yaml file contains two resources, a deployment and a service. Deployments are used to create pods, and services are used to route traffic to the pods using label selectors. A major part of Kubernetes is the use of labels and selectors. Labels are key-value pairs that can be used for filtering.

Inspect the yaml manifest and understand the different parts of it:

- Identify the two resources
- Identify the labels and selectors. How are they used?
- Try to understand how the environment variables are added to the pods.

Now that you have looked through the yaml you may have figured out the following:

- The deployment creates 3 pods
- The pods have 3 environment variables that uses a "fieldRef"
- The container listens on port 8080.
- The service listens for traffic on port 8080 and routes it to port 8080 inside the pod.

The `fieldRef` inside the environment variables is used to reference a field of the pod and use the value of it as an environment variable.

- `metadata.namespace` is used to reference the namespace that the pod is inside. When no namespace is provided for a resource, then the "default" namespace is used.
- `metadata.name` is used to reference the name of the pod. The name is automatically generated using the name of the replica set + a random string for each pod. The name of the replicaset comes from the name of the deployment + a hash to uniquely identify the revision.
- `spec.nodeName` is used to reference the name of the node that the pod is scheduled to run on.

Now that you understand the yaml file, run the command `kubectl apply -f hello-kubernetes.yaml` to apply the resources to the Kubernetes cluster. You can then use `kubectl get pods` to get a list of the pods and `kubectl get service` to get a list of the services.

### Exercise 3 - Connecting to the application

Now that you have deployed the application the next step is to try and connect to it. The application is a HTTP server that listens for requests on port 8080. To connect to the application, we should do it through the service.

Connecting to a service can be done in different ways. The simplest way to connect to a service from outside of the cluster is to use either the `kubectl port-forward` command, or the `minikube service` command.

To use the `kubectl port-forward` command, run the following command `kubectl port-forward svc/hello-kubernetes 8080:8080`. The command will open a port on your local machine and forward traffic to a port on the service. In this case, it is 8080 on both your local machine and the service, but it could be changed to `9000:8080` to use port 9000 on your local machine and forward it to port 8080 on the service. Open a browser and go to [http://localhost:8080](http://localhost:8080) to access the service.

To use the `minikube service` command, run the following command `minikube service hello-kubernetes`. The command will pick a random open port on your local machine, port-forward to the service using that port, and open a window with the correct path in your default browser. You can read more about the command [here](https://minikube.sigs.k8s.io/docs/commands/service/).

Now that you can connect to the application, try and understand the web page. The webpage gives different information about the pod that was handling your request. It displays the pod name, the namespace the pod is inside, and the node that the pod is running on.

Try to refresh the webpage a few times and notice how the values change. You should see that the name of the pod changes. This is because the request was routed to a different pod.

### Exercise 4 - Scaling the application

Some programs are stateless and designed to have multiple instances of the same program running. In the case of the hello-kubernetes application, you can increase and decrease the amount of replicas with no problem. It may be desirable to scale your deployment up or down to match the demand of the application. There are two ways to scale deployments in Kubernetes - manual, or automatic. Automatic scaling will not be covered in this exercise.

To manually scale a deployment, you would modify the `replicas` field of the deployment resource. This can be done by either modifying the yaml file and reapplying it, or by using the edit command. To edit the deployment using the edit command, use the following: `kubectl edit deployment/hello-kubernetes`. This will open a window with your default text editor. Simply modify the file, save it, and close the window to modify the resource.

1. Try to change the replica count to 5.
2. Check that the amount of pods has changed to 5
3. Try accessing the application to verify it still works
4. Change the replicas back to 3
5. Check that the amount of pods has changed to 3
6. Try accessing the application to verify it still works

When scaling the amount of replicas, the service will automatically start/stop routing traffic to the new/old pods without disrupting existing connections.

### Exercise 5 - Adding more nodes

You are using minikube is on your local machine to run Kubernetes. In the real world, you would have many virtual machines on many different physical machines. Each virtual machine would run Kubernetes and be connected to the other machines to form a Kubernetes cluster. The cluster you have on your machine only has a single node. You can verify this using `kubectl get nodes`. But with minikube you can very easily add and remove nodes.

Use `minikube node add` to add a new node to the cluster and `minikube node delete <name of node>` to delete a node.

Try to create two new nodes and then scale the hello-kubernetes deployment to 10 pods. Try refreshing the webpage a couple of times. You should notice that your requests gets routes to pods on the different nodes. You can also use `kubectl get nodes` to see the new nodes. To see what nodes the pods are running on, use `kubectl get pods -o wide` to get extra information about the pods. You should see that the hello-kubernetes pods are spread out on the different nodes.

Now we want to try to delete the two nodes that you created. Open a new terminal window and use the following command `kubectl get pods -o wide -w`. This command will watch for changes and print them to the terminal. Now try to delete the nodes that you just created and notice how the hello-kubernetes pods that previously ran on the nodes gets terminated and that new pods are created and scheduled to run on the other nodes.

### Exercise 6 - Deploying application using Helm

[Helm](https://helm.sh/) is a package manager for Kubernetes. Helm simplifies the process of deploying and managing applications on Kubernetes by providing a standardized way to package, distribute and manage Kubernetes resources. Helm packares are called "charts". A chart is a collection of files that describes a set of Kubernetes resources along with configurations. Charts can be customized to suit specific deployment requirements.

To install Helm go to their [install](https://helm.sh/docs/intro/install/) guide. For Windows users who has chocolatey installed already, simply run `choco install kubernetes-helm`.

The hello-kubernetes application that you deployed earlier has a Helm chart. Go to the repository [paulbouwer/hello-kubernetes](https://github.com/paulbouwer/hello-kubernetes) on GitHub and download / clone.

To install the chart using the default values, simply open a terminal inside the hello-kubernetes repository you just cloned and type the command `helm install hello-kubernetes ./deploy/helm/hello-kubernetes`. This will install the Helm Chart located at `./deploy/helm/hello-kubernetes` and give the release the name "hello-kubernetes". You can see the status of the Helm release using `helm status hello-kubernetes`. Get a list of the pods and services and see what was created.

You should see that it created 3 pods and 1 service. This is similar to the deployment you made before, except this is installed using Helm. But now that it is installed you should try to connect to it like before, just remember that the service is now called something different. Hint: `kubectl get services`.

A Helm chart can be configured using "values". The default values can be found inside the Helm chart. Open the file located at `./deploy/helm/hello-kubernetes/values.yaml` and see the different values. We want to try to increase the amount of replicas using the `deployment.replicaCount` value. Because we want to modify an existing release, we need to use the `helm upgrade` command. Use `helm upgrade hello-kubernetes ./deploy/helm/hello-kubernetes --set deployment.replicaCount=5` to set the replica count to 5. Now get a list of the pods and notice how the amount of pods changed.

You can get a list of all Helm releases in the default namespace using the following command `helm list`.

### Exercise 7 - Interactive container

Similarly to Docker, you can create an interactive container with Kubernetes. You can also get a shell inside an already running container.

First, we will try to get a shell inside an existing container. The command to execute commands inside containers is called exec, for example `kubectl exec pods/<name of pod> -- <command>` will run a command inside a running container. To get an interactive shell, you need to use the exec command: `kubectl exec --stdin --tty pods/<name of pod> -- <command>`. To get a shell for one of the hello-kubernetes pods you need to use this: `kubectl exec --stdin --tty pods/<name of pod> -- /bin/sh`.

Once you have a shell you can now run commands inside of it. Try using the `ls` command to list all files and folder inside the current directory. You may notice that this is a NodeJS application. Try to list the contents of the `server.js` file using the `cat` command.

To exit the interactive shell write `exit` and hit the `ENTER` key or just close the terminal window.

You will now create an interactive container that is removed once you exit the shell. Run the following command: `kubectl run ubuntu --rm -i --tty --image ubuntu -- bash`. This will create a pod called "ubuntu" that will run the Ubuntu image. Once you exit the terminal the pod will be deleted.

Because the container is running inside the Kubernetes cluster you can now access services without using the port-forward command. To test this we first want to intall the curl package - use `apt update && apt install curl -y` to install curl. Once curl is installed, write the following command to send a HTTP request to the hello-kubernetes service: `curl hello-kubernetes:8080`. The response will be the HTML for the hello-kubernetes webpage that you have seen earlier. You can try using the command multiple times and see how the response changes.

Because the service is inside the same namespace as your ubuntu container you can use the DNS entry `hello-kubernetes`. If you want to accesss a service in a different namespace you need to use a different hostname. Use the following command `curl hello-kubernetes.default:8080` where `default` is the namespace that the hello-kubernetes deployment is made in.

Exit the terminal using the exit command.

Sometimes you don't want to delete the container when you exit the shell. Use the following command to create an ubuntu container that won't be deleted when you exit the shell: `kubectl run ubuntu -i --tty --image ubuntu -- bash`. To reattach the same shell again use one of the following command: `kubectl attach ubuntu -c ubuntu -i -t`. You can even open two terminals and use the attach command and the shell will be shared. Try to do this and write something in one shell and see how it is also written in the other.

You can also copy files to containers. Create a file on your local machine called "test.txt" and enter some random text. Open a new terminal inside the directory that you created the file, and use the following command to copy the test.txt file to the ubuntu container: `kubectl cp test.txt ubuntu:/test.txt`. Open the other terminal again and use the `ls` and `cat` commands to verify the file was copied to the container.

### Exercise 8 - Cleaning up

Kubernetes resources can be deleted using the `kubectl delete` command. You can either delete individual resources, such as a the hello-kubernetes deployment using the following command `kubectl delete deployment/hello-kubernetes`, or you can delete it using the file you used to create the resources with using the command `kubectl delete -f hello-kubernetes.yaml`. If you used Helm to create the resources then you should also delete it using Helm.

- To begin with, we will delete the first hello-kubernetes deployment that you made using the yaml manifest file: `kubectl delete -f hello-kubernetes.yaml`
- Next we will uninstall the hello-kubernetes release of the hello-kubernetes Helm chart: `helm uninstall hello-kubernetes`
- Delete the ubuntu container: `kubectl delete pods/ubuntu`

You can get a list of the pods and services to verify that they are deleted.