# Triton-Inference-Server-Deployment-with-ONNX-Models
Triton Inference Server Deployment with ONNX Models

This repository provides an example configuration for deploying models using the Triton Inference Server. The Triton Inference Server is a versatile inference serving platform that supports multiple deep learning frameworks.

# Prerequisites
Docker installed on your machine
Basic knowledge of Docker and deep learning frameworks (PyTorch, TensorFlow, ONNX Runtime, etc.)

# Getting Started
Follow the steps below to configure and start the Triton Inference Server on your local machine.


### Step 1: Clone the Repository
Clone this repository to your local machine:

git clone [<repository_url>](https://github.com/tamanna18/Triton-Inference-Server-Deployment-with-ONNX-Models/tree/main)https://github.com/tamanna18/Triton-Inference-Server-Deployment-with-ONNX-Models/tree/main
cd Triton-Inference-Server-Deployment-with-ONNX-Models 

### Step 2: Set up the Model Repository
The Triton Inference Server requires a model repository where your models will be stored. In this repository, we will use the /models directory as the model repository.

Replace <model_repository_path> with the absolute path to your desired model repository directory in the following command:

docker run --rm -p 8000:8000 --name triton-server-container -v "<model_repository_path>:/models" nvcr.io/nvidia/tritonserver:21.06-py3 bash


This command starts a Docker container and mounts the model repository directory to the /models directory within the container.


### Step 3: Start the Triton Inference Server
Inside the Docker container, run the following command to start the Triton Inference Server:

tritonserver --model-repository=/models

The server will start and display log output indicating the initialization of different backends (PyTorch, TensorFlow, ONNX Runtime, etc.). Note any warnings or errors that may occur during startup.


### Step 4: Test the Server
To test if the Triton Inference Server is running successfully, open a new terminal window and run the following command:

curl -v http://localhost:8000/v2/models

You should receive a response containing information about the available models in the model repository

# Additional Configuration
* If you have GPU support on your machine, you can use the --gpus all flag when running the Docker command to enable GPU functionality.
* Make sure to specify the correct model repository path in the Docker command and ensure that the model repository directory contains the necessary model files and a config.pbtxt file for each model.
* Refer to the Triton Inference Server documentation for more advanced configuration options and deployment scenarios.


# Contributing
Contributions to this repository are welcome! If you have any suggestions, bug fixes, or improvements, please feel free to submit a pull request.



