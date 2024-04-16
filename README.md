# BraTS-Toolkit-Simulator
## Automated tumour segmentation

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

You must have the Brats toolkit installed on your computer and have the python path selected correctly using the SlicerBrianTumorSegmentation, where you have installed the Brats toolkit. 

The extension has been tested on the Intel® Core™ i9-10900X CPU @ 3.70GHz × 20 with an operating System Ubuntu 20.04.2 LTS

# Feature Request
Please open an issue to request any features or changes. 
