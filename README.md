# Kubernetes

# Architecture of Kubernetes

![Uploading image.png…]()

**1️⃣ Kubelet (Node Agent)**

👉 This is the brain of the worker node

What it does:
1. Talks to the Kubernetes control plane
2. Ensures containers are running as defined in Pod specs
3. Pulls container images
4. Starts/stops containers
5. Reports node & pod status

   If you deploy a pod:

apiVersion: v1
kind: Pod
spec:
  containers:
  - name: app
    image: nginx

👉 Kubelet:

- Receives this instruction
- Pulls the image
- Runs the container via container runtime

**2️⃣ Container Runtime**

👉 This is the engine that actually runs containers

**Common runtimes:**

Responsibilities:
1. Pull images from registry
2. Create/start/stop containers
3. Manage container lifecycle

Flow:

Kubelet → Container Runtime → Container

**3️⃣ Kube-Proxy (Networking Component)**

👉 Handles networking and service communication

What it does:
1. Maintains network rules (iptables/ipvs)
2. Enables communication between pods
3. Implements Kubernetes Services (ClusterIP, NodePort)

Example:

When one pod calls another via service:

frontend → backend-service → backend pod

👉 Kube-proxy routes traffic correctly
