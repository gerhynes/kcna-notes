# KCNA Notes
Sources:
- [CNCF Kubernetes and Cloud Native Associate Certification Course](https://youtu.be/AplluksKvzI)

The CNCF Kubernetes and Cloud Native Associate (KCNA) is the entry-level CNCF certification teaching:

- The landscape of Cloud Native technologies
- A close look at the core Kubernetes components
- A quick look at the vast amount of CNCF projects and cloud-native tooling
- A general overview of Security, Deployment, and Monitoring
- The structure and governance of the CNCF, and the community around Cloud Native

The exam is more engineer-focused than other entry-level cloud certificates.

Prerequisites include:
- Linux knowledge
- Networking knowledge
- Any associate level cloud certification

The exam covers 5 domains:
- 46% Kubernetes Fundamentals 27-28 questions
- 22% Container Orchestration 25 questions
- 16% Container Native Architecture 25 questions
- 8% Cloud Native Observability 4-5 questions
- 8% Cloud Native Application Delivery 4-5 questions

The Linux Foundation (which includes the Cloud Native Computing Foundation) uses the PSI network of test centers and online proctored exams.

A passing grade is 750/1,000 or c.75%. There are 60 questions and no unscored questions. You can afford to get 15 questions wrong. There is no penalty for wrong questions. The questions are multiple choice and multiple answer.

The exam duration is 90 minutes. Seat time is 120 minutes, including showing an online proctor your workspace, reading and accepting an NDA, and providing feedback at the end.

The cert is valid for 36 months before recertification. You get two attempts to pass.

## Cloud Native Concepts
Cloud Native describes an architectural approach that emphasizes application workloads that are **portable, modular, and isolate** between different cloud deployment models and Cloud Service Providers (CSPs).

CSPs commonly describe Cloud Native as meaning everything built on the CSP. This is more accurately described as "Cloud First".

Some describe Cloud Native as having four key principles:
1. Microservices
2. Containerization
3. Continuous Delivery
4. DevOps

Cloud Native can also mean technologies like Kubernetes and CNCF projects that are both distributed and are agnostic to any CSP.

The CNCF defines Cloud Native as:

> Cloud Native technologies empower organizations to build and run scalable applications in modern, dynamic environments, such as public, private, and hybrid clouds. Containers, services, meshes, microservices, immutable infrastructure, and declarative APIs exemplify this approach.
> 
> These techniques enable loosely coupled systems that are resilient, manageable and observable.
> 
> Combined with robust automation, they allow engineers to make high impact changes, frequently and predicatbly with minimal toll.
> 
> The Cloud Native Computing Foundation seeks to drive adoption of this paradigm by fostering and sustaining an ecosystem of open source, vendor neutral products.
> 
> We democratize state-of-the-art patterns to make these innovations accessible for everyone.

### Cloud Native vs Cloud Service Providers
A **Cloud Service Provider** (CSP) is:
- A collection of cloud services
- Strong application integration and synergies between services
- Utilizing metered billing
- Under a single unified API

Examples include: AWS, Azure, GCP, IBM Cloud.

**Cloud Native** is a workload, application or system that is designed to run on cloud services and "take advantage of cloud offerings".

Cloud Native workloads cannot take full advantage of CSPs because CSPs intentionally have proprietary technology to encourage you to use their managed services that have exclusive integrations with other services.

### The Linux Foundation
The **Linux Foundation** (LF) is a non-profit technology consortium founded in 2000 as a merger between Open Source Development Labs and the Free Standards Group to standardize Linux, support its growth, and promote its commercial adoption.

The Foundation is supported by a variety of technology companies from Google and Microsoft to AT&T and Qualcomm.

### Cloud Native Computing Foundation
The **Cloud Native Computing Foundation** (CNCF) is a Linux Foundation project founded in 2015 to help advance container technology.

CNCF operates an independent organization from its parent organization. It has its own board members, global tech conferences (CloudNativeCon and KubeCon), and its own certifications.

It also has its own collection of projects, including:
- Kubernetes
- Prometheus
- Etcd
- ContainerD

### Cloud Native Landscape
The [Cloud Native Landscape](https://landscape.cncf.io ) is an interactive map developed by the CNCF to showcase all available cloud native technologies and to help identify the category they serve. 

Categories include:
- App Definition and Development
- Orchestration and Management
- Runtime
- Provisioning
- Special (training and certification)
- Observability and Analysis

### Cloud Native Trail Map
The Cloud Native Trail Map is a recommended path to adopting Cloud Native architecture.

1. Containerization
2. Continuous Integration and Deployment CI/CD
3. Orchestration and Application Development
4. Observability and Analysis
5. Service Proxy, Discovery, and Mesh
6. Networking Policy and Security
7. Distributed Databases and Storage
8. Streaming and Messaging
9. Container Registry and Runtime
10. Software Distribution

The path order will vary based on your use case. All parts of the path will be trekked during adoption.

### VMs and Containers
A **Virtual Machine** (VM) will have a host OS and a Hypervisor, which allows you to run a guest OS with apps, databases, libraries, packages, and binaries. 

Virtual Machines allow you to run multiple workloads on a single machine so you are best utilizing that machine. The problem is that there is still wasted space since you have to provision a virtual machine to be a particular size.

**Containers** will run on a host OS and a Container Runtime. This can run multiple containers, each with its own isolated workload. Any remaining space is available to be used by another container.

Virtual Machines do not make the best use of space. Apps are not isolated which could cause config conflicts, security problems, or resource hogging.

Containers allow you to run multiple apps which are virtually isolated from each other. You can launch new containers and configure OS dependencies per container.

### Microservices
With **Monolithic Architecture**, one app is responsible for everything and functinality is tightly coupled.

With **Microservice Architecture**, multiple apps are each responsible for one thing and functionality is isolate and stateless.

### Kubernetes
**Kubernetes** (K8s) is an open-source container orchestration system for automating the deployment, scaling, and management of containers.

It was originally created by Google and is now maintained by the CNCF as a CNCF Project.

The advantage of Kubernetes over Docker is the ability to run contanerized apps distrbuted across multiple VMs.

A unique component of Kubernetes are pods. A pod is a group of one or more containers with shared storage, network resources, and other shared settings.

Kubernetes is ideal for microservice architecture where a company has tens to hundreds of services they need to manage.

### Kubernetes Components
**Cluster** - A logical grouping of all components 

**Namespace** - A named logical grouping of Kubernetes components within a cluster. Used to isolate different workloads on the same cluster.

**Node** - A virtual machine or serverless container. There are two types of nodes: Cotrol Plane  and Worker nodes. Worker nodes  are where your applcation or workload runs. Control Plane nodes manage Worker nodes.

**Pod** - The smallest unit in Kubernetes. It's an abstractin over a container and generally defines an application workload.

**Service** - A static IP address and DNS name for a set of pods (persists an address even if a pod dies), and a load balancer. (A "service" can also mean a container that continuously runs).

**Ingress** - Translates HTTP/S rules to point to services.

**API Server** - Allows users to interact with K8s components using kubectl or by sending HTTP/S requests.

**Kubelet** - An agent installed on all nodes. It allows users to interact with a node via the AP Serer and kubectl

**kubectl** - A  command line interface (CLI) that allows users to interact wth the cluster and compnents via the AP server.

**Cloud Controller Manager** - Allows you to link a Cloud Servce Provider to leverage cloud services.

**Controller Manager** - A control loop that watches the state of the cluster and will change the current state back to a desired state.

**Scheduler** - Determines where to place pods on nodes. Places them in a scheduling queue.

**Kube Proxy** - An application on worker nodes that provides routing and filtering rules for ingress (incoming) traffic to pods.

**Network Policy** - Acts as a virtual firewall at the namespace-level or pod-level.

**ConfigMap** - Allows you to decouple environment-specific configuration from your contaner images, so that your applications are easily portable. Used to store non-confidential data in key-value pairs.

**Secret** - Stores small amounts of sensitive data such as a password, token, or key.

**Volumes** - Used for mounting storage, either locally on the node or remotely to cloud storage

**StatefulSet** - Provides guarantees about the ordering and uniqueness of pods. Think of databases where you have to determine read and write order or limit the amount of containers. StatefulSets are hard. If you can, host your database externally from your K8s cluster instead, such as on RDS.

**ReplicaSets** - Maintain a stable set of pods running at a given time. This can provide a guarantee of availability.

**Deployment** - A blueprint for a pod. Think of it like an EC2 Launch Template.

### Manifest Files in Kubernetes
**Manifest** files in the context of Kubernetes are any Kubernetes Configuration file that defines the configuration of various K8s components.

These are all Manifets files with specific purposes:
- Deployment file
- PodSpec file
- Network Policy file

Manifest files can be written in either YAML (more common) or JSON (rare).

A Manifest can contain multiple K8s component definitions/configurations.

In YAML `---` is used to seperate multiple components.

The `kubectl apply` command is generally used to deploy manifest files.

```bash
kubectl apply -f resource.yaml
```

**Resource Configuration file** is sometimes used to describe multiple resources in a manifest.

### Control Plane and Worker Nodes
**Control Plane Node** (formerly Master Node) manages processes like scheduling and restarting nodes.

**Worker Node** does the work of running your app in pods of containers.

In the Control Plane Node:
- **API Server** is the backbone of communication in a cluster.
- **Scheduler** determines where to start a pod on a worker node.
- **Controller Manager** detects state changes (if a pod crashes it restarts it)
- **etcd** is a key-value store that stores the state of the cluster.
- **Kubelet** allows users to interact with the node via kubectl
- Core DNS 

The Worker nodes runs:
- Kubelet
- Kube Proxy
- Container Runtime
- Pods and Containers

### Pods
**Pods** are the smallest unit in Kubernetes. They abstract away the container layer so you can directly interact with the Kubernetes layer.

A Pod is intended to run one application in multiple containers. 

A Pod could be:
- Database Service
- Job Service
- Frontend App Service
- Backend App Service

You can run multiple apps in a pod but those containers will be tightly dependent. 

Each pod gets its own private IP address:
- Containers will run on different ports
- Containers can talk to each other via localhost

Each pod can have a shared storage volume attached. All containers will share the same volume.

When the last remaining container dies (maybe crashes) in a pod, so does the pod. When a replacement pod is created, the pod will be assigned an IP address. IP addresses are ephemeral for pods, they don't persist by default.

To get pods and show their IP addresses, use:

```bash
kubectl get pods -o wide
```

### API Server
The core of a Kubernetes Control Plane is the **API Server**. The API Server exposes a HTTP API that lets end users, different parts of your cluster, and external components communicate with one another.

The Kubernetes API lets you query and manipulate the state of API objects in Kubernetes, such as pods, namespaces, ConfigMaps and events.

The API Server is the component of the Control Plane that exposes the Kubernetes API; it's the front end for the Control Plane.

The main implementation of the Kubernetes API server is kube-apiserver. kube-apiserver is designed to scale horizontally; it scales by deploying more instances.

You can run several instances of kube-apiserver and balance traffic between those instances.

**Everything has to go through the API Server**.

You can interact with the API Server via:
- UI
- API
- CLI (kubectl)

### Deployment
A **Deployment** provides delarative updates for Pods and ReplicaSets. It defines their desired state.

A Deployment Controller changes the actual state to the desired state at a controlled rate.

The default Deployment Controller can be swapped out for other deployment tools, such as Argo CD, Flux, Jenkins X.

A Deployment will create and manage a ReplicaSet. A ReplicaSet  will manage replicas of pods.

### ReplicaSets
**ReplicaSets** are a way to maintain a desired amount of redundant pods (replicas) to provide a guarantee of availability.

It is not recommended to directly create ReplicaSets. Instead, a Deployment can create and manage ReplcaSets for you.

Horizontal Pod Autoscaler (HPA) can be used to autoscale a ReplicaSet.

### Stateless vs Stateful
**Stateless**
- Every request doesn't care about previous or current state
- Web apps that store sessions outsde of themselves (database or cookies) are stateless
- You can send a request to any server. It doesn't matter
- ReplicaSets are stateless

**Stateful**
- Every request relies on state data. All databases are stateful
- Monolthic web apps that store session data in memory on a virtual machine are  stateful
- A read replica database needs to remember to send writes only to the primary database
- StatefulSets are stateful

### StatefulSets
**StatefulSets** are used when you need traffic to be sent to specific pods.

StatefulSets will always have:
- a unique and predictable name and address
- ordinal index number assigned to each pod
- a persistent volume attached, with a persistent link from the pod to the storage. If  a pod is rescheduled, the original persistent volume (PV) will be mounted to ensure data integrty and consistency
- StatefulSet pods will always start in the same order and terminate in reverse order

StatefulSets currently require a "headless" service to manage the identities. There is a headless service used to maintain the network identty of the pods, and another service that provides read access to the pods.

Writes will be directed to the main pod by its DNS Hostname, which is identified by a headless service.

Read traffic can be distributed to all reading pods using a ClusterIP Service.

The headless service is a service with ClusterIP set to none. It does not provide load balancing or a static IP address.  A headless service is used to identify specific pods by assigning them a DNS record.

Each pod has its own volume. A Persistent Volume Claim can dynamically reference a Persistent Volume.

### Namespaces
A **Namespace** is a way to logically isolate resources within a Kubernetes Cluster. Namespaces can be organized based on a projet, department, or any user-defned grouping.

To view all namespaces, use:

```bash
kubectl get namespace
```

Kubernetes starts 4 initial namespaces.
1. **default** - The default namespace where all pods and services run unless a namespace is specified.
2. **kube-public** - For resources that are publicly visible and readable
3. **kube-system** - The system namespace that stores objects created by the Kubernetes system. Engineers deploying applications are not supposed to touch this namespace
4. **kube-node-lease** - Holds lease objects associated with each node. Used to detect node failures by sending heartbeats.

You can create your own namespaces with:

```bash
kubectl create namespace namespace_name
```

In clusters with a small amount of resources, namespaces aren't necessary.

Names of resources need to be unique within a namespace but not across namespaces. Namespace-based scoping is applicable only for namespaced objects, such as Deployments or Services, not for cluster-wide objects, such as StorageClass, Nodes, PersistentVolumes.

**Single-Namespace Objects** - **ConfigMaps** and **Secrets** can't be shared across namespaces.

**Multi-Namespace Objects** - **Services** and **Pods** can belong to multiple namespaces.

**Cluster-wide Objects** - **Volumes** and **Nodes** cannot be bound to namespaces since they are global.

You can apply system quota restrictions on a namespace to avoid overuse, such as memory or compute.

If you don't provide a namespace for a component, it will end up in the default namespace.

### In-Tree vs Out-of-Tree
In Cloud Native projects, you'll hear the term In-Tree and Out-of-Tree.

**In-Tree**
- Plugins, components, or functionality that are provided by default and/or reside in the main repository.
- Think of In-Tree as internal plugins

**Out-of-Tree**
- Plugins, components, or functionality that must be installed manually, and extends or replaces the default behaviour.
- Think of Out-of-Tree as external plugins

### Endpoints and Endpoint Slices
**Endpoints** track the IP addresses of the pods assigned to a Kubernetes Service.

When a service selector matches a pod label, the pod IP address is added to the pool of endpoints. Pods expose themselves to services via endpoints.

To see a list of endpoints, use

```bash
kubectl get endpoints
```

**Endpoint Slices** break up Endpoints into smaller manageable segments. Each Endpoint Slice has a limit of 100 pods.

### Jobs and CronJobs
A **Background Job** is a one-off task used to run a piece of code. They are commonly used to perform maintenance or to trigger a computational workload, such as backing up a database every X minutes or deleting all users who have not confirmed their email.

A **Job** creates one or more pods and will continue to retry execution of the pods until a specified number of them sucessfully terminate.

```bash
kubectl create job hello --image=busybox -- echo "Hello World"
```

A **CronJob** is a job that executes based on a repeating schedule.

```bash
kubectl create cronjob gello --image=busybox --schedule="*/1 * * * *" -- echo "Hello World"
```

### Kubernetes Dashboard
**Kubernetes Dashboard** is an open-source application you can deploy to your cluster to provide a UI to view Kubernetes components.

## Selectors
**Selectors** are a way of selecting one or more Kubernetes objects.

In Kubernetes there are 3  types of selectors:
1. **Label Selector** - Selects Kubernetes objects based on the applied label, such as `env:prod`
2. **Field Selector** - Select Kubernetes objects based on object data, such as metadata, status
3. **Node Selector** - Select nodes for very specific pod placement 

Label Selectors define labels as a key-value pair under metadata in a manifest file.

You can use the `--show-labels` flag to see labels.

```bash
kubectl get pods --show-labels
```

You can apply labels with the `label` command.

```bash
kubectl label pods apache-web owner=devops
```

### Recommended Labels
Some labels are recommended to be applied to every resource object:
- **app.kubernetes.io/name** - The name of the application
- **app.kubernetes.io/instance** - A unique name identifying the instance of an application
- **app.kubernetes.io/version** - The current version of the application (semantic version, revision hash)
- **app.kubernetes.io/component** - The component within the architecture
- **app.kubernetes.io/part-of** - The name of a higher-level application this one is part of
- **app.kubernetes.io/managed-by** - The tool being used to manage the operation of an application
- **app.kubernetes.io/created-by** - The controller/user who created this resource

Shared labels and annotations share a common prefix: app.kubernetes.io 

Labels without a prefix are private to users.

### Selecting Labels
Kubernetes objects like Services and ReplicaSets will target pods based on **Label** selectors.

The selector syntax varies for different Kubernetes objects.

You can use selectors in kubectl with `--selector` or `-l`.

```bash
kubectl get pods --selector env=development
kubectl get pods -l env=development
```

### Annotations
Kubernetes **Annotations** allow you to attach arbitrary non-identifying metadata to objects. Clients, such as tools or libraries, can and may require this annotation in order to work.

For example, Ingress often use annotations to communicate to Ingress Controllers. To use the nginx Ingress Controller, you need to specify a rewrite/target path.

## Kubelet
### PodSpec File
**PodSpec** is a configuration file that describes a pod. It's `kind` will be `Pod`.

The `spec` section can define multiple containers including:
- The name of the container
- The image
- The command to run on startup
- The port the container will operate on
- The restart policy

You can directly deploy a pod with `kubectl apply` and the PodSpec.

```bash
kubectl apply -f nging.yaml
```

In practice, you won't directly deploy pods. Instead you'd use `Deployment` or `Job` as the `kind`.

### gRPC
**Remote Procedure Call** (RPC) is a framework of communication in distributed systems. It allows one program on a machine to communicate with another program on a remote machine without knowing that it's remote. The concept of RPC has been around since the 1970s.

**gRPC** is a modern open-source high performance RPC framework that can run in any environment. gRPC was initially created by Google.

You can think of gRPC as an alternate method of communication instead of REST or GraphQL.

gRPC can connect services in and across data centers with pluggable support for:
- load balancing
- tracing
- health checking
- authentication

gRPC works by:
- Installing a gRPC library for your program
- Defining a Protobuf (.proto) file that describes the data structure
- Writing code that works with gRPC

Distributed systems like Kubernetes use gRPC for pod communication.

### Kubelet
**Kubelet** is responsible for pod-internal API communication via the API Server.

Kubelet is a node agent that runs on every single node, both Control Plane and Workers.

An agent is a program installed on a server to observe what occurs for specific programs, and to communicate information externally or trigger actions to be performed.

Kubelet performs the following tasks:
- Watches for pod changes
- Configures the container runtime to 
	- Pull images
	- Create namespaces
	- Run containers

Kubelet uses PodSpec files to determine what images to pull and containers to run.

Kubelet will continuously monitor pods for any kind of changes.

Kubelet will send back HTTPS requests to the API Server, container logs and execution requests.

Kubelet can interact with storage through the Container Storage Interface (CSI) using gRPC.

Kubelet can interact with a Container Runtime Interface (CRI) also using gRPC.

## kubectl
**kubectl** is a command line tool that lets you control Kubernetes clusters.

kubectl looks for a file named `config` in the `$HOME/.kube` directory.

A kubectl command is structured `kubectl [COMMAND] [TYPE] [NAME] [FLAGS]`.

The command is the operation you want to perform, including:
- **annotation** - Key-value data that can be applied to resources
- **apply** - Executes manifest files to create or modify Kubernetes resources
- **auth** - Inspects if you are authorized to perform an action
- **autoscale** - Creates an autoscaler that automatically chooses and sets the number of pods that run in a cluster
- **cp** - Copy files and directories to and from containers
- **create** - Create specific cluster-level resources: ConfigMap, Deployment, Job, namespace, Role, Secret
- **delete** - Delete resources by filename, labels
- **describe** - Show details of a specific resource or group of resources
- **diff** - Diffs the online configuration with local config
- **edit** - Edit a resource from the default editor. Edit a deployed manifest file and apply the changes
- **exec** - Execute a command within a container
- **expose** - Expose a resource as a Kubernetes service
- **get** - Get the status of an existing Kubernetes resource
- **kustomize** - Print a set of API resources generated from instructions in a kustomization.yaml file
- **label** - Update labels on a resource
- **logs** - Print the logs for a container in a pod or specific resource
- **patch** - Update fields of a resource using strategic merge patch, JSON merge patch, or JSON patch
- **port-forward** - Forward one or more local ports to a pod
- **proxy** - Creates a proxy server between localhost and the Kubernetes API Server
- **run** - Create and run a container image in a pod
- **scale** - Set a new size for a Deployment, ReplicaSet, Replication Controller, or StatefulSet

The type is the resource type you want to command.

```bash
kubectl describe deployments
```

 Resource types can have abbreviations:
 - deployments -> deploy
 - persistentVolumes -> pv
 - pods -> po

```bash
kubectl describe deploy
```

There are 50+ resource types, including:
- ConfigMaps (cm)
- Endpoints (ep)
- Namespaces (ns)
- Nodes (no)
- PersistentVolumesClaims (pvc)
- PersistentVolumes (pv)
- Pods (po)
- Secrets
- Services (sv)
- Deployments (deploy)
- ReplicaSets (rs)
- CronJobs (cj)
- Jobs
- Events (ev)
- Ingresses (ing)
- NetworkPolicies (netpol)
- StorageClasses (sc)

The name specifies the name of the resource. Names are case sensitive.

```bash
kubectl get pods example-pod1 example-pod2
```

If the name is ommitted, details for all resources are displayed.

```bash
kubectl get pods
```

Flags specify optional flags. kubectl doesn't enforce the use of `=`.

```bash
kubectl create role my-role --verb=get,list,watch --resource rs.extensions
```

- Flags generally start with two hyphens, such as `--server`
- Sometimes flags have abbreviations, such as `-s`
- The available flags will vary based on the command
- Sometimes flags can be assigned values or do not expect a value

The [kubectl documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) shows examples of how to use all the kubectl commands.

## Distributions
### Minikube
**Minikube** sets up a local single-node Kubernetes cluster on macOs, Linux, or Windows for learning purposes.

Minikube is running a virtual machine running a control plane and work processes with Docker as the container layer.

- Supports the latest Kubernetes release
- Cross-platform
- Deploys as a VM, container, or on bare metal
- Supports multiple container runtimes
- Docker API endpoints for fast image pushes
- Advanced features such as LoadBalancer, filesystem mounts, and FeatureGates
- Addons for easily installed Kubernetes applications
- Supports common CI environments

### K3s and K3d
**K3s** is a lightweight tool designed to run production-level Kubernetes workloads for low-resourced and remotely-located IoT and Edge devices and bare metal.

Originally created by Rancher, it's a Sandbox CNCF project.

K3s does not use Kubelet, but runs Kubelet on the host machine and uses the host's scheduling mechanism to run containers.

K3s uses kube-proxy to proxy the network connections of the nodes, while Kubernetes uses kube-proxy to proxy the network connections of an individual container.

K3s can have a tighter security deployment than Kubernetes because of its small attack area.

**K3d** is a platform-agnostic, lightweight wrapper that runs K3s in a Docker container. 

It helps run and scale single or multi-node K3s clusters quickly without further setup while maintaining a high availability mode.

### Kind
Primarily designed to test Kubernetes, **Kind** (Kubernetes in Docker) helps you run Kubernetes clusters locally and in CI pipelines using Docker containers as "nodes".

It's an open-source CNCF-certified Kubernetes installer that supports highly-available multi-node clusters and builds Kubernetes release builds from its source.

### MicroK8s
MicroK8s is created by Canonical and installed using the Snap package manager.

```bash
sudo snap install microk8s --classic
```

It's a Kubernetes distribution designed to run fast, self-healing and highly-available clusters.

It's optimized for the quick and easy installation of single and multi-node clusters on multiple OSes, as long as they have Snap.

MicroK8s is modular in design. You start with nothing and can enable addons to quickly use exactly what you need and nothing more.

### Lightweight K8s Distribution Comparison
Minikube 
- Runs in a VM
- Intended for development purposes
- Very easy to use, very popular

Kind
- Designed to run anywhere containers run
- Intended for development purposes
- Faster startup time than Minikube since it's not spinning up a VM

K3s and K3d
- Can be used for production use cases
- Designed for embedded, edge devices, or limited resources

MicroK8s
- Needs Snap to install
- Modular, starts with nothing installed
- Restarts everything if there is a crash
- Well suited for self-hosted production use cases

### Managed Kubernetes Providers
Managed Kubernetes providers are Cloud Service Providers or platforms that abstract away the effort of setting up, maintaining a cluster. They can support autoscaling as well.

**Google Kubernetes Engine** (GKE)
- The easiest to use with the richest amount of features

**Amazon Elastic Kubernetes Service** (EKS)
- Difficult to use via the UI, powerful CLI tool
- Worth it for integrations with other AWS services

**Azure Kubernetes Service** (AKS)
- Fairly easy to use
- Unique service for debugging live containers

**IBM Cloud Kubernetes Service** 
- Easy to use, not as feature rich
- More expensive than any other CSP

**Oracle Container Engine for Kubernetes**
- Cost effective for a CSP
- Worst Ui, limited options

**DigitalOcean Kubernetes (DOKS)**
- Very easy to use
- Predictable spend
- Beautiful UI

**CIVO Kubernetes**
- Cloud platform specifically focused on Kubernetes
- Most cost effective
- Simple UI

### Management Layers
A management layer for running Kubernetes on other platforms or allows you to etend your control plane to multiple platforms.

**Weave Kubernetes Platform** (WKP) - All of Weave's open-source tools packaged as a platform so you can build out a GitOps-enabled cluster.

**Rafay** - Similar to OpenShift but with a larger focus on governance and GitOps-based management for any Kubernetes clusters running on anything.

**VMWare Tanzu** - Wherever vSphere runs, you can deploy and monitor Kubernetes clusters.

**Azure Arc** multi-cluster management - Governs compute such as Kubernetes from other CSPs, on-premise, or the edge.

**Google Anthos** multi-cluster management - GKE being extended to manage clusters deployed to VMs on other clouds or on-premise. It's focused on managing Kubernetes.

**Platform9** - Similar to RayFay but relies more on third-party tooling instead of trying to leverage native functionality from public cloud service providers.

**Red Hat OpenShift** - Platform as a Service for Kubernetes. 
- Kubernetes with a commercial platform by Red Hat built on top
- kubectl is extended with additional functionality with the oc CLI
- Quickly deploy local code to a remote OpenShift cluster via odo
- Quality Assurance pipeline built into the platform
- Fixes critical bugs earlier instead of waiting for the next Kubernetes release
- Uses Red Hat CoreOS (an OS optimized for running containers)
- OperatorsHub, an automated installation tool (one click marketplace)
- GUI developer console
- CodeReady workspaces, cloud developer environment for Kubernetes

**Rancher Kubernetes Engine** (RKE)
- Runs entirely within Docker containers
- Works on bare metal and virtualized servers
- Solves the problem of instalation complexity, a common issue in the Kubernetes community
- Installation and operation of Kubernetes is both simplified and easily automated
- Entirely independent of the OS and platform you're running
- As long as you can run a supported version of Docker, you can deploy and run Kubernetes with RKE

## Runtimes
### Container Runtime Interfaces
**Orchestration Systems** (Docker or Kubernetes) will use a container runtime interface.

**Container Runtime Interfaces** (such as containerd or CRI-O) allow you to run a variety of different container runtimes, which push and pull images, and supervise containers.

**Open Container Initiative (OCI) Runtimes** create and run containers. The major difference between native and virtualized runtimes is isolation. Virtualized runtimes can provide security benefits through isolation.

Native Runtimes
- runC
- Crun

Sandboxed/Virtualized Runtimes
- gviso
- Nabla Containers
- Kata Containers

### containerd
**containerd** is an industry-standard container runtime with an emphasis on simplicity, robustness and portability.

Docker extracted their container runtime and donated it to the CNCF. This includes Docker's functionality for executing containers, handling low-level storage, and managing image transfers.

containerd makes it easier for projects like Kubernetes to access the low-level "Docker" elements they need, instead of actually using Docker.

Images you build with Docker aren't really "Docker images". Docker now uses the containerd runtime. Your images are built in the standardized Open Container Initiative (OCI) format.

### CRI-O
**CRI-O** is an implementation of the Kubernetes CRI (Container Runtime Interface) to enable using OCI (Open Container Initiative) compatible runtimes.

It's a kightweight alternative to using Docker (containerd) as the runtime for Kubernetes.

It allows Kubernetes to use any OCI-compliant runtime as the container runtime for running pods. It supports runC and Kata Containers as the container runtimes, but any OCI-conformant runtime can be plugged in in principle.

### Container Runtimes
Virtualized Runtimes use lightweight VMs with individual kernels for isolation.

Native Runtimes use namespaces andcgroups in shared kernels for isolation.

runC is a low-level container runtime that creates and runs containers. runC would be used alongside containerd or CRI-O.

So containerd is a daemon process that manages and runs containers. It pushes and pulls images, and manages storage and networking. It supervises the running of containers.

runC creates and runs containers.

### Control Groups (cgroups)
A process is an instance of a running program on Linux.

**Control Groups** (cgroups) allow you to group processes to apply different kinds of limitations:

- **Resource limiting** - groups can be set to not exceed a configured memory limit, which includes the filesystem cache
- **Prioritization** - some groups may get a larger share of CPU utilization or disk I/O throughput
- **Accounting** - measures a group's resource usage, which might be used for billing purposes
- **Control** - freezing groups of processes, their checkpointing and restarting

Think of cgroups as a way to limit programs on Linux from overusing CPU, memory, or storage.

The primary design goal for cgroups was to provide a unified interface to manage processes or whole operating-system-level virtualization, including Linux Containers (LXC).

### Linux Containers
**Linux Containers** (LXC) is an OS-level virtualization technology that allows for the creation and running of multiple isolated Linux virtual environments (VEs) on a single control host.

#### VEs vs VMs
- With VEs there is no pre-loaded emulation manager software as in a VM
- In a VE, the application (or OS) is spawned in a container and runs with no added overhead, except for a usually miniscule VE initialization process
- There is no hardware emulation, which means that aside from the small memory software penalty LXC will boast bare metal performance characteristics because it only packages the needed application
- VEs cannot be easily managed via a GUI management console and don't offer some other features of VMs, such as IaaS setups and live migrations.

## Storage
### Container Storage Interface (CSI)
**Container Storage Interfaces** (CSI) standardize how Container Orchestration Systems access various storage providers.

Container Orchestration Systems could be Mesos, Kubernetes, Docker Swarm.

Storage Providers include: Azure Disk, AWS EBS, NetApp Trident, OpenStack Cinder, and Google CLoud Storage.

### Kubernetes Backing Store and etcd
Components of a Kubernetes cluster (pods, nodes, control plane, volumes) need a level of protection in case of disaster.

Kubernetes resources's state is stored in etcd, but could also be backed by a database such as MariaDB.

**etcd** is a strongly consistent, distributed key-value store that provides a reliable way to store data that needs to be accessed by a distributed syste, or cluster of machines.

etcd resides in the Control Plane node. It is used by CoreDNs and Rook, as well as the Kubernetes cluster.

### Rook and MinIO
**Rook** turns distributed storage systems into self-managing, self-scaling, self-healing storage services.

It automates the tasks of a storage administrator: deployment, bootstrapping, configuration, provisioning, scaling, upgrading, migration, disaster recovery, monitoring, and resource management.

**MinIO** offers high-performance S3-compatible object storage.

Native to Kubernets, MinIO is the only object storage suite available on every public cloud, every Kubernetes distribution, the private cloud, and the edge.

It is software-defined and open source under GNU AGPL v3.

### Volumes
Kubernetes supports many types of volumes and a pod can use any number of volme types simultaneously.

**Persistent Volumes**
- Attaching external storage to a pod
- The data will persist even if the pod is terminated

**Ephemeral Volumes**
- A volume that only exists as long as the pod exists
- Intended for temporary data storage

**Projected Volumes**
- maps several existing volume sources into the same directory

**Volume Snapshot**
- Archives a volume configuration and its data for rollbacks or backup

Types of volumes supported, include:
- AWS ElasticBlockStore
- Azure DIsk
- Azure File
- cephfs
- cinder
- configMap
- downwardAPI
- emptyDir
- fc (fibre channel)
- Google Cloud Persistent Disk
- glusterfs
- hostPath
- iscsi
- local
- nfs
- persistentVolumeClaim
- portworxVolume
- projected
- rbd
- secret
- vsphereVolume

### Persistent Volumes (PV)
A **Persistent Volume** is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes.

A Persistent Volume is similar to a node in that it's a cluster resource. It doesn't reside within a node or pod.

PVs are volume plugins like Volumes but have a lifecycle independent of any individual pod that uses the PV.

The API object captures the details of the implementation of the storage, whether that's NFS, iSCSI, or a cloud-provider-specific storage system.

Mounting PVs directly to a pod is not allowed and is against Kubernetes' design principles. It would cause tight coupling between the pod volume and the underlying storage. Persistent Volume Claims ensure decoupling.

### Storage Classes
A **Storage Class** is a way of defining a class of storage that is backed by a provisioner.

A Storage Class can be used by several Persistent Volumes.

Storage Class contains:
- Provisioner - who is providing the storage, such as Amazon EBS
- Parameters - what type of storage to use
- reclaimPolicy - if the pod is gone, does the volume remain

### Persistent Volume Claim (PVC)
A **Persistent Volume Claim** (PVC) is used to decouple Persistent Volumes from pods.

A PVC asks for a particular type of storage and if a PV that meets the criteria is matched, the PV is claimed and bound.

PVCs are similar to a pod requesting resources from a node. Pods consume node resources. PVCs consume PV resources.

Pods can request specific levels of resources (CPU and memory). PVCs can request specific size and access modes, such as ReadWriteOnce, ReadOnlyMany, ReadWriteMany.

### ConfigMaps
A **ConfigMap** is an API object used to store non-confidential data in key-value pairs for pods.

Pods can consume ConfigMaps as:
- environment variables
- command line arguments
- configuration files in a volume

A ConfigMap allows you to decouple environment-speciific configuration from your container images, so that your applications are easily portable.

A ConfigMap can be used by more than one pod.

## Services
Kubernetes **Services** allow you to attach a static IP address and DNS name for a set of pods. This allows you to persist an address for a pod even if it dies. 

Services also act as load balancers.

A pod without a service will have a dynamic IP address so when the pod dies so does the IP address.

Kubernetes Services have the following service types:
- **ClusterIP** - default, randomly forwards traffic to any pod set with the target port
- **Headless** - sends traffic to a specfic pod, when you have stateful pods, such as a database
- **NodePort** - external service, allows you to use a worker node IP address
- **LoadBalancer** - similar to NodePort except it leverages the Cloud Service Provider's load balancer
- **ExternalName** - a special service that does not have selectors and uses DNS names instead

### Traffic Policies
Kubernetes Services allow you to set a **Traffic Policy** to determine how ingress traffic is routed.

There are two types of traffic policy:
1. **External Traffic Policy** - how traffic from external sources is routed
2. **Internal Traffic Policy** - how traffic from internal sources is routed

Both policies have two valid values:
- Cluster - route external traffic to all ready endpoints
- Local - only route to ready node-local endpoints

If the traffic policy is local and there are no node-local endpoints, then kube-proxy does not forward any traffic for the relevant Service.

### ClusterIP
A **ClusterIP** is the default service type for a Kubernetes service. If you omit the type for a service, it will default to ClusterIP.

It's used for internal traffic. External traffic will not reach the service. Traffic will be randomly distributed to any targeted pods.

Traffic originating from within the cluster will pass through the node's Kubernetes Proxy and then onto the Kubernetes service.

A service can span multiple worker nodes for cross-node pods.

You would use ClusterIP for:
- Debugging
- Testing
- Internal Traffic
- Internal Dashboards

### NodePort
A **NodePort** allows you to expose a port for a VM (node) running pods that the service is managing. With a NodePort, external traffic can reach the pods.

In the manifest file, `type` is set to `NodePort` and as well as `port` and `targetPort`, there is a `nodePort` value for the port you're exposing the node on. 

- port - exposes the Kubernetes service on the specified port within the cluster. Other pods within the cluster can communicate with this service on the specified port
- targetPort - the port the service will send requests to and your pod will be listening on. Your application in the container will need to be listening on this port also
- nodePort - exposes a service externally to the cluster by means of the target node's IP address and the NodePort. NodePort is the default setting if the port field is not specified

There is no external load balancer, so a NodePort is intended for a single Kubernetes service and for non-production workloads.

### LoadBalancer
A **LoadBalancer** service type allows you to use an external load balancer, which handles the routing and traffic distribution logic.

The external load balancer could be from a managed third-party cloud service, such as AWS Network Load Balancer.

The LoadBalancer service type isn't well-suited for production workloads. Generally it's recommended to use Kubernetes Ingress. 

### Headless
A **Headless** service is a service with no ClusterIP address. It does not provide load balancing or proxying. `clusterIP` wil be set to `None` in the manifest.

Headless services are useful when dealing with a stategul application (reads and writes) and you need writes to go to a specific pod.

Headless services are needed to manage the network identity of the stateful pods by assigning a DNS record to each pod so you can route traffic to a DNS hostname.

### ExternalName
**ExternalName** services are the same as ClusterIP services with the exception that instead of returning a static IP, it returns a CNAME record.

A CNAME (canonical name) record is a DNS record that maps one domain name (an alias) to another name (a canonical name).

### `kubectl expose` Command
`kubectl expose` is used to quickly create Kubernetes services for a deployment.

```bash
kubectl expose deployment my-app --type=NodePort \
--name=my-service --port=80 --targetPort=8080 --nodeport=3000
```

### BusyBox
**BusyBox** combines tiny versions of many common Unix utilities into a single small executable. It's a Swiss army knife of embedded Linux as the single executable replaces the basic functions of more than 300 common commands.

BusyBox can be used to interactively debug services to ensure they're working.

```bash
kubectl run -it --rm --restart=Never busybox --image=gcr.io/google-containers/busybox sh
```

## Networking
### Ingress
**Ingress** exposes HTTP/S routes from outside the cluster to services within the cluster. Traffic routing is controlled by rules defined on the Ingress resource.

Ingress lets you translate a custom domain on SSL to a service running within your Kubernetes cluster.

In order for Ingress to work, you need to use an **Ingress Controller**, such as AWS, GCE, Nginx.

Ingress enables you to consolidate the traffic-routing rules into a single resource and runs as part of a Kubernetes cluster.

### CoreDNS
**Domain Name System** (DNS) is a service responsible for translating (or resolving) a service name to its IP address.

**CoreDNS** is the default DNS server for Kubernetes and ensures pods and services have Fully Qualified Domain Names (FQDN). Without CoreDNS, the cluster's communication would cease to work.

A FQDN is a domain name that specifies its exact location in the tree hierarchy, also known as an absolute domain.

CoreDNS has 

in-tree (internal) plugins, including:
- acl - enforces access control policies on source IP and prevents unauthorized access to DNS servers
- any - gives a minimal response to ANY
- azure - enables serving zone data from Microsoft Azure DNS service
- cache - enables a frontend cache
- health - enables a healthcheck endpoint
- log - enables query logging to standard output

out-of-tree (external) plugins, including:
- git - pulls git repositories
- alias - replaces zones apex CNAMEs
- redisc - enables a networked cache using Redis
- Kubernetai - serves multiple Kubernetes within a server

CoreDNS pods are extracted by a service object called kube-dns.

```bash
kubectl get service kube-dns -n kube-system
```

CoreDNS lives in the Control Plane node.

Each pod (not just CoreDNS pods) has a `resolv.conf` file to help with DNS resolving.

```bash
kubectl exec -it my-pod -- sh
car /etc/resolv.conf
# nameserver 10.100.0.10
# search default.svc.cluster.local svc.cluster.local cluster.local ec2.internal
# options ndots:5
```

`nslookup` can be used to see where things are resolved with CoreDNS.

```bash
nslookup my-service-name
# Server:    10.100.0.10
# Address:   10.100.0.10#53
# Name:      kubernetes.default.svc.cluster.local
# Address:   10.100.0.1
```

### Load Balancing
**Load Balancing** is a network component where traffic flows through the load balancer and the load balancer decides how to distribute the traffic to multiple targets (computer nodes) based on a set of rules.

Ingress and Service both have load balancing.

There are multiple levels of load balancing, from external load balancers, controlled by a third-party service, to Ingress to Service to internal load balancing with iptables / ipvs.

### Probes
**Probes** are used to detect the state of a container.

**Liveness Probe** - kubelet uses liveness probes to know when to restart a container. For example, liveness probes could catch a deadlock, where an application is running but unable to make progress. Restarting a container in such a state can help to make the application more available despite bugs.

**Readiness Probe** - kubelet uses readiness probes to know when a container is ready to start accepting traffic. A pod is considered ready when all of its containers are ready. One use of this signal is to control which pods are used as backends for services.

**Startup Probe** - kubelet uses startup probes to know when a container application has started. If such a probe is configured, it disables liveness and readiness checks until it succeeds, making sure those probes don't interfere with the application startup. This can be used to adapt liveness checks on slow-starting containers, preventing them from getting killed by kubelet before they are up and running.

### Netfilter
**Netfilter** is a project that enables:
- packet filtering
- network address and port translation (NAPT)
- translation packet logging
- userspace packet queueing
- other packet mangling

The Netfilter hooks are a framework inside the Linux kernel that allows kernel modules to register callback functions at different locations of the Linux network stack.

The registered callback function is then called back for every packet that traverses the respective hook within the Linux network stack.

Projects built on top of Netfilter:
- IPTables - generic firewalling software that allows you to define rulesets
- Nftables - successor to IPTables, more flexible, scalable and performant packet classification
- IPVS - specfically designed for load balancing, uses hash tables

### IPTables
Modern operating systems segregate virtual memory into kernel space and user space. Kernel space is reserved for running a privileged operating system kernel, kernel extensions, and device drivers. User space is the memory area where application software and some drivers execute.

**IPTables** is a userspace utility program that allows a system administrator to configure the IP packet filter rules of the Linux kernel firewall. iptables applies to IPv4, while ip6tables  applies to IPv6.

iptables are essentially virtual firewalls on Linux. It's common to set and modify iptables to restrict access based on ports and protocols:

```bash
iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT
```

### IPVS
**IP Virtual Server** (IPVS) uses the NetFilter framework. It also incorporates  LVS (Linux Virtual Server).

IPTables struggles to scale to tens of thousands of services as it is bottlenecked at 5000 nodes per cluster.

IPVS is specifically designed forload balancing and uses more efficient datastructures (hash tables) allowing for almost unlimited scale under the hood.

In the future Kube Proxy will default to IPVS.

### Various Proxies
A **Proxy** is a server application that acts as an intermediary between a client requesting a resource and the server providing that resource.

There are several kinds of proxies in Kubernetes:
- **kubectl proxy** - proxies from a localhost address to the Kubernetes API Server
- **API Server proxy** - a bastion built into the API Server, connects a user outside of the cluster to ClusterIPs which might otherwise not be reachable
- **kube-proxy** - runs on each node and used to reach services
- **Proxy/Load Balancer** in front of API Servers - acts as a load balancer if there are several API Servers
- **Cloud Load Balancers** - for external traffic to reach pods in cluster

A **Forward Proxy** is when a number of servers egressing traffic have to pass through the proxy first.

A **Reverse Proxy** is when ingress traffic is trying to reach a colection of servers and must pass through a proxy.

### kube-proxy
**kube-proxy** is a network proxy that runs on each node in your cluster. It's designed to load balance traffic to pods.

kube-proxy maintains network rules on nodes. These network rules allow network communication to your pods from network sessions inside or outside of your cluster.

kube-proxy can run in three modes:
1. iptables (current default) - suited for simple use cases
2. IPVS - scales to 1000+ services
3. Userspace (legacy) - not recommended for use

### Container Networking Interface
The **Container Networking Interface** (CNI) is a specification (open standard) for writing plugins to configure networking interfaces for Linux containers.

The interface allows containers to use both built-in plugins (such as loopback, bridge, ipvlan, dhcp, flannel) and third-party plugins (Calico, Ciliu, Weave).

### Service Mesh
A **Service Mesh** manages service to service comunication for microservice architectures. A service here meaning an application, not a Kubernetes service.

A service mesh is an infrastructure layer that can provide the following:
- Reliability - traffic management, retries, load balancing
- Observability - metrics, traces
- Security - TLS certifications, identity

The Service Mesh Control Plane handles the installation of the proxies into pods, as well as the proxies' capabilities.

Service meshes use a **sidecar pattern**. A proxy container is installed on each pod. Application containers must pass through the proxy before egressing the pod.

You don't have to run a service mesh but in most production use cases it's recommended to do so.

**Envoy** is an open-source edge and service proxy. Multiple service meshes use Envoy as its proxy. Envoy is a graduated CNCF project.

Available service meshes for Kubernetes include:
- **Istio** - currently the most popular service mesh for Kubernetes due to its highly configurable nature. Istio uses envoy as its proxy. Istio is not a CNCF project
- **Kuma** - a CNCF sandbox project that uses Envoy as its proxy
- **Linkerd** - a CNCF-graduated project known for having strong security and "just working". Linkerd does not use Envoy. Instead it uses a simple and ultralight "micro-proxy" called Linkerd2-proxy
- Consul - an open-source service mesh by Hashicorp, offered as a managed cloud service mesh. It's not a CNCF project.

### Envoy
**Envoy** is a self-contained process designed to run alongside every application server. It can be installed on a VM or as a container.

Envoy supports a wide range of functionality:
- L3/L4 filter architecture
- HTTP L7 architecture
- First class HTTP/2 support
- HTTP/3 support
- HTTP L7 routing
- gRPC support
- Service discovery and dynamic configuration
- Health checking
- Advanced load balancing
- Front/edge proxy support
- Best in class observability

In practice, you would not install and manually configure Envoy. You would allow a service mesh control plane to install it into your pods. A service mesh may come with a UI or configuration files to configure your Envoy.

## Cluster Networking
### Network Address Translation (NAT)
Network Address Translation (NAT) is a method of mapping one IP address space into another by modifying network address information in the IP header of packets while they are in transit across a traffic routing device.

For example, this might be necessary if you are communicating with two private networks that might have conflicting addresses.

### Eth0 and Network Namespace
An **Ethernet Device** is a software and/or hardware technology that allows a server to communicate on a computer network. A Network Interface Card (NIC) is commonly used to establish a wired connection to a network.

Cloud service providers have virtual NICs for your VMs to connect to the virtual network.

**eth0** represents the first ethernet interface attached to your VM.

A **Network Interface** is an abstraction on top of the ethernet interface to provide a logical networking stack with its own routes, firewall rules, and network devices.

Linux by default has one network namespace, called Root Network Space, and this is what programs will use by default.

Use the `ifconfig` command to observe network devices attached to a Linux VM.

Use the `ip netns` command to create, modify, or view network namespaces.

```bash
sudo ip netns add nsl
```

### Cluster Networking
Kubernetes has the following opinions about cluster networking:
- all pods can communicate with all other pods without using NAT
- all nodes can communicate with all pods without using NAT
- the IP that a pod sees itself as is the same IP that others see it as

NATs can stil be used in Kubernetes.

There are 4 broad types of network communication for clusters:
1. Container-to-Container
2. Pod-to-Pod
3. Pod-to-Service
4. External-to-Service

The talk [Life of a Packet](https://youtu.be/0Omvgd7Hg1I) by Michael Rubin is a god resource for Cluster Networking.

### Container to Container Networking
All containers in the same pod have the same IP address and port space. Containers can communicate with each other via localhost on different ports.

Within the manifest file, the `containerPort` value is used to define the local port for the container.

### Virtual Ethernet Devices (Veths)
**Virtual Ethernet Devices** can act as a tunnel between network namespaces to create a bridge to a physical network device in another namespace, but can also be used as standalone network devices.

Packets on one device in the pair are immediately received on the other device. veth devices are always created in interconnected pairs.

Use the `ip link` command to create veth pairs.

```bash
ip link add <p1-name> netns <p1-ns> type veth peer <p2-name> netns <p2-ns>
```

### Pod to Pod Networking
For Pod to Pod communication on the same node, Veth is used to communicate from the Pod Network Namespace to the Root Network Namespace.

In the Root Network Namespace a **bridge** is used to allow all Pod Network Namespaces to talk to other pods.

Pods can see all other pods, and communicate using their IP addresses.

Routing allows multiple networks to communicate independently and yet remain seperate using a router.

Bridging connects two seperate networks as if they were a single network using a bridge.

Pods can communicate to other pods running on other worker nodes. How pods can  communicate with pods on other nodes is network specific and will vary. 

In the case of AWS, they have their own implementation of the Container Networking Interface (CNI), Amazon VPC Container Network Interface plugin for Kubernetes managed node to node communication leveraging AWS Virtual Private Cloud.

### Pod to Service Networking
When a pod dies, its IP address changes and this can make communication hard if you are relying on the IP address for communication.

A service creates a virtualized static IP and then uses iptables, which is installed on the node, to perform Network Address Translation (NAT) and load balancing to other pods. 

### Ingress Egress Internet to Cluster
**Egress** is how pod traffic exits to the internet. This will be network specific.

In the case of AWS, pods use the Amazon VPC Container Network Interface (CNI)  plugin to be able to talk to your virtual private cloud and then egress out to the Internet Gateway (IGW) via route tables.

**Ingress** is how external traffic reaches a pod. It travels to a service. From there, a service could be using:
- Kubernetes Service wth type Load Balancer - This will work with a Cloud Controller Manager to implement a solution that works with a T4 (UDP/TCP) Load Balancer
- Kubernetes Ingress - This will use an Ingress Controller to work with a Cloud Service Provider load balancer

## Security
### 4Cs of Cloud Native Security
The 4 Cs of Cloud Native security are Cloud, Clusters, Containers, and Code. Each layer of the model builds on the next outermost layer.

This is Defense in Depth, a series of defensive mechanisms layered in order to protect valuable data and information.

### Cloud Layer
The Cloud Layer is also known as the base layer. Security at this layer is going to vary based on managed or self-managed infrastructure.

**Managed Infrastructure (IaaS)**
- Cloud Service Providers
- Cloud Platforms, such as CIVO

Security will vary greatly based on provider and independent research will need to be undertaken. For example, AWS's managed Kubernetes offering is EKS. You would need to research EKS security.

**Self-Managed**
- Co-located Servers, such as Equinix
- Corporate Datacenters

Security is going to be based on infrastructure security.
- Network access to API Server (Control Plane)
- Network access to nodes
- Kubernetes access to Cloud Provider API
- Access to etcd
- etcd encryption

### Cluster Layer
There are two parts to Cluster Layer security.

1 **Components of the Cluster** - Securing configurable cluster components
- Controlling access to the Kubernetes API
	- Using Transport Layer Security (TLS) for all API traffic
	- API authentication
	- API authorization
- Controlling access to the Kubelet
- Controlling the capabilities of a workload or user at runtime
	- Limiting resource usage on a cluster
	- Controlling what privileges containers run with
	- Preventing containers from loading unwanted kernel modules
	- Restricting network access
	- Restricting cloud metadata API access
	- Controlling which nodes pods may access
- Protecting cluster components from compromise
	- Restrict access to etcd
	- Enable audit logging
	- Restrict access to alpha or beta features
	- Rotate infrastructure credentials frequently
	- Review third-party integrations before enabling them
	- Encrypt secrets at rest
	- Set up alerts for security updates and vulnerabilities

2 **Components in the Cluster** - Securing the applications running within the cluster
- RBAC Authorization (access to the Kubernetes API)
- Authentication
- Application secrets management (and encrypting them in etcd at rest)
- Ensuring that pods meet defined Pod Security Standards
- Quality of Service (and customer resource management)
- Network policies
- TLS for Kubernetes Ingress

### Container and Code Layers
**Container Layer**
- Container vulnerability scanning and OS dependency security
- Image signing and enforcement
- Disallow privileged users
- Use container runtime with stronger isolation

**Code Layer**
The application code is one of the primary attack surfaces over which you have the most control.
- Access over TLS only
- Limiting port ranges of communication
- Third-party dependency security
- Static code analysis
- Dynamic probing attacks

### Infrastructure Security
Suggestions for securing your infrastructure in a Kubernetes cluster.

**Network Access to the API Server (Control Plane)**
All access to the Kubernetes Control Plane is not allowed publicly on the internet and is controlled by network access control lists restricted to the set of IP addresses needed to administer the cluster.

**Network Access to Nodes**
Nodes should be configured to only accept connections from the Control Plane on the specified ports, and accept connections for services in Kubernetes of type NodePort and LoadBalancer.

**Kubernetes Access to Cloud Provider API**
Each cloud provider grants a different set of permissions to the Kubernetes Control Plane and nodes. It's best to provide the cluster with cloud provider access that follows the principle of least privilege for the resources it needs to administer.

**Access to etcd**
Access to etcd (the datastore for Kubernetes) should be limited to the Control Plane only. Depending on your configuration, you should attempt to use etcd over TLS

**etcd Encryption**
Wherever possible, it's a good practice to encrypt all storage at rest, and since etcd holds the state of the entire cluster (including Secrets), its disk should definitely be encrypted at rest.

### AAA
**Authentication, Authorization, and Accounting** (AAA) form a framework for identity management systems.

**Authentication** - identifying who you are
- Static passwords
- One-time password (OTP) - MFA/UFA
- Digital certificates (x.509)
- Basic auth

**Authorization** - getting permission
- Role-Based Access Controls (RBAC)

**Accounting** (auditing) - to log and audit trails
- Audit policies
- Audit backends (where the logs will be stored)

### Role-Based Access Controls
**Role-Based Access Controls** (RBAC) is a way of defining permissions for identities based on an organizational role.

RBAC authorization uses the rbac.kubernetes.k8s.io API group to drive authorization decisions, allowing you to dynamically configure policies through the Kubernetes API.

To enable RBAC, start the API Server with the `--authorization-mode` flag.

```bash
kube-apiserver --authorization-mode=RBAC
```

With Kubernetes RBAC, there are only allow rules. Everything is denied by default.

### Role-Based Access Controls Types
The RBAC API declares four kinds of Kubernetes objetcs: Role and Role Binding, Cluster and Cluster Role Binding.

A **Role** is a set of permissions for a particular namespace.

A **ClusterRole** is a set of permissions across a namespace.

**Role Binding** and **Cluster Role Binding** link permissions to Subjects (an identity), such as:
- User account - a single user
- Service account - represents a machine user, to be used by an application service
- Group - a group of user accounts and/or service accounts

### Role Configuration Example
A Role can be configured for a particular namespace. The `kind` can be set to `Role` or `ClusterRole`. The rules (permissions) specify actions this role is allowed to perform.

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""] # indicates core API group
  resources: ["pods"]
  vergs: ["get", "watch", "list"] 
```

### Secrets Management
A **Secret** is similar to a ConfigMap with the exception that they can be encrypted. In its configuration, its `type` will be `kubernetes.io/basic/auth`.

By default, secrets are unencrypted in the etcd store. 
- Anyone with access to etcd has access to the secrets
- Anyone who has access to a pod within a namespace will have access to the Secrets used by that pod

Keep Secrets safe:
- Enable encryption at rest for Secrets
- Enable or configure RBAC rules that restrict reading data in Secrets
- Use mechanisms such as RBAC to limit whihc principals are allowed to create new Secrets or replace existing ones

### Network Policy
**Network Policies** act as virtual firewalls for pod communication.

Pod communication can be restricted based on the following scopes:
- Pod to pod
- Namespaces
- Specific IPs

**Selectors** are used to select resources with matching labels for the Network Policy to be applied to.

The Network Plugin you are using, such as Calico, Weave, Cilium, Kube-router Romana, must support Network Policies.

### Calico
**Calico** is an open-source network and network security solution for containers, VMs, and native host-based workloads.

Calico supports a broad range of platforms, including:
- Kubernetes
- OpenShift
- Mirantis Kubernetes Engine (MKE)
- OpenStack
- Bare metal services

Calico gives you a choice of dataplanes:
- Linux eBPF
- Standard Linux
- Windows HNS

Calico Network Policies extend the base functionalities of network policies:
- policies can be applied to any object
- the rules can contain specific actions
- you can use ports, port ranges, protocols, HTTP/ICMP attributes, IPs or subnets, any selectors as a source/target of the rules
- you can control traffic flows via DNAT settings and policies for traffic forwarding

Calico can perform better than alternatives, such as Flannel, Cilium, WeaveNet.

### Anatomy of a Network Policy File
For a network policy, you'll specify either a `podSelector` or a `namespaceSelector`.

You can define `ingress` rules, permitting traffic entering a pod, as well as `egress` rules, permitting traffic exiting a pod.

### In Transit vs At Rest
**Encryption In Transit** refers to data that is secure while moving between locations, using algorithms like TLS or SSL.

**Encryption At Rest** refers to data that is secure while residing in storage or in a database, using algorithms such as AES or RSA.

**Transport Layer Security** (TLS) is an encryption protocol for data integrity between two or more communicating applications. TLS 1.0, 1.1 are deprecated. TLS 1.2 and 1.3 are current best practice.

**Secure Socket Layers** (SSL) is an encryption protocol for data integrity between two or more communicating applications, and the predecessor to TLS. SSL 1.0, 2.0, and 3.0 are deprecated.

### Certificates and TLS
Kubernetes provides a certificates.k8s.io API, which lets you provision TLS certificates that you control which are signed by a Certificate Authority (CA). The CA and certificates can be used by your workloads to establish trust.

**Public Key Infrastructure** (PKI) is a set of roles, policies, hardware, software, and procedures needed to create, manage, distribute, use, store, and revoke digital certificates and manage public-key encryption.

An **x.509 certificate** is a standard defined by the International Telecommunication Union (ITU) for public key certifications.

x.509 certifications are used in many internet protocols:
- SSL/TLS and HTTPS
- Signed and encrypted email
- code signing and document signing

A certificate contains:
- an identity - hostname, organization, or individual
- a public key - RSA, DSA, ECDA

Kubernetes requires PKI for the following operations:
- Client certificates for the kubelet to authenticate to the API Server
- Server certificate for the API Server endpoint
- Client certificates for administrators of the cluster to authenticate to the API Server
- Client certificates for the API Server to talk to the kubelets
- Client certificate for the API Server to talk to etcd
- Client certificate/kubeconfig for the controller manager to talk to the API Server
- Client certificate/kubeconfig for the scheduler to talk to the API Server
- Client and server certificates for the front-proxy

Most certificates are stored in `etc/kubernetes/pki`. Lightweight distributions store them in different locations.

### Kubernetes Security Best Practices
Best practices of securing Kubernetes according to Aqua Security.

1. Enable Kubernetes Role-Based Access Controls (RBAC)
2. Use third-party authentication for API Server
3. Protect etcd with TLS, firewall, and encryption
4. Isolate Kubernetes nodes
5. Monitor network traffic to limit communications
6. Use process whitelisting
7. Turn on audit logging
8. Keep Kubernetes version up to date

## Autoscaling
**Autoscaling** is when systems without manual intervention adjust capacity (such as CPU or RAM) to meet the demands of user traffic by adding or removing resources. It is  commonly triggered by events. 

**Pod-based Scaling**
- **Horizontal Pod Scaling** (HorizontalPodAutoscaler) - adds more pods to meet the demand
- **Vertical Pod Scaling** (VerticalPodAutoscaler) - resizes pods for the optimal CPU and memory resources

**Node/Cluster-based Scaling**
- Cluster Auto Scaling (Cluster Autoscaler or Karpenter) - adds or removes nodes (servers) based on demand

**Cluster API**
Declarative APIs and tooling to simplify provisioning, upgrading, and operating multiple Kubernetes clusters. Cluster API can be extended to support any infrastructure (AWS, Azure, vSphere), bootstrap, or Control Plane provider (kubeadm is built-in).

### Scale vs Autoscale
The `scale` command will:
- update the amount of replicas in the state of the deployment object
- perform a deploy

```bash
kubectl scale --replicas=3 deploy/my-app
```

The `autoscale` command is used to create a HorizontalPodAutoscaler.

```bash
kubectl autoscale deployment foo --min=1 --max=5 --cpu-percent=80
```

### KEDA
Kubernetes Event-driven Autoscaling (KEDA) allows you to scale based on event data.

KEDA has a wide range of scalers, including:
- ActiveMQ
- Apache Kafka
- AWS CloudWatch
- AWS Kinesis Stream
- Cassandra
- Datadog
- Elasticsearch
- Kubernetes Workload
- MongoDB
- Microsoft SQL Server
- MySQL
- New Relic
- PostgreSQL
- Prometheus
- RabbitMQ
- Redis Streams

## Open Standards
**Open Standards** are when multiple organizations adopt a specific technical standard. A standard is considered open when a public-facing community can participate in the development, maintenance, and future changes to the standard.

**Open Container Initiative (OCI)**
Defines industry standards around container image formats and runtimes to make sure that all container runtimes can run images produced by any build tool.

**Container Networking Interface (CNI)** 
A specification and library for writing plugins to configure network interfaces in Linux containers.

**Container Runtime Interface (CRI)**
A plugin interface which enables kubelet to use a wide variety of container runtimes, without the need to recompile. CRI-O is an implementation of the Kubernetes CRI to enable the use of OCI compatible runtimes.

**Container Storage Interface (CSI)**
A standard for exposing arbitrary block and file storage systems to containerized workloads on container orchestration systems like Kubernetes. 

**Open Telemetry**
A collection of tools, APIs, and SDKs to instrument, generate, collect, and export telemetry data (metrics, logs, and traces).

## Governance
### CNCF Governance Structure
The CNCF is composed of three main bodies:
1. **Governing Board** (includes Marketing Committee)
	- Responsible for marketing
	- Budget decisions
	- Other business oversight
2. **Technical Oversight Committee** (TOC) (includes Special Interest Groups, SIGs)
	- Defines and maintains technical vision
3. **End User Community** (includes End User SIGs and User Groups)
	- Provides feedback from companies to improve cloud native ecosystem

Memberships are composed of: Platinum, Gold, Silver, End User, and Academic/Non-Profit members.

### CNCF Memberships
Platinum Members:
- Appoint one representative to the CNCF Governing Board
- Appoint one representative as a voting memebr in any subcommittes or activities of the Governing Board
- Enjoy most prominent placement in displays of membership including on the website

Gold Members:
- Appoint one representative to the CNCF Governing Board for every 5 Gold memebrs, up to 3 maximum Gold representatives

Silver Members:
- Appoint one representative to the CNCF Governing Board for every 10 Silver members, up to 3 maximum Silver representatives

End User Members:
- Participate in the End User Advisory Committee
- Nominate one representative to the End User Technical Advisory Board

Academic and Non-Profit Members:
- Participation is limited to academic and non-profit institutions and requires approval by the Governing Board
- Entitled identify their organization as members supporting the mission of the CNCF and any other rights or benefits as determined by the Governing Board

Platinum Membership - $370,000 annually at 3-year minimum contract (AWS, Apple, New Relic)

Gold Membership - $120,000 annually (Salesforce, American Express, Equinix)

Silver Membership - $7,000-50,000 from under 50 to 5,000+ employees (Digital Ocean, Accenture, Deloitte, HashiCorp)

Academic and Non-Proft Memberships - $1,000/500 annually (Mitre, Wikimedia Foundation, CloudFoundry)

End User Members - No cost

### CNCF Governing Board
The **Governing Board** is responsible for marketing and other business oversight and budget decisions for the CNCF.

The Board does not make technical decisions for the CNCF, other than working with the TOC to set the overall scope for the CNCF.

The Board approves a budget directing the use of funds raised from all sources of revenue to be used for technical, marketing, or community investments that advance the mission of the CNCF.

The Board elects a Chair to preside over meetings, authorize expenditures approved by the budget and manage any day-to-day operations.

There are ~30 board members and the Board meets 3-5 times a year.

The Board:
- defines and enforces policy regarding intellectual property (copyright, patent or trademark) of the foundation
- directs marketing and evangelism efforts through events, press, and analyst outreach, web, social, and other marketing efforts
- oversees operations and qualification efforts
- establishes and oversees any committees created to drive the mission of the foundation
- establishes and executes a brand compliance program based on the CNCF requirements, which may include a certification test, to use the brand marks established by the TOC
- adopts guidelines or policies for the use of trademarks
- provides overall financial governance

### Technical Oversight Committee
The **Technical Oversight Committee** (TOC) provides technical leadership to the cloud native community.

Their responsibilities include:
- defining and maintaining the technical vision for the CNCF
- approving new projects and creating a conceptual architecture for the projects
- aligning projects and removing/archiving projects
- accepting feedback from the End User Community and mapping to projects
- aligning interfaces to components under management (code reference implementations before standardizing)
- defining common practices to be implemented across CNCF projects

### Special Interest Groups
**Special Interest Groups** (SIGs) are specialized committees that work under and report to the TOC.

SIGs are long-lived groups and are led by recognized and relevant experts.

SIGs include:
- Traffic
- Observability
- Governance
- App Delivery
- Core and Applied Architecture
- Security

SIGs are responsible for:
- Strengthening the project ecosystem to meet the needs of end users and project contributors
- Identifying gaps in the CNCF project portfolio, finding and attracting projects to fill these gaps
- Educating and informing users with unbiased, effective, and practically useful information
- Focusing attention and resources on helping foster project maturity, systematically across CNCF projects
- Clarifying relationships between projects, CNCF project staff, and community volunteers
- Engaging more communities and creating an on-ramp to effective TOC contribution and recognition
- Reducing some project workload on TOC while retaining executive control and tonal integrity with the elected body
- Avoiding creating a platform for politics between vendors

### End User Community
CNCF End Users are individuals or organizations that use cloud-native technologies but do not sell cloud-native services

Vendors, consultants, training partners, and telcos are not End Users.

The End User Community acts as a feedback loop between those using cloud-native and those maintaining and building cloud-native solutions.

The End User Comunity is an ecosystem of:
- Finding cloud-native talent
- Finding local user groups
- Meeting project maintainers
- Contributing to the CNCF technology radar

### End User Technology Radar
A technology radar is an opinionated guide to a set of emerging technologies.

The **CNCF End User Technology Radar** is intended for a technical audience who want to understand what solutions ernd users use in cloud native, and which they recommend.

**Assess**
The CNCF End User Community has tried it out and find it promising. They recommend having a look at these items when you face a specific need for the technology in your project. Such as Cilium, Linkerd, GitHub Actions

**Trial**
The CNCF End User Community has used it with success, and recommends you have a closer look at the technology. Such as XRay

**Adopt**
The CNCF End User Community can clearly recommend this technology. They have used it for long periods of time on many teams and it has proven stable and useful. Such as HashiCorp Vault, Terraform

### CNCF Charter
The CNCF Charter is a public document that helps define and guide the CNCF. It contains:
- The organization structure of the CNCF
- The mission and values of the CNCF
- The description of the membership tiers
- The definition of CNCF projects
- CNCF governing policies
- Codes of Conduct
- General definitions and rules in relation to the CNCF

### CNCF Values
The CNCF strives to adhere to the following principles:
- **Fast is better than slow** - enable projects to progress at high velocity to support aggressive adoption by users
- **Open** - be open and accessible, and operate independently of specific partisan interests. Accept all contributors based on the merits of their contributions. Technology must be available to all according to open source values. The technical community and its decisions shall be transparent
- **Fair** - avoid undue influence, bad behaviour, or "pay-to-play" decision making
- **Strong technical identity** - achieve and maintain a high degree of its own technical identity shared across projects
- **Clear boundaries** - establish clear goals to allow projects to co-exist. Help the ecosystem understand where to focus for new innovation
- **Scalable** - support all scales of deployment, from startups to service providers to enterprises
- **Platform agnostic** - the specifications developed will not be platform-specific to ensure that they can be implemented on a variety of architectures and OSes

### KubeCon and CloudNativeCon
**KubeCon** is a technology conference for Kubernetes. **CloudNativeCon** is a technology conference for Cloud Native. 

They are now essentially a single conference referred to as KubeCon + CloudNativeCon.

The conference happens twice a year, in North America and Europe. The North American event also has adjacent conferences: IstioCon, ServiceMeshCon, GitOpsCon.

### CNCF Projects
**CNCF Projects** are technologies managed by the CNCF. Many CNCF projects are developed by external tech companies and then handed over to the CNCF for long-term support.

Projects are categorized based on their "maturity level":
- **Graduated** - production ready for enterprise
- **Incubating** - the API might rapidly change, may be incomplete and unsuitable for large enterprises
- **Sandbox** - experimental, prototypes, may not pass security review

The maturity level is based on the Crossing the Chasm diagram from _Crossing the Chasm_ (1991).

One way to locate Sandbox CNCF projects is to filter based on CNCF relation.

The Sandbox process goes: project proposal -> TOC triage (brief assessment) -> SIG presentation and recommendation -> TOC review -> Sandbox (three TOC sponsors step forward) 

The Incubation process goes: project proposal -> TOC incubation sponsor steps forward -> due diligence (tech and gov, user interviews) -> TOC review -> TOC vote

There is at least one graduated CNCF project for each broad Cloud Native category:
- Container runtime - containerd
- Coordination and service discovery - CoreDNS, etcd
- Service proxy - Envoy
- Logging - Fluentd
- Container registry - Harbor
- Application definition and image build - Helm
- Tracing - Jaeger
- Scheduling and orchestration - Kubernetes
- Service mesh - Linkerd
- Security and compliance - Open Policy Agent (OPA), The Update Framework (TUF)
- Monitoring - Prometheus
- Cloud native storage - Rook
- Databases - TiKV, Vitess

## Serverless
Serverless architecture generally describes fully managed cloud services. Serverless is not a boolean (yes/no) but on a scale where a cloud service has a degree of serverless. Some services are more serverless than others.

A serverless service could have all or most of the following characteristics:
- Highly elastic and scalable
- Highly available
- Highly durable
- Secure by default
- Abstracts away the underlying infrastructure
- Pay-for-value, billed based on execution of business task
- Scales to zero, resources cost nothing when not in use

### Cloud Native Kubernetes Serverless
NCF has a landscape just for serverless.

What CNCF classifies as "serverless" are:
- Function as a service
	- AWS Lambda
	- Azure Serverless Functions
	- Google CLoud Functions
- Serverless Frameworks
	- Dapr
	- AWS SAM
	- Chalice
- Installable Platforms
	- Kubernetes-based Event Driven Autoscaling (KEDA)
	- Apache OpenWhisk
	- OpenFaaS
	- Knative
	- Fission
	- Kubeless
- Tools
	-  Lumigo
	- Dashbird

### Knative
Knative is a Kubernetes-based platform to deploy and manage modern serverless workloads.

Knative is a project to create a standard set of building blocks for Kubernetes to enable serverless development patterns.

Knative is generally composed of two parts:
- Knative Serving
	- take containerized code and deploy it with relative ease
	- scale to zero costs
- Knative Eventing
	- trigger serverless functions based on Kubernetes API events
	- loop in other event sources to trigger serverless functions

It's not a complete serverless framework and doesn't offer a Function as a Service offering.

Knative defines its own set of Kubernetes Objects as Kubernetes Custom Resource Definitions (CRDs). 

Knative components include:
- Service - manage the lifecycle of a workload
- Route - map network endpoints
- Configuration - maintain desired state
- Revision - point-in-time snapshots of code

Knative has its own CLI called kn, which is used alongside kubectl.

```bash
kn service create hello \
--image gcr.io/knative-samples/helloworld-go \
--port 8080 \
--env TARGET=world \
--revision-name=world
```

### Knative vs OpenFaaS
Unlike OpenFaaS, Knative is not a fuly-fledged serverless platform, but is better positioned as a platform for creating, deploying, and managing serverless workloads.

However, from the point of view of configuration and maintenance, OpenFaaS is simpler. With OpenFaaS, there is no need to install all components seperately, as with Knative, and you don't have to clear previous settings and resources for new developments if the required components have already been installed.

A significant drawback of OpenFaaS is that the container launch time depends on the provider, while Knative is not tied to any single cloud solution provider. Based on the pros and cons of both, organizations may also choose to use Knative and OpenFaaS together to effectively achieve different goals.

## Observability
### The Pillars of Observability
**Observability** is the ability ot measure how internal systems work in order to answer questions regarding performance, tolerance, security, and faults with a system/application.

To obtain observability, you need to use metrics, logs, and traces. Using them in isolation will not give you observability.

**Metrics** are numbers that are measured over a period of time. For example, average CPU usage over a specified period.

**Logs** are text files where each line contains event data about what happened at a certain time.

**Traces** are a history of requests as they travel through multiple apps/services so that you can pinpoint performance or failure.

### Open Telemetry
**Open Telemetry** (OTEL) is a collection of open-source tools, APIs and SDKs to instrument, generate, collect, and export telemetry data.

Open Telemetry standardizes the way telemetry data (metrics, logs, and traces) are generated and collected.

A Wire Protocol refers to a way of getting data from point to point, such as SOAP, AMQP.

Instrumentation is the act of embeddinga monitoring library into your existing application in order to capture monitoring data, such as metrics, traces, or logging.

Open Telemetry supports a variety of languages, including C++, Rust, Go, Java, Python, JavaScript.

For certain frameworks there are plug and play libraries to quickly instrument your apps:
- Spring
- ASP.NET Core
- Express
- Quarkus

The Open Telemetry Collector is an agent installed on the target machine, or as a dedicated server, and is a vendor-agnostic way to receive, process, and export telemetry data.

It removes the need to run, operate, and maintain multiple agents/collectors. This works with improved scalability and supports open-source observability data formats (such as Jaeger, Prometheus, Fluent Bit) sending to one or more open-source or commercial backends. The local Collector agent is the default location to which instrumentation libraries export their telemetry data.

### Prometheus
**Prometheus** is an open-source systems monitoring and alerting toolkit originally built at SoundCloud. It is a timeseries database which collects and stores metrics as time series data.

Prometheus' main features are:
- a multi-dimensional data model with time series data identified by metric name and key/value pairs
- PromQL, a flexible query langauge to leverage this dimensionality
- no reliance on distributed storage; single server nodes are autonomous
- time series collection happens via a pull model over HTTP
- pushing time series is supported via an intermediary gateway
- targets are discovered via service discovery or static configuration
- multiple modes of graphing and dashboarding are supported

Prometheus values reliability. You can always view what statistics are available about your system, even under failure conditions. 

If you need 100% accuracy, such as for per-request billing, Prometheus is not a good choice as the collected data will likely not be detailed and complete enough. In such a case, you would be best off using some other system to collect and analyze the data for billing, and Prometheus for the rest of your monitoring.

Prometheus scrapes metrics from instrumented jobs, either directly or via an intermediary push gateway for short-lived jobs. It stores all scraped samples locally and runs rules over this data to either aggregate and record new time series from existing data or generate alerts. Grafana or other API consumers can be used to visualize the time series data.

### Grafana
**Grafana** is an open-source analytics and interactive visualization web application. Grafana is commonly used along with a time series database like: InfluxDB, Prometheus, or Graphite.

### Traces and Spans
A **Trace** is a data/execution path through a system and can be thought of as a directed acyclic graph (DAG) of spans.

A **Span** represents a logical unit of work that has an operation name, the start time of the operation, and the duration. Spans may be nested and ordered to model causal relationships.

### Cost Management
- **Label resources**, such as metadata, to be able to use a visualization tool like Prometheus and Grafana to visualize costs
- **Find idle and unallocated resources** - visualize idle CPU, memory and storage with Prometheus and Grafana
- **Rightsize workloads**
	- VerticalPodAutoscaler - adjust CPU and memory of pods
	- HorizontalPodAutoscaler - add and remove pods to meet demand
- **Find cluster downsizing opportunities**
	- ClusterAutoscaler - and or remove nodes to meet demand
- **Use (free trials of) Kubernetes cost tools**, such as Kubecost
- **Estimate future costs** - use load testing such as with SpeedScale, K6, JMeter, Gatling
- **Avoid utilization waste** (running but not used/not live)
	- Use serverless architecture that scales to zero when no traffic for a period of time
- Reduce technical debt
	- Evaluate architecture to reduce the amount of pods
	- Evaluate cloud native technologies

### Kubernetes System Logs and Klogs
System Logs record events happing in the cluster, which can be useful for debugging.

You can configure log verbosity to see more or less detail.

Logs can be as coarse-grained as showing errors within a component, or as fine-grained as showing step-by-step traces of events (like HTTP access logs, pod state changes, controller actions, or scheduler decisions).

In kubectl you can view logs from pods with the `logs` command.

```bash
kubectl logs nginx --all-containers=true
```

There is a Kubernetes logging library, Klog, which is based off Go's logging library and generates log messages for the Kubernetes system components.

## Cloud Native Application Delivery
### Testing and Chaos Testing
**Testing** is asserting the expectations of the input and outputs of functions.

**Chaos testing** is building a system to withstand and tolerate any kind of failure by purposely introducing random failures in a production system.

Testing frameworks that can be used with Kubernetes include: ChaosKube, TestKube, and ChaosMonkey.

### Helm
A package manager is a collection of software tools that automates the process of installiing, upgrading, configuring and removing programs for a computer in a consistent manner. 

**Helm** is the package manager for Kubernetes and is broadly composed of three concepts:

- **Chart** - contains all of the resource  definitions necessary to run an application, tool, or service inside of a Kubernetes cluster
- **Repository** - the place where charts can be collected and shared
- **Release** - an instance of a chart running in a Kubernetes cluster

A Helm chart is a collection of files within a directory. These will include `Chart.yaml` (containng information about the chart) and `values.yaml` (the default configuration values for the chart).

Helm reserves the use of `charts/`, `crds/`, and `templates/` directories. Otherwise files will be left as they are.

The Helm chart describes the contents of the package such as the type of chart and its dependencies.

To package a chart directory in a versioned chart archive, use the `helm package` command.

```bash
helm package --sign ./mychart --key mykey --keyring ~/.gnupg/secring.gpg
```

Versioned chart archives are used by Helm package repositories. Artifact Hub is where you can find published Helm charts.

```bash
helm repo add nicholaswilde https://nicholaswilde.github.io/helm-charts/
helm repo update
helm install postgres nicholaswilde/postgres
```

### Kustomize
Kustomize provides more flexibility when writing Kubernets configuration files by allowing you to overlay (override) to "patch" configurations. Kustomize is built into kubectl.

With Kustomize, you define your base architecture in a `base` directory, and then have a `patches` directory with subdirectories for `dev` and `prod`. The `kustomization.yaml` files define what will be overwritten in the base components.

### Infrastructure as Code
Manually configuring your cloud infrastructure allows you to easily start using new service offerings to quickly prototype architectures, however it comes with several downsides:

- Its easy to misconfigure a service through human error
- Its hard to manage the expected state of configuration for compliance
- Its hard to transfer configuration knowledge to other team members

**Infrastructure as Code** (IaC) is when you write a configuration script to automate creating, updating, or destroying cloud infrastructure.

IaC is a blueprint of your infrastructure which lets you easily share, version, or inventory your cloud infrastructure.

Infrastructure as Code tools fall into two broad categories:

**Declarative**
- Explicit. What you see is what you get
- More verbose but zero chance of misconfiguration
- Uses scripting languages, such as JSON, Yaml, XML

Examples include AWS CloudFormation, Azure Blueprints and ARM Templates, Google Cloud's Cloud Deployment Manager, and Terraform, which supports many cloud service providers.

**Imperative**
- Implicit. You say what you want and the rest is filled in
- Less verbose, but you could end up with misconfiguration
- Does more than declarative
- Uses programming languages, such as Python or JavaScript

Examples include the AWS Cloud Development Kit (CDK), which offers many built-in templates for opinionated best practices, or Pulumi, which supports AWS, GCP, Azure, and Kubernetes.

### IaC for Kubernetes
**Managing the Infrastructure of the Cluster**
Terraform (or any IaC tool) can be used to provision the cluster itself and managed services to be used alongside the cluster, such as managing a database

Terraform can technically manage cluster components via their Manifest module so you can benefit from the state managemen provided by Terraform. Though Kubernetes already manages state with the Controller Manager and etcd.

**Managing Infrastructure in the Cluster**
For managing application infrastructure within the cluster (Pods, Services, Ingress), it's recommended to package these as Helm charts and use that in your CI/CD.

### GitOps
**GitOps** is when you take Infrastructure as Code and use a Git repository to introduce a formal process to review and accept changes to infrastructure code. Once that code is accepted, it automatically triggers a deploy.

For example, a change to Terraform could be committed to GitHub. Once a PR is approved and merged, a CI/CD process is triggered, deploying the changes to the cloud platform.

### CI/CD Models
**Production** (prod) is the live server where real users are using the platform.

**Staging** is a private server where developers do final manual tests (QA) before deploying to prod.

The CI/CD lifecycle is generally: Code -> Build -> Integrate -> Test -> Release -> Deploy.

Continuous Integration involves a developer's code being automatically reviewed.

Continuous Delivery involves preparing a developer's code for release to production.

Continuous Deployment involves automatically deploying code as soon as developers push code and all tests pass.

### Argo vs Flux
The CNCF have two CI/CD projects that serve the same purpose but take different approaches.

**Flux**
- Originally developed by Weaveworks
- CLI-first approach
- Experimental web UI as a plugin
- Supports role-based access controls (RBAC)
- Flux 2+ supports multi-tenancy
- Supports Helm and Kustomization
- Automates container updates

Argo
- Both CLI and web UI
- Supports role-based access controls (RBAC)
- Supports single sign on (SSO)
- Supports multi-tenancy
- Supports Helm, Kustomization, ksonnet, and jsonnet
- Uses manual commit and sync to update containers

Generally Flux is simpler.

### Jenkins, Jenkins X, and CloudBees
**Jenkins** is a popular and mature open-source CI/CD tool for any kind of workload. It's written in Java, has many plugins for any use case, and can be used to deploy applications to Kubernetes

**Jenkins X** is an open-source CI/CD tool for modern cloud application on Kubernetes. It has a reputation for being easier to use. It may replace or merge with Jenkins in the future to only have a single CI/CD tool for all use cases.

**CloudBees** is the commercial distribution of Jenkins and Jenkins X for large and compliance-first organizations. CloudBees acquired InfraDNA, the organization that originally created Jenkins.

### CircleCI
CircleCI is a proprietary, fully-managed CI/Cd service to make deployments easy and seamless. CircleCI can support deploying applications ot Kubernetes.

## Deployment Strategies
A deployment strategy is a way to change or upgrade an application.

A **Rollout** is when you replace or update servers/pods with a new version of an application.

A **Rollback** is when you replace or revert recently updated servers/pods back to a previous version.

There are several different deployment strategies that can be used with Kubernetes:
- **Recreate** - Terminate the current pods, create new pods all at once
- **Rolling Update** - Replace one or multiple pods at a time
- **Canary** - Add new pods and route a subset of your users to the new server. If no bugs or errors occur, roll out changes to all pods
- **Blue/Green** - Deploy an exact copy of your entire infrastructure, swap the traffic, and then either terminate or rol back to the old environment
- **A/B Testing**, **Red/Black** - Similar to Canary and Blue/Green but continuously keep the alternate environments running to test features on a subset of users
- **Dark Launches** - Similar to A/B testing except you use a feature flag to roll out new features, and rollback by turning off the feature in the software instead of reverting infrastructure changes

### Recreate
The **Recreate** strategy involves terminating all running instances and recreating them with a new version. It's also known as an In-Place deploy.

In your deployment file you can define your strategy type as `Recreate`.

```yaml
spec:
  replicas: 3
  strategy:
    type: Recreate
```

You terminate all pods and traffic is temporarily interrupted. New pods are created and traffic is routed to them.

- Very simple and can be very fast
- Users will experience downtime
- Ideal for non-production workloads or where interruptions can be tolerated

### Rolling Updates
The **Rolling Updates** strategy involves replacing one or more pods at a time. This is the default strategy of Kubernetes.

A specified amount of pods are terminated, new pods are created and the next set of pods are terminated. This repeats until done.

- Reduced availability might happen while each set of pods is terminated and new pod are created
- Rollbacks can be slower and harder
- Deploys will be slow

If there's not enough capacity (CPU, memory, bandwidth) to meet the demands of traffic, then users can experience degraded, delayed service or no access to services at all. 

Two important values are:
- maxSurge - the amount of pods that can be added at a time
- maxUnavailable - the amount of pods that can be unavailable at a time

```yaml
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 2
      maxUnavailable: 0
```

A maxSurge and maxUnavailable of 2 would ensure no drop in availability. The deployment would have to first create the new pods before tearing down the old.

### Canary
The **Canary** strategy deploys a new version of the app into a new pod and serves it to a subset of existing users. If no error or bug has occurred, the rollout changes to all users by replacing old pods with new pods.

- Fast rollout
- Slow rollback
- No drop in availability

Canary will use the load balancer weighted rules to only send an amount of traffic to the canary pods and original pods.

### Blue/Green
The **Blue/Green** strategy is when you create a completely new environment of all components and you send all traffic to the new (green) environment. If it's all ok, you terminate the old (blue) environment. If anything goes wrong, you roll back to blue and tear down green.

- Zero downtime
- No reduced availability
- Slow to deploy, but faster than Canary
- If something goes wrong, larger impact to users immediately
- Can instantly roll back to previous infrastructure

### A/B Testing, Red/Black
**A/B Testing** or the **Red/Black** strategy is similar to Canary and Blue/Green but serves the new app (or experimental features) to a subset of users based on a set of load balancing rules.

The key difference is that Canary and Blue/Green deployments are temporary, as you intend to roll out changes to all pods, while A/B Testing and Red/Black happen for a longer period of time.

### Dark Launches
Similar to A/B Testing, except that it happens at the application layer.

- You want to test a feature on a subset of users
- You code a feature flag into your app to turn the new feature on or off
- If users are happy with the feature, you leave it switched on. If not, you turn it off
- Rollbacks are faster as rollback at the infrastructure level is'nt required

### Deployment History
You can check the history of previous deploys with the following command:

```bash
kubectl rollout history deploy/<deployment_name>
```

### Deployment Rollout Status
You can get the status of your deployment with the rollout status command:

```bash
kubectl rollout status deployment/<deployment_name>
```

### Deployment Rollback
You can roll back to the previous deployment (shown in the rollout history) with rollout undo:

```bash
kubectl rollout undo deployment/<deployment_name>
```