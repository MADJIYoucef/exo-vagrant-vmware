**Exercise: Deploy Nginx to Kubernetes**

**Objective:** Create Kubernetes manifests to deploy an Nginx container as a Pod.

**Steps:**

1. **Create a Deployment Manifest (`nginx-deployment.yaml`):**
   Create a YAML file called `nginx-deployment.yaml` and define a Deployment resource to deploy an Nginx container. Here's a basic example:

   ```yaml
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: nginx-deployment
   spec:
     replicas: 3
     selector:
       matchLabels:
         app: nginx
     template:
       metadata:
         labels:
           app: nginx
       spec:
         containers:
         - name: nginx-container
           image: nginx:latest
   ```

   In this manifest:
   - We define a Deployment named `nginx-deployment`.
   - We specify that we want 3 replicas of the Nginx Pod.
   - We label the Pods and selector with `app: nginx`.
   - We use the official Nginx Docker image.

2. **Apply the Deployment:**
   Apply the `nginx-deployment.yaml` manifest to your Kubernetes cluster using the `kubectl apply` command:

   ```bash
   kubectl apply -f nginx-deployment.yaml
   ```

   This will create the Deployment, which will in turn create and manage the desired number of Nginx Pods.

3. **Verify the Deployment:**
   Use `kubectl` commands to verify that the Deployment and Pods have been created successfully:

   - Check the status of the Deployment:
     ```bash
     kubectl get deployments
     ```

   - Check the status of the Pods:
     ```bash
     kubectl get pods
     ```

   - Check the details of a Pod:
     ```bash
     kubectl describe pod <pod-name>
     ```

4. **Access the Nginx Service:**
   To access the Nginx service running inside the Pods, you can create a Service resource or use port forwarding. Here's an example of creating a NodePort Service:

   Create a `nginx-service.yaml` file:

   ```yaml
   apiVersion: v1
   kind: Service
   metadata:
     name: nginx-service
   spec:
     selector:
       app: nginx
     ports:
     - protocol: TCP
       port: 80
       targetPort: 80
     type: NodePort
   ```

   Apply the service manifest:

   ```bash
   kubectl apply -f nginx-service.yaml
   ```

   You can then access Nginx in a web browser by using the NodePort assigned by Kubernetes. To find the NodePort, run:

   ```bash
   kubectl get svc nginx-service
   ```

   Open a web browser and navigate to `http://NODE_IP:NODE_PORT`, where `NODE_IP` is the IP address of your Kubernetes node and `NODE_PORT` is the NodePort value.

Congratulations! You've successfully deployed an Nginx container to Kubernetes using manifests. This exercise covers the basics of creating a Deployment and accessing a service within your cluster.
