# This toolkit has been updated according to comments from Slicer Community. The  new link to the toolkit is https://github.com/UWA-Medical-Physics/SlicerBrats
# BraTS-Toolkit-Simulator
## Automated tumour segmentation

Note: Please mention and cite the extesnion github page if you use any part of the extension code. Thank you.

This python scripted 3D Slicer module integrates the BraTS-Toolkit for automatically segmenting the brain tumour for user provided number of patients (as many as user required) 
in a folder. Furthermore, it computes the inverse transform to transform the Brat space segmentation result back to original T1-MRI space. This allows to align the segmentation 
results with the original data for quantitative evaluation. The segmentation is based on the following four imaging modalities:

    T1-MRI
    3D Flair
    Contrast MRI
    T2-MRI

What it is and what it can be used for? Its an interface to the BraTS-Toolkit to automate image analysis and tumour segmentation workflow.

![Screenshot from 2024-02-06 12-11-03](https://github.com/saimasafdar2021/SlicerBrainTumorSegmentation/assets/80670821/293f8fc6-8dcb-42da-81f6-57f5561ba9e4)

# Tutorial 

1) Path to the external Python: Users specify the location where the BraTs Toolkit, a crucial component of the program, will be installed. This step ensures seamless integration with the desired Python environment.

2) Path to data directory: Users must provide the path to the directory containing patients' data in NifTI format. Within this directory, individual patient data folders are present, each comprising the following essential images, including (a) T1-weighted magnetic resonance imaging (MRI), (b) T2-weighted MRI, (c) T2 fluid attenuated inversion recovery (FLAIR), and (d) T1-weighted contrast-enhanced MRI (T1c). These images form the foundation for subsequent processing.

3) Patient ID: To accurately track processed patient data within the provided data folder, users input a unique patient identifier. This identifier enables the software to organize and associate the processed data with the respective patient.

4) Select neural network models: Users can choose from a list of trained neural network models. The flexibility to select multiple models and incorporate new available models into the list. This feature empowers users to tailor the program's analysis to their specific requirements and leverage the latest advancements in neural network models.

![s5](https://github.com/UWA-Medical-Physics/SlicerBrainTumorSegmentation/assets/80670821/018d95f7-74e1-444a-9390-4bb6f6b865e9)

How to run?
The program requires specific inputs to execute its functionality effectively. These inputs include:

1)	Path to the external Python: This parameter defines the location where the BraTs Toolkit is installed. 
This is the Path to the external Python installed on the user computer that contains the installation of the BraTS-Toolkit.
Or this path is required to install the BraTS-Toolkit.

2)	Path to data directory: Users must provide the path to the directory containing the patients' data.
Within this directory, individual patient data folders are present, with each folder comprising the following essential images: 
(a) T1-weighted magnetic resonance imaging (MRI), (b) T2-weighted MRI, (c) FLAIR, and (d) contrast-enhanced MRI. 

3)	Patient ID: To track patients data.

4)	Select neural network models: This input allows users to choose from a list of trained neural network models. 
Users have the flexibility to select multiple models and even incorporate new available models into the list. 

What are the outputs?
Outputs are the segmentation files for each patient data. The segmentation is performed based on the selected number of neural networks. In the fusion part of the 
program all the segmentations from the individual neural networks are combined based on majority voting and iterative SIMPLE fusion to generate consensus segmentations.
These segmentations are converted to original MRI data space to get the transformed segmentations so that the tumour segmentation results can be viewed on the original 
MRI data. 

Publication: to be added soon

License: Apache 2.0. 

# Installation
Pre-requisites installation:
For Brats-toolkit installation, pease follow the link below:

Further, NVIDIA Docker Toolkit needs to be installed (installation instructions here: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker and here: https://neuronflow.github.io/BraTS-Preprocessor/#dockerinstallation ).
https://github.com/neuronflow/BraTS-Toolkit

First install the NVIDIA toolkit container with the apt commands
https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#configuration

### Installing with Apt

Configure the production repository:

    curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
      && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
        sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
        sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list

Optionally, configure the repository to use experimental packages:

    sed -i -e '/experimental/ s/^#//g' /etc/apt/sources.list.d/nvidia-container-toolkit.list

Update the packages list from the repository:

    sudo apt-get update

Install the NVIDIA Container Toolkit packages:

    sudo apt-get install -y nvidia-container-toolkit

After that install Docker
https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

Install using the apt repository

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

Set up Docker's apt repository.

### Add Docker's official GPG key:
    
    sudo apt-get update
    
    sudo apt-get install ca-certificates curl
    
    sudo install -m 0755 -d /etc/apt/keyrings
    
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    
    sudo chmod a+r /etc/apt/keyrings/docker.asc

### Add the repository to Apt sources:
    echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
      $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    
    sudo apt-get update

Install the Docker packages.

To install the latest version, run:

     sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

Verify that the Docker Engine installation is successful by running the hello-world image.

     sudo docker run hello-world

This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.

You have now successfully installed and started Docker Engine.

Finally check NVIDIA-smi using
    
        sudo docker run --rm --runtime=nvidia --gpus all ubuntu nvidia-smi


Use the following link to resolve any issues with the docker installation
https://forums.developer.nvidia.com/t/nvida-container-toolkit-failed-to-initialize-nvml-unknown-error/286219/2

After this, you have to make the docker run without sudo, for that follow the https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user  

https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user

To create the docker group and add your user:

Create the docker group.

    sudo groupadd docker

Add your user to the docker group.

    sudo usermod -aG docker $USER

Log out and log back in so that your group membership is re-evaluated.

If you're running Linux in a virtual machine, it may be necessary to restart the virtual machine for changes to take effect.

You can also run the following command to activate the changes to groups:

     newgrp docker

Verify that you can run docker commands without sudo.

     docker run hello-world

You must have the Brats toolkit installed on your computer and have the python path selected correctly using the SlicerBrianTumorSegmentation, where you have installed the Brats toolkit. 

The extension has been tested on the Intel® Core™ i9-10900X CPU @ 3.70GHz × 20 with an operating System Ubuntu 20.04.2 LTS

# Feature Request
Please open an issue to request any features or changes. 
