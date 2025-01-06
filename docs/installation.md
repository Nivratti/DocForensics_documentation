# Installation process of Document Forensics Project

This page will guide you through the initial setup and installation process to get the Document Forensics Project up and running on your machine.

## Prerequisites:

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
    - Nvidia container toolkit: [installation](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)

- **Others:**
     - Stable internet connection for cloning the repository and downloading dependencies.
     - Access to a terminal or command prompt.
    
Ensure that your machine meets the above specifications to ensure smooth operation of the Document Forensics Project.


## Installation Guide:

This guide provides detailed instructions on how to set up the Document Forensics Project on your machine. You can choose to set up the project on a CPU or a GPU, though a GPU setup is recommended due to its advantages in speeding up predictions.

1. **Clone the Repository**:
   Clone the project repository to your local machine using the following command:
   
   ```bash
   git clone https://github.com/Nivratti/DocForensics_Mauritius_Inference.git
   cd DocForensics_Mauritius_Inference
   ```

### GPU Setup (Recommended):

There are two distinct methods available for setting up the project on a GPU: Docker and Docker Compose. You can opt for any of these methods depending on your preferences or the specifics of your environment setup.

- i) [Docker Setup:](#docker-setup)
- ii) [Docker Compose Setup](#docker-compose-setup)
  
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

### CPU Setup:

There are two methods available for setting up the project on a CPU: Docker and Docker Compose. You can opt for any of these methods depending on your preferences or the specifics of your environment setup.

- i) [Docker Setup On CPU:](#docker-setup-on-cpu)
- ii) [Docker Compose Setup On CPU](#docker-compose-setup-on-cpu)

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

## Initial Configuration:

No initial configuration is required to get started with the Document Forensics Project. Once the installation steps are completed, you can begin using the system to analyze digital documents for forensic purposes.

Feel free to explore the project documentation further to understand the various features and functionalities available within the Document Forensics Project.