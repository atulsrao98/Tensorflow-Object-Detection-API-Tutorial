# Tensorflow-Object-Detection-API-Tutorial
This repository lists all the steps to install Tensorflow-GPU and hence setup and utilize the Tensorflow Object Detection API on windows without Anaconda.

### ------------------------------------------------------------------------------------------------------------

## INDEX
### •	Tensorflow-gpu installation on Windows 
### •	External Dependencies.
### •	Object Detection Environment Setup

### ------------------------------------------------------------------------------------------------------------

## Tensorflow - GPU Installation 
This Instalation will require the lastest version of Visual Studio Build Tools (C++) and Visual Studio Community at the least

Step 1: Install Nvidia CUDA Toolkit and CUDNN
If Nvidia Geforce Experience is already installed then de select from CUDA toolkit setup
Extract CUDNN files and place in respective folders in CUDA toolkit installation directory

Add directory path to PATH variable under Edit System Variables

1."(CUDA TOOLKIT INSTALLATION DIRECTORY)\CUDA\(VERSION)\bin" <br />
2."(CUDA TOOLKIT INSTALLATION DIRECTORY)\CUDA\(VERSION)\libnvvp" <br />
3."(CUDA TOOLKIT INSTALLATION DIRECTORY)\CUDA\(VERSION)\extras\CUPTI\lib64" <br />
4."(CUDA TOOLKIT INSTALLATION DIRECTORY)\CUDA\(VERSION)\include" <br />

Step 2: Create New Directory Tensorflow and Navigate to Directory <br />
$ cd C:\Tensorflow

Step 3: Setup Python Virtual Enviornment named tf <br />
$ python -m venv tf

Step 4: Activate Enviornment <br />
$ tf\Scripts\activate.bat

Step 5: Verify CUDA installation <br />
$ nvcc --version

Step 6: Install basic libraries <br />
$ pip install numpy <br />
$ pip install pandas <br />
$ pip install matplotlib <br />

List of Installed packages can be seen by <br />
$ pip list

Step 7: Install Tensorflow GPU <br />
$ pip install --upgrade tensorflow-gpu

Step 8: Install Kernel <br />
$ ipython kernel install --user --name=(name of virutualenv)

Step 9: Install Jupyter Notebook <br />
$ pip install jupyterlab

Step 10: Verify Installation <br />
Launch Jupyter Notebook from within the enviornment. Under the new drop down menu select the name of the virtual enviornment.
In the untitled notebook type run the following command.If there are no errors the installation was successful.
$ import tensorflow as tf

### ------------------------------------------------------------------------------------------------------------

## EXTERNAL DEPENDENCIES 

### Vim for Windows
This allows the Unix Vim editor to be utilized from the windows command line. Select the GUI Option from the list. <br />
https://www.vim.org/download.php#pc

### GIT for Windows
This software should allow for easier cloning of github repositories and can be run from within the windows command line. <br />
The Git Bash terminal can also be utilized for running shell scripts. <br />
https://gitforwindows.org/

### ------------------------------------------------------------------------------------------------------------

## OBJECT DETECTION API 

Step 1: Navigate to the Tensorflow Directory <br />
$ cd C:\Tensorflow

Step 2: Activate Virutal Enviornment <br />
$ tf\Scripts\activate.bat

Step 3: Install the following Dependencies <br />
$ pip install Cython <br />
$ pip install contextlib2 <br />
$ pip install Pillow <br />
$ pip install lxml <br />
$ pip install pathlib

Step 4: Navigate into the tf directory <br />
$ cd tf

Step 5: Create a new directory objdetect <br />
$ mkdir objdetect

Step 6: Clone the tensoflow/models repository into /objdetect <br /> 
https://github.com/tensorflow/models <br />
$ git clone https://github.com/tensorflow/models.git

Step 7: Download the latest version of the protobuf compiler <br />
https://github.com/protocolbuffers/protobuf/releases <br />
Extract the zip file. Rename the folder to protoc and place it in C:\ <br />
The file that we need is protoc.exe present within the bin folder

Step 8: Navigate to /models/research and clone the COCOAPI <br />  
https://github.com/cocodataset/cocoapi <br />
$ git clone https://github.com/cocodataset/cocoapi.git

Step 9: Execute protoc.exe from within /models/research <br />
$ C:\protoc\bin\protoc object_detection/protos/*.proto --python_out=.
<br />
The first part of the command should contain the path to the protoc folder created in Step 7. <br />
Only if the full path is specified will there be no errors

Step 10: Navigate into /models/research and execute the following. <br />
This is done to avoid the error object_detection is not recognized <br />
$ python setup.py install

Step 11: Navigate into /models/research/object_detection and run Jupyter Notebook <br />

Step 12: Open the file object_detection_tutorial.ipynb <br />
The following steps will detail the changes that need to be made to the specific file <br />

### 1. Load Label Map Section
Comment out the line that assigns the path to a variable. <br />
Replace the first attribute in the create_category_index_from_labelmap() method with the complete path to the file mscoco_label_map.pbtxt.

It should look something like this: <br />
category_index = label_map_util.create_category_index_from_labelmap('C:/Tensorflow/tf/objdetect/models/research/object_detection/data/mscoco_label_map.pbtxt', use_display_name=True)

### 2. Test Images Path
This is the section just below the Load Label Map Section. <br />
At the begining of the cell add <br />
$ import pathlib <br />
As in the previous step 'PATH_TO_TEST_IMAGES_DIR' should contain the full path to the test images directory <br />

It should look something like this : <br />
PATH_TO_TEST_IMAGES_DIR = pathlib.Path('C:/Tensorflow/tf/objdetect/models/research/object_detection/test_images')

### ------------------------------------------------------------------------------------------------------------

## OUTPUT

![download (1)](https://user-images.githubusercontent.com/40848327/75218850-45d34600-57c1-11ea-829d-8fa9d1026c8b.png)
