# Getting Started with Document Forensics Project

This page will guide you through the initial setup and installation process to get the Document Forensics Project up and running on your machine.

## Prerequisites

Before proceeding with the installation, ensure you have the following prerequisites met on your machine:

- **Operating System**: 
    - Linux (Ubuntu 18.04 LTS or later is recommended)
    - macOS (10.14 Mojave or later)
    - Windows 10 Pro, Enterprise or Education (64-bit, Build 15063 or later)

- **Hardware**:
    - **CPU**: At least 4 cores
    - **RAM**: 12 GB or more
    - **Disk Space**: 50 GB or more of free space
    - **GPU**: A modern nvidia GPU with memory > 12 GB is recommended to provide a significant speedup in predictions.
  
- **Software**:
    - Docker: Follow the [official Docker installation guide](https://docs.docker.com/get-docker/) to install Docker on your machine.
    - Docker Compose: Follow the [official Docker Compose installation guide](https://docs.docker.com/compose/install/) to install Docker Compose on your machine.
    - GPU driver: If you are setting up project on nvidia gpu, then driver version >= 525 will be required.

- **Others:**
     - Stable internet connection for cloning the repository and downloading dependencies.
     - Access to a terminal or command prompt.
    
Ensure that your machine meets the above specifications to ensure smooth operation of the Document Forensics Project.


## Installation Guide

This guide provides detailed instructions on how to set up the Document Forensics Project on your machine. You can choose to set up the project on a CPU or a GPU, though a GPU setup is recommended due to its advantages in speeding up predictions.

1. **Clone the Repository**:
   Clone the project repository to your local machine using the following command:
   
   ```bash
   git clone https://github.com/Nivratti/DocForensics_Mauritius_Inference.git
   cd DocForensics_Mauritius_Inference
   ```

### GPU Setup (Recommended)

There are three distinct methods available for setting up the project on a GPU: Docker, Docker Compose, and using the `setup.sh` script. You can opt for any of these methods depending on your preferences or the specifics of your environment setup.

- i) [Docker Setup:](#docker-setup)
- ii) [Docker Compose Setup](#docker-compose-setup)
- iii) [Script Setup](#script-setup)
  
#### Docker Setup:
This guide provides instructions on setting up the Document Forensics Project on a GPU using Docker.

   1. **Build the Docker Image**:
   
      In the project directory, you'll find a file named `Dockerfile`. This file contains the instructions to build the Docker image for the GPU setup. Build the Docker image using the following command:

      ```bash
      docker build -t docforensics_mauritius_inference:latest .
      ```

   2. **Run the Docker Container**:
      Now, run the Docker container from the image you just built. This will start the Document Forensics Project on your machine:

      ```bash
      docker run --name docforensics_mauritius_inference -p 6003:6003 docforensics_mauritius_inference:latest
      ```

   3. **Accessing the Project**:
      Once the Docker container is up and running, you can access the Document Forensics Project through your web browser using the URL: `http://localhost:6003`

   4. **Stopping the Project**:
      To stop the Document Forensics Project and the running container, use the following command:
      ```bash
      docker stop docforensics_mauritius_inference
      ```

#### Docker Compose Setup

Docker Compose facilitates the management of multi-container Docker applications, making it a convenient method for setting up the Document Forensics Project on a GPU. Here's how to proceed:

1. **Prepare the Docker Compose File**:
   Ensure you have a `docker-compose.yml` file in the project directory. The file should have the content as provided above, tailored to the specifics of the Document Forensics Project and GPU setup.

2. **Build the Docker Images**:
   Navigate to the project directory where the `docker-compose.yml` file is located, and execute the following command to build the Docker images:
   ```bash
   sudo docker-compose build
   ```

3. **Start the Docker Containers**:
   Now, start the Docker containers using the following command:
   ```bash
   sudo docker-compose up
   ```

4. **Accessing the Project**:
   Once the Docker containers are up and running, access the Document Forensics Project through your web browser using the URL: `http://localhost:6003`


5. **Stopping the Project**:
   To stop the Document Forensics Project and the running containers, use the following command:
   ```bash
   sudo docker-compose down
   ```

These steps outline the procedure for setting up and managing the Document Forensics Project on a GPU using Docker Compose.

#### Script Setup

The `setup.sh` script is a straightforward method to set up the Document Forensics Project on a GPU. This script will create a new Conda environment and install all the necessary dependencies. Ensure you have Anaconda installed on your system before proceeding.

1. **Run the Setup Script**:
   Make the script executable and run it to set up the project:
   ```bash
   chmod +x setup.sh
   ./setup.sh
   ```

2. **Activate the Conda Environment**:
   Once the script execution completes, activate the new Conda environment created by the script:
   ```bash
   conda activate document-forensics-gpu
   ```

3. **Start the Project**:
   Now, with the Conda environment activated, start the Document Forensics Project:
   ```bash
   python main.py
   ```

4. **Accessing the Project**:
   Once the project is up and running, access it through your web browser using the URL: `http://localhost:6003`

5. **Stopping the Project**:
   To stop the Document Forensics Project, simply terminate the running process in the terminal using `Ctrl + C`.

6. **Deactivate the Conda Environment**:
   After stopping the project, deactivate the Conda environment:
   ```bash
   conda deactivate
   ```

These steps outline the process to set up the Document Forensics Project on a GPU using the `setup.sh` script. This method requires Anaconda to be installed on the system, as it relies on Conda environments to manage dependencies.
```

In this section, a step-by-step procedure is provided to set up the Document Forensics Project on a GPU using the `setup.sh` script. It includes making the script executable, running it, activating the newly created Conda environment, starting the project, and how to access, stop, and deactivate the environment post usage.


### CPU Setup

There are three distinct methods available for setting up the project on a CPU: Docker, Docker Compose, and using the `setup_cpu.sh` script. You can opt for any of these methods depending on your preferences or the specifics of your environment setup.

- i) [Docker Setup On CPU:](#docker-setup-on-cpu)
- ii) [Docker Compose Setup On CPU](#docker-compose-setup-on-cpu)
- iii) [Script Setup On CPU](#script-setup-on-cpu)

#### Docker Setup On CPU:
This guide provides instructions on setting up the Document Forensics Project on a CPU using Docker.

1. **Build the Docker Image**:

    In the project directory, you'll find a file named `Dockerfile-cpu`. This file contains the instructions to build the Docker image for the CPU setup. Build the Docker image using the following command:

    ```bash
    sudo docker build -f "Dockerfile-cpu" -t docforensics_mauritius_inference_cpu:latest .
    ```

2. **Run the Docker Container**:
    Now, run the Docker container from the image you just built. This will start the Document Forensics Project on your machine:

    ```bash
    sudo docker run --name docforensics_mauritius_inference_cpu -p 6003:6003 docforensics_mauritius_inference_cpu:latest
    ```

3. **Accessing the Project**:
    Once the Docker container is up and running, you can access the Document Forensics Project through your web browser using the URL: `http://localhost:6003`

4. **Stopping the Project**:
    To stop the Document Forensics Project and the running container, use the following command:
    
    ```bash
    sudo docker stop docforensics_mauritius_inference_cpu
    ```

#### Docker Compose Setup On CPU

Docker Compose facilitates the management of multi-container Docker applications, making it a convenient method for setting up the Document Forensics Project on a CPU. Here's how to proceed:

1. **Prepare the Docker Compose File**:
    Ensure you have a `docker-compose-cpu.yml` file in the project directory. The file should have the content as provided above, tailored to the specifics of the Document Forensics Project and CPU setup.

2. **Build the Docker Images**:
    Navigate to the project directory where the `docker-compose-cpu.yml` file is located, and execute the following command to build the Docker images:
    
    ```bash
    sudo docker compose -f "docker-compose-cpu.yml" build
    ```

3. **Start the Docker Containers**:
    Now, start the Docker containers using the following command:
    
    ```bash
    sudo docker compose -f "docker-compose-cpu.yml" up
    ```

4. **Accessing the Project**:
    Once the Docker containers are up and running, access the Document Forensics Project through your web browser using the URL: `http://localhost:6003`

5. **Stopping the Project**:
    To stop the Document Forensics Project and the running containers, use the following command:
    
    ```bash
    sudo docker compose -f "docker-compose-cpu.yml" down
    ```

#### Script Setup On CPU

The `setup_cpu.sh` script is a straightforward method to set up the Document Forensics Project on a CPU. This script will create a new Conda environment and install all the necessary dependencies. Ensure you have Anaconda installed on your system before proceeding.

1. **Run the Setup Script**:
    Make the script executable and run it to set up the project:
    
    ```bash
    chmod +x setup_cpu.sh
    ./setup_cpu.sh
    ```

2. **Activate the Conda Environment**:
    Once the script execution completes, activate the new Conda environment created by the script:
    
    ```bash
    conda activate document-forensics-cpu
    ```

3. **Start the Project**:
    Now, with the Conda environment activated, start the Document Forensics Project:
    
    ```bash
    python main.py
    ```

4. **Accessing the Project**:
    Once the project is up and running, access it through your web browser using the URL: `http://localhost:6003`

5. **Stopping the Project**:
    To stop the Document Forensics Project, simply terminate the running process in the terminal using `Ctrl + C`.

6. **Deactivate the Conda Environment**:
    After stopping the project, deactivate the Conda environment:
    
    ```bash
    conda deactivate
    ```

These steps outline the process to set up the Document Forensics Project on a CPU using the `setup_cpu.sh` script. This method requires Anaconda to be installed on the system, as it relies on Conda environments to manage dependencies.
