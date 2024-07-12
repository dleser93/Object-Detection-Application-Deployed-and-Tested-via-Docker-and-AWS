# Object-Detection-Application-Deployed-and-Tested-via-Docker-and-AWS
The central problem addressed in this assignment for the lecture "Data Intensive Computing" is image detection, specifically the accurate identification and localization of objects within a large dataset of images. Developing an efficient data processing application capable of performing object detection on a large scale. The group members of this group project were Caspar Mayrgündter, Dennis Leser and Nikola Tzotchev. 

## Introduction
The assignment focuses on understanding the principles of computation and data offloading while utilizing the scalable and efficient cloud infrastructure provided by Amazon Web Services (AWS). The assignment consists of four main parts. First, we implemented a data processing application that performs object detection on images. The application accepts an array of base64 encoded strings representing images and returns the detected objects as a JSON response. Official TensorFlow documentation, specifically the object detection tutorial, was utilized as a reference during the implementation process.

Next, the application was dockerized, meaning it was deployed within a Docker container. The provided Dockerfile served as a basis for setting up the necessary environment for the application’s execution. Following the dockerization, the application was executed both locally and remotely. For local execution, the Docker container was built and started using a Docker client on the chosen operating system. Images from the provided datasets were sent to the Docker container via POST requests, encoded as base64 strings. The average inference time of the implementation was measured by collecting data on the time it took for the application to perform object
recognition on the entire dataset. For remote execution, the containerized application was deployed on AWS, leveraging the cloud infrastructure provided by the platform. Similar to local execution, images were sent to the application via POST requests, but with the URL of the AWS instance instead of localhost. Data regarding the time required to transfer each image file and the average inference time on AWS were collected and analyzed.

To facilitate access to AWS resources, the group utilized the AWS Academy program, which provided AWS console access without the need for individual credit card details. Everybody was allocated a budget of 100 Dollar for the project, which was deemed sufficient unless unnecessary AWS resources were created. A step-by-step guide was provided to ensure proper setup and usage of AWS services.

## Build and Run the Docker Container
```
docker build -t myapp .
docker run -d -p 5000:5000 myapp
```

## Requests
```
 curl -X POST -d "@content.json" http://{aws_public_ip}:5000/api/detect
# multiple images
 curl -X POST -d "@content_multiple.json" http://{aws_public_ip}:5000/api/detect
```
