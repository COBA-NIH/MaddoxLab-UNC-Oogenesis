# C. elegans oogenesis segmentation project

# Notes from a CellProfiler-based approach, July 2021

### Overview:
The goal of this project is to create a workflow to accurately segment C. elegans oocytes.

The images are challenging to segment, as there is no nuclear stain and the cells are defined by bright staining at the borders. In addition, these are 3-dimensional images requiring 3D segmentation.

I attempted to create a solution using ilastik to generate a pixel classifier and then to segment using the ilastik probabilities in CellProfiler. Using this approach, I was unable to create a high quality segmentation. The cells are different size, and it was hard to accurately segment and declump the small and large cells.

### Table of contents for each directory

##### CellProfiler-ilastikSegmentation
- **SaveAsTiff.cppipe**: pipeline used to import the original .nd2 images and export .tiff files for each channel
- **ilastik-segmentation.cppipe**: the pipeline used by Pearl for her best quality segmentation. They use the original images + ilastik predictions. You will need the declumpobjects.py plugin to run this pipeline.
- **oocyte-training.ilp**: ilastik project used to predict different regions of the image (background, out-of-focus light, cell interior, cell border)

##### cellprofiler-pipelines
- **SaveAsTiff.cppipe**: pipeline used to import the original .nd2 images and export .tiff files for each channel
- **Segmentation.cppipe**:  Attempt to segment the original images directly (without using ilastik)

##### cellprofiler-plugins
The declumpobjects.py plugin used for this project.
