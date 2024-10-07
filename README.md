# devops interview questions
![image](https://github.com/user-attachments/assets/b31d6869-26c7-4993-bb66-0718d42a4809)


this repo contains questions and exercises on various technical topics, related to DevOps
## questions:

<details>
<summary>What is the difference between tcp and udp?</summary><b>
Both are communication protocols, tcp is a connection-based protocol, it establishes a connection before it starts sending information and after it is finished it closes, so it is more reliable but less fast than udp which is not connection-based.
</b></details>

<details>
<summary>What is a context switch?</summary><b>
An operation of the processor that allows processes to run concurrently, the processor takes a sort of snapshot of the current state of the registers in memory, keeps it aside and moves on to work on another process.
Because the operation is performed at high speed, it appears as if the processor is running the processes in parallel.
</b></details>

<details>
<summary>What is a deadlock?</summary><b>
A deadlock is a situation in which one process tries to access a certain resource that a second process uses while the second process tries to access a resource that the first process uses and a situation is created where no one can progress.
</b></details>

<details>
<summary>What is the difference between process and thread?</summary><b>
process is basically software that runs on the processor with resources defined for Process, it does not share these resources with other Processes.
A thread, on the other hand, is part of a process, a process can have several threads running at the same time that will share its resources.
</b></details>

<details>
<summary>What is the difference between deployment and statefulset?</summary><b>

deployment is intended for applications that are stateless such as web servers such as nginx and apache that do not need permanent storage while statefulset is more suitable for applications that are stateful such as DBs.

In terms of deployment, the pods can be replaced all the time while sts keeps a unique ID for each pod it manages and uses this ID when it needs to reschedule these pods.
Each pod in sts has its own DNS name that does not change, if the pod dies the IP can change but its DNS name will remain the same, this is realized by headless service, the DNS names include the serial number of the pod.

Each replica in sts has its own state, with pvc for each pod, for example sts with 4 replicas, will create 4 pods where each pod has its own volume and its own pvc.
In deployment the pods share volume and pvc while in sts each pod has its own volume and pvc.
</b></details>

<details>
<summary>Why are containers better than VMs?</summary><b>

Containers have already become the standard in the market, they replace VMs mainly because they provide better utilization of resources because they share the same operating system with other containers.
Virtual machines are more resource optimization at the infrastructure level, instead of needing a server for each application you can set up several virtual servers on the same hardware, the servers will be completely isolated from each other, each will have its own operating system and they can sit on the same hardware even if their operating system different.

Because a container contains exactly what it needs to run, it takes less time to upload and download a container because the weight of its image is usually measured in megabytes than to upload and download a machine whose image weight will usually be several gigabytes, in addition you can run several containers on the same vm so you can run multiple applications on the same machine.
</b></details>

<details>
<summary>What is affinity and anti-affinity in k8s?</summary><b>

Affinity - chooses where to put the pod according to the labels of the node.

Anti-affinity - prevents the pods from being scheduled on the same node or close to each other, and ensures separation. Helps in distributing loads over different nodes
</b></details>

<details>
<summary>What is daemonset in k8s?</summary><b>
It's a component that uploads a pod on every node in the cluster. This is for example for an agent that pulls metrics on the node like the node exporter in Prometheus.
</b></details>

<details>
<summary>What is PV and PVC?</summary><b>

PV (Persistent Volume):
is a physical or virtual storage unit in k8s. This is an independent disk intended to include application data in k8s.

PVC (Persistent Volume Claim):
is the request made by the user (in a pod) to receive storage from the PV
</b></details>

<details>
<summary>What is helm?</summary><b>
its a tool for managing and installing applications in Kubernetes.
It allows you to organize your applications within units that wrap each application called charts, and it allows you to install them easily and you can change things in the application through one file where we simply change the values.
</b></details>

<details>
<summary>What is ingress?</summary><b>
It is a component that routes requests by subdomain, as soon as it is created it addresses a certain controller that creates an external LB and its uniqueness is that it is possible through one LB to access several services by subdomain or path.
</b></details>

<details>
<summary>What are the differences in services in k8s?</summary><b>


cluster ip:
This is the basic type of every service and it only gives us internal access to the service without access from the outside

NodePort:
It uses the public ip of the node where the pod is located and gives us access to the service through a certain port

load balancer:
As soon as it is created, it creates an NLB in the cloud that is configured and as soon as we access the created NLB, it leads us to the service
</b></details>

<details>
<summary>What is kube-scheduler?</summary><b>
It is a component in k8s that is responsible for scheduling created pods into nodes in the cluster. Its main purpose is to select suitable nodes for pods based on various factors such as resource requirements.
</b></details>

<details>
<summary>What is hpa and vpa?</summary><b>
These are two components in k8s that are responsible for auto scaling to pods in deployment
Based on cpu and memory, and each one does auto scaling with a different approach.
 hpa does scaling by increasing and decreasing the amount of pods in the deployment.
On the other hand, the vpa does scaling by increasing and decreasing the resources allocated to the pods in the deployment.
</b></details>

<details>
<summary>What is liveness probe and what is readiness probe?</summary><b>
 
kubelet uses liveness probe in order to know when to restart the container, for example, liveness probe can detect a deadlock situation in which the application cannot continue, and restart it.

kubelet uses readiness probes to know when a pod is ready to start receiving traffic A pod is considered "ready" when all its containers are ready, this is used to control pods that are used as backends for services, when a pod is not ready it is removed from the service's load balance list.

kubelet uses startup probes to know when a container started, if this probe is configured, it cancels the livesness probes and the readiness probes until it succeeds.
The use for this is to allow containers that rise slowly time to rise instead of being killed by the kubelet before they finish rising.
</b></details>

<details>
<summary>What is Multi-container pod?</summary><b>
It is a pod with more than one container whose containers can communicate with each other easily, we use it in the way we say there is one site container and another monitoring container that monitors it or containers that use the same volume and it is easier for them to share information with each other.
</b></details>

<details>
<summary>What are limits in k8s?</summary><b>
There is a request and there are limits, where in limits we define a limit of resources such as CPU and RAM. If a container exceeds the limit of the RAM, the container will fall and if it exceeds the limit of the CPU, it will simply be slower.
</b></details>

<details>
<summary>Why do you use the "main" function in python?</summary><b>

`
if __name__ == '__main__':
`

Actually, when we run the code directly from the file where it is written, __name__ will be equal to __main__ and then the code will run as we wanted, but if we import this file into another file, the __name__ will be equal to the name of the file.
Why does it matter to anyone?
Because when we import a file in Python, Python runs the file we imported before our file and if we did not define the condition

`
if __name__ == '__main__':
`

The entire file is run, usually we don't want such a thing to happen, so we will define this condition and then when we do the import the __name__ will not be __main__ but it will be the name of the file for example my_file, then the condition will not be fulfilled and therefore everything inside the main function will not be run.
</b></details>

<details>
<summary>What is venv in Python?</summary><b>
venv is a kind of virtual environment that you can create for your project and there will be all the modules that your project needs, instead of you downloading each module for the whole system.
A use for this is that if a certain project needs a module version for example snir:1.6 and another module needs version snir:1.4, you can create a separation using a virtual environment.
</b></details>

<details>
<summary>What is the difference between list and tuple?</summary><b>
The difference in Python between list and tuple is that list is a mutable data type, meaning that it can be changed and tuple cannot, tuple is more efficient than list in terms of memory.
</b></details>

<details>
<summary>What is the difference between an interpreter and a compiler?</summary><b>
An interpreter takes the code and transfers it to machine language line by line, while a compiler takes the code and transfers it to machine language all at once,
A program that uses a compiler will run faster than one that uses an interpreter,
But it will be more difficult to debug it because it first scans the code, transfers it to machine language and only then returns an error, while software that uses an interpreter goes line by line and when it reaches an error it returns it.

An example of a language that uses an interpreter: Python

An example of a language that uses a compiler: node.js
</b></details>

<details>
<summary>What is git rebase?</summary><b>
git rebase is a command in git that serves us for roughly the same purpose as git merge but does it in a more orderly way, it takes the commits that happened in the feature branch and unites it with the commits of the master
</b></details>

<details>
<summary>What is the difference between API and REST API?</summary><b>
REST is a type of API, not every API is a REST API but every REST API is an API.
API is the way for applications to communicate with each other, for example in web development, the API is usually the way we receive information from a certain service, usually at a certain URL, with certain parameters and more information on how to make an API request from the service.
REST is a set of rules on how to build a web api, because there are many ways to build a web api, a set of rules agreed upon saves time deciding how to build it and also saves time understanding how to use it.
REST usually uses the HTTP protocol, PUT and GET headers in order to receive information or change information and the information will usually be returned in JSON format.
</b></details>

<details>
<summary>What is MARKUP LANGUAGE?</summary><b>
MARKUP LANGUAGE is a computer language used to describe information such as text, images or other visual information, it uses tags to describe it and the computer or browser knows how to display the information, an example of such a language is HTML, in HTML there are tags that help the browser know how to present the information to us.
</b></details>

<details>
<summary>What is Jinja2?</summary><b>
A templating engine in Python used to create HTML, XML or other MARKUP formats that are returned to the user in HTTP requests.
Comes with the Python web development library, Flask, and basically allows us to return HTML pages to the user when he goes to our web server written in Python.
Variables can be transferred from the code itself to the HTML pages, for example let's say we have an HTML page that contains the sentence Hi, snir and we would like to transfer the variable name=snir to be displayed on the HTML page, in the code of the HTML page we will edit it to: Hi, {{ name }}.
You can say that this is Python's way of transferring information between the backend and the frontend, a kind of bridge.
</b></details>

<details>
<summary>What is systemd?</summary><b>
It is a DAEMON in LINUX for managing the system, it manages starting and stopping services, logging for services, it is used with systemctl for example.
</b></details>

<details>
<summary>What is CDN?</summary><b>
content delivery network - a group of servers scattered around the world whose goal is to shorten latency as much as possible, for example if my servers are located in the US, someone in India will have high latency, cdn solves this problem.
</b></details>

<details>
<summary>What is DHCP How does DHCP work?</summary><b>
DHCP is a mechanism that distributes IP addresses to components in the network automatically, when a server joins the network it sends a request to the DHCP server to receive an IP address, the DHCP server returns an IP address to it and as long as the server is running the IP address belongs to it, as soon as the server is turned off its address returns to the dhcp pool and you can Divide it again.
</b></details>

<details>
<summary>blue-green deployment vs canary</summary><b>

When we want to deploy to a new version or for any change, we don't want to have any down time at all, blue-green deployment is a method to deploy where you have two versions of the application, one green and one blue.

The green one is the application that currently exists to which the load balancer transfers traffic and the blue one is the application that we want to deploy to, with this method we will divide the servers into 2 groups and the load balancer will only refer to half of the green application, at this time we will deploy the blue application to all the servers that the load balancer does not Refers to them and when we are done we can refer the load balancer to the blue version and the users will not feel it.

Canary deployment is another method of deployment where we will take a smaller part of the servers under the load balancer, say 5%, deploy to them and this way we can check if the deployment works without affecting 95% of the people, we will use this method mainly for tests and less in production.
</b></details>

<details>
<summary>What is the difference between terraform and ansible and when will we use each of them?</summary><b>
Both are (iac) tools that we can use to build our infrastructures with code. Thanks to the fact that tf is declarative, it has the option to see that a certain resource depends on another resource, let's say we want to create a db inside a k8s cluster, so even if we register the db first, it will first create the db in k8s because it depends on it, and only then will it create the db in k8s. In contrast, Ansible does not have this option and simply creates the resources from start to finish.
 tf also has a state feature that, after we have lifted the infrastructure with it, it knows what is in the air and what is not, and in contrast, Ansible does not have this feature as a default.
Usually it is better to pick up the infrastructure with tf and after that work on the infrastructure like making installations and all kinds of changes in the infrastructure itself with Ansible.
</b></details>
