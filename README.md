# 📍 Introduction

Containerization has revolutionized the way applications are deployed and managed, and Docker Swarm is a powerful tool for orchestrating containers in a production environment. In this step-by-step guide, we will walk you through the process of deploying a web application using Docker Swarm on AWS. By the end of this tutorial, you will have a robust and scalable setup for your web app.

## ✅ Solving the Problem 🧩

By deploying your web app using Docker Swarm on AWS, you are addressing several key challenges:

- **Scalability**: Docker Swarm enables you to scale your application horizontally by adding or removing nodes seamlessly. This ensures your app can handle increased traffic.

- **High Availability**: With Swarm, your app is distributed across multiple nodes, making it highly available. If one node fails, the others can continue serving the application.

- **Simplified Management**: Docker Swarm provides an easy-to-use interface for managing containerized applications, reducing the complexity of orchestration.

- **Resource Efficiency**: Containers consume fewer resources compared to traditional virtual machines, optimizing resource utilization and reducing costs.

## ✅ Step 1: Provision AWS Instances 🌐

Start by logging into your AWS portal and create three new EC2 instances, each with unique names:

- Swarm-manager
- Swarm-worker1
- Swarm-worker2

Ensure that you configure the inbound rules for these instances to allow the following traffic:

- Custom TCP port 2377 from anywhere (IPv4)
- Custom TCP port 8001 from anywhere (IPv4)

## ✅ Step 2: Install Docker 🐳

SSH into each of the two instances (Swarm-manager and Swarm-worker1) and install Docker with the Docker Engine. You can refer to Docker's official documentation or other resources for detailed instructions on Docker installation.

## ✅ Step 3: Initialize Swarm on Swarm Manager 🤖

Access the "Swarm Manager" node and initiate the Swarm by running the following command:

```bash
sudo docker swarm init
```
## ✅ Step 4: Add Workers to the Swarm 🏗️

After initializing the Swarm on the "swarm-manager" node, a key will be generated. You need to copy and run this key on the other two servers (Swarm-worker1). This step adds both machines as workers to the Swarm.

## ✅ Step 5: Check Swarm Node Status 🚥
To verify the status of all nodes in the Swarm, run the following command on the manager node:

```
docker node ls
```
This command will display information about all the nodes in the Swarm.


## ✅ Step 6: Create a Docker Service 🛠️

On the Swarm Manager node, create a Docker service using the following command:

```
sudo docker service create --name django-app-service --replicas 2 --publish 8001:8001 trainwithshubham/react-django-app:latest
```

This command creates a service named "django-app-service" with three replicas, publishing port 8001.

## ✅ Step 7: List Docker Services 📋

To list the Docker services running in the Swarm, use the following command:
```
sudo docker service ls
```

This will display a list of services, including the one you just created.

## ✅ Step 8: Verify Containers 🐋

The service you created will deploy containers on the manager and worker nodes. To check if containers are running on the manager node, execute:
```
sudo docker ps
```

You should see containers related to your service.

## ✅ Step 9: Access the Web App 🌐

Now, your web app service is running on all three nodes. To access it, grab the IP address of any of the nodes followed by port 8001, like this:

```
http://<Any_IP_of_2_VMs>:8001
http:3.82.60.74:8001
```

You should be able to access your web application through this URL.

## ✅ Step 10: Removing Nodes ♻️

If you need to remove a node from the Swarm environment, run the following command on the specific worker node:
```
sudo docker swarm leave
```

As a result, the worker node will leave the Swarm, and you can confirm its status by checking the output of:
```
docker node ls
```

# 📍 Conclusion

Congratulations! 🎉 You've successfully deployed a production-ready web app using Docker Swarm on AWS. Docker Swarm's orchestration capabilities make it easier to manage and scale your application, ensuring it runs smoothly in a production environment. Feel free to connect and follow for more informative content on containerization and cloud computing.

## 🔍 Checkout GitHub Repository for projects:

🔗 https://github.com/sumanprasad007

## 🔍 Check out my YouTube channel - Prasad Suman Mohan:

🔗 https://youtube.com/@sumanprasad007





