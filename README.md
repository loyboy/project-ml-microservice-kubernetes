[![loyboy](https://circleci.com/gh/loyboy/project-ml-microservice-kubernetes.svg?style=svg)](https://app.circleci.com/pipelines/github/loyboy/project-ml-microservice-kubernetes)

## Project Overview

In this project, I have applied the skills I had acquired in this course to operationalize a Machine Learning Microservice API. 

I was given an all-ready made pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project is testing my ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

My project goal was to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project I was able to:
* Test the project code using linting
* Complete a Dockerfile to containerize this application
* Deploy the containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Uploaded the complete Github repo with CircleCI config file to indicate that my code has been tested

---

## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running the Python App through `app.py` , in three different ways

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Make a prediction

After Running `app.py`, make a prediction using a separate terminal tab within your linux/Mac OS, and make a call to the `./make_prediction.sh` file

## Files in the repository

- [.circleci/config.yml](.circleci/config.yml): CircleCI configuration for this project
- [model_data](model_data), [app.py](app.py), [requirements.txt](requirements.txt): Flask app files
- [Makefile](Makefile): includes python related instructions on environment setup and lint tests
- [Dockerfile](Dockerfile): includes docker related instructions to assemble the Docker image
- [run_docker.sh](run_docker.sh): Builds the docker image and runs the containerized Flask app
- [upload_docker.sh](upload_docker.sh): This tags and pushes image to your personal Docker account repository in the cloud
- [run_kubernetes.sh](run_kubernetes.sh): Deploy the Flask app to the Kubernetes Cluster, and forward the container port (80) to a host port (8000)
- [make_prediction.sh](make_prediction.sh): Send a request to the deployed Flask app to make a prediction within the localhost
- [output_txt_files/docker_out.txt](output_txt_files/docker_out.txt): Output after running a prediction via Docker deployment
- [output_txt_files/kubernetes_out.txt](output_txt_files/kubernetes_out.txt): Output after running a prediction via Kubernetes deployment

