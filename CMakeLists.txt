cmake_minimum_required(VERSION 3.16.3...3.19.7 FATAL_ERROR)

project(BatchBrainMRTumorSegmentation)

#-----------------------------------------------------------------------------
# Extension meta-information
set(EXTENSION_HOMEPAGE "https://github.com/UWA-Medical-Physics/SlicerBatchBrainMRTumorSegmentation")
set(EXTENSION_CATEGORY "Segmentation")
set(EXTENSION_CONTRIBUTORS "Saima Safdar (The University of Western Australia)")
set(EXTENSION_DESCRIPTION "Automatic batch brain tumour segmentation")
set(EXTENSION_ICONURL "https://github.com/UWA-Medical-Physics/SlicerBatchBrainMRTumorSegmentation/blob/main/BatchBrainMRTumorSegmentation.png")
set(EXTENSION_SCREENSHOTURLS "https://github.com/UWA-Medical-Physics/SlicerBatchBrainMRTumorSegmentation/blob/main/Screenshot%20from%202024-02-06%2012-11-03.png")
set(EXTENSION_DEPENDS "NA") # Specified as a list or "NA" if no dependencies

#-----------------------------------------------------------------------------
# Extension dependencies
find_package(Slicer REQUIRED)
include(${Slicer_USE_FILE})

#-----------------------------------------------------------------------------
# Extension modules
## NEXT_MODULE
add_subdirectory(BatchBrainMRTumorSegmentation)

#-----------------------------------------------------------------------------
include(${Slicer_EXTENSION_GENERATE_CONFIG})
include(${Slicer_EXTENSION_CPACK})
