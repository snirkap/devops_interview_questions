# devops interview questions
his repo contains questions and exercises on various technical topics, related to DevOps
## questions:

<details>
<summary>What is the difference between tcp and udp?</summary>
Both are communication protocols, tcp is a connection-based protocol, it establishes a connection before it starts sending information and after it is finished it closes, so it is more reliable but less fast than udp which is not connection-based.
</details>

<details>
<summary>What is a context switch?</summary>
An operation of the processor that allows processes to run concurrently, the processor takes a sort of snapshot of the current state of the registers in memory, keeps it aside and moves on to work on another process.
Because the operation is performed at high speed, it appears as if the processor is running the processes in parallel.
</details>

<details>
<summary>What is a deadlock?</summary>
A deadlock is a situation in which one process tries to access a certain resource that a second process uses while the second process tries to access a resource that the first process uses and a situation is created where no one can progress.
</details>

<details>
<summary>What is the difference between process and thread?</summary>
process is basically software that runs on the processor with resources defined for Process such as cpu, memory and ip, it does not share these resources with other Processes.
A thread, on the other hand, is part of a process, a process can have several threads running at the same time that will share its resources.
</details>

<details>
<summary>What is the difference between deployment and statefulset?</summary>

deployment is intended for applications that are stateless such as web servers such as nginx and apache that do not need permanent storage while statefulset is more suitable for applications that are stateful such as DBs.

In terms of deployment, the pods can be replaced all the time while sts keeps a unique ID for each pod it manages and uses this ID when it needs to reschedule these pods.
Each pod in sts has its own DNS name that does not change, if the pod dies the IP can change but its DNS name will remain the same, this is realized by headless service, the DNS names include the serial number of the pod.

Each replica in sts has its own state, with pvc for each pod, for example sts with 4 replicas, will create 4 pods where each pod has its own volume and its own pvc.
In deployment the pods share volume and pvc while in sts each pod has its own volume and pvc.
</details>

<details>
<summary>Why are containers better than VMs?</summary>

Containers have already become the standard in the market, they replace VMs mainly because they provide better utilization of resources because they share the same operating system with other containers.
Virtual machines are more resource optimization at the infrastructure level, instead of needing a server for each application you can set up several virtual servers on the same hardware, the servers will be completely isolated from each other, each will have its own operating system and they can sit on the same iron even if their operating system different.

Because a container contains exactly what it needs to run, it takes less time to upload and download a container because the weight of its image is usually measured in megabytes than to upload and download a machine whose image weight will usually be several gigabytes, in addition you can run several containers on the same vm so you can run multiple applications on the same machine.
</details>

<details>
<summary>What is affinity and anti-affinity in k8s?</summary>

Affinity - chooses where to put the pod according to the labels of the node.

Anti-affinity - prevents the pods from being scheduled on the same node or close to each other, and ensures separation. Helps in distributing loads over different nodes
</details>
