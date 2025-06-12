# Deploying with Kubernetes

This repo consists of a deployment made with __Kubernetes__.  

__Step 1:__  
In your terminal, create a directory with your preferred name.  
Change working directory to the directory you just created with the `cd` command.  
Use this command `code .` to open __VS Code__ if you have it installed already.

__Step 2:__  
Create an "__index.html__" file and use the official Nginx image from __Docker Hub__.  
Use `minikube start` to start a local cluster.  
Check if __kubectl__ is working. Use this command to do that: `kubectl version --client`.  
Use `kubectl get nodes` to verify that your __kubectl__ is functioning.  

__Step 3:__  
1. Create a deployment manifest by creating an "__nginx-deployment.yml__" file, specifying the container image, number of replica, and ports.  
2. Create a __YAML file__ called "__nginx-service.yml__" to expose the application.  
3. Use a __NodePort__ or __LoadBalancer__ service type. The purpose of this is to enable external access.  
4. In exposing the application, first set up a custom __Nginx website__ on __Kubernetes__.  
5. Modify your configurations slightly by creating a "__Dockerfile__".  
6. Build the image by using this command: `docker build -t "your-directory-name:/custom-nginx:latest .`.  
7. Run the `minikube start` command.  
8. Store your __HTML file__ (index.html) in Kubernetes and deploy NGINX which then launches the NGINX in a pod.
9. Mount your custom HTML. The purpose of this is to connect your HTML to NGINX.
10. Expose your deployment by running the command: `kubectl expose deployment nginx-service --type=NodePort --port=80`.

__Step 4:__  
1. Apply the deployment by running the command: `kubectl apply -f nginx-deployment.yml`.
2. Apply the service by running the command: `kubectl apply -f nginx-service.yml`.
3. Verify that your application is running smoothly with this command: `minikube service`.
4. Use `Ctrl + C` to stop the tunnel in order to proceed with the tasks.

__Step 5:__  
1. Scale up your deployment with this command: `kubectl scale deployment/nginx-service --replicate=5`.
2. In performing a rolling update, check your pods to see if there was any increment. Use the command: `kubectl get pods`.
3. Modify the version of your image in the deployment YAML file.
4. Apply the deployment again by using the command stated earlier in Step 4 (1).
5. Monitor the rollouts happening. Check to make sure your new image has been created and running. Use the command `kubectl describe deployment nginx-deployment | grep Image`.



