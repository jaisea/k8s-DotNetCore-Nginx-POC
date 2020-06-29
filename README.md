# k8s-DotNetCore-Nginx-POC

# Task 
Your task is to build and deploy a distributed web application to Kubernetes. The application consists of a Nginx powered file server that responds to each request with a static json file and a webApi application that can work simultaneously and make request to the file server. 
 
## WebAPI Application
There is a .net core web api (version 3.1.1) application, that should be built in a container and deployed into k8s cluster. The minimum amount of instances to run simultaneously is 2. It's a simple web application that returns a random weather forecast,  some simple stats (count of received requests) and a static file from the file server.  

## File server 
Use an official nginx image and update it so that it will return a static file. The file is named static.json. The file should be accessible by GET request to URL which is nginx container IP address within k8s. 

## Configuration 
By default the web application doesn’t know the URL of the file server. It’s dynamically taken from the environment variable “NGINX”. 

## Deployment 
Create a deployment for the application into the k8s Minikube. 
 
## Result 
```
GET http://IP:5001/weatherforecast - ([{"date":"2020-03-28T16:29:25.3487316+01:00","temperatureC":-9,"temperatureF":16,"summary":"Sweltering"},.... 
GET http://IP:5001/weatherforecast/stats - MachineName – 9 
GET http://IP:5001/weatherforecast/fetch - {"version": "1.1.132", "buildId": "2703"}  
```