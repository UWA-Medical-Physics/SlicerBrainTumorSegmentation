# BraTS-Toolkit-Simulator
Automated tumour segmentation
This python scripted 3D Slicer module integrates the BraTS-Toolkit for automatically segmenting the brain tumour for user provided number of patients (as many as user required) 
in a folder. Furthermore, it computes the inverse transform to transform the Brat space segmentation result back to original T1-MRI space. This allows to align the segmentation 
results with the original data for quantitative evaluation. The segmentation is based on the following four imaging modalities:

    T1-MRI
    3D Flair
    Contrast MRI
    T2-MRI

What it is and what it can be used for? Its an interface to the BraTS-Toolkit to automate image analysis and tumour segmentation workflow.

