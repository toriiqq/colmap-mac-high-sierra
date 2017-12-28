# colmap-mac-high-sierra
This is how to setup colmap-cuda on macOS high sierra.

## Mac, OS and GPU
macbook pro 13-inch, 2016, four thunderbolt 3 ports  
macOS high sierra 10.13.2  
sonnet eGFX Breakaway Box GPU-350W-TB3Z  
nvidia geforce 1080ti  

## Setup NVIDA driver and CUDA toolkit

#### Install NVIDIA web drivers and setup egpu.  
[https://egpu.io/forums/mac-setup/wip-nvidia-egpu-support-for-high-sierra/](https://egpu.io/forums/mac-setup/wip-nvidia-egpu-support-for-high-sierra/)


#### Install CUDA Toolkit 9.1
Download and install  
[https://developer.nvidia.com/cuda-toolkit](https://developer.nvidia.com/cuda-toolkit)

#### Add paths in .bashrc      
    export PATH="/Developer/NVIDIA/CUDA-9.1/bin:$PATH"  
    export LD_LIBRARY_PATH="/Developer/NVIDIA/CUDA-9.1/lib:$LD_LIBRARY_PATH"  

    
## Install Command Line Tools for Xcode 8.3.2 

[https://developer.apple.com/download/more/](https://developer.apple.com/download/more/)  
(apple developer id required)  

#### Open terminal, 
    sudo xcode-select -s /Library/Developer/CommandLineTools
% After all the installation, you can put back to the latest CLT by `sudo xcode-select -r`
 
## Setup COLMAP

#### Install ceres
[http://ceres-solver.org/installation.html](http://ceres-solver.org/installation.html)  
see also 
[https://colmap.github.io/install.html](https://colmap.github.io/install.html)

#### Install COLMAP
https://colmap.github.io/install.html

    git clone https://github.com/colmap/colmap
    cd colmap

Comment out gpu_mat_test.cu in `src/mvs/CMakeLists.txt` (L46 in colmap3.3). See also, [https://github.com/colmap/colmap/issues/36](https://github.com/colmap/colmap/issues/36)

With this build, your colmap works great when GPU is on but won’t work without. 


## Computation time

#### Gerrard Hall (100 images)
[https://drive.google.com/open?id=0B6q7-Pen0AbDNHBPblFHQUpEdFU](https://drive.google.com/open?id=0B6q7-Pen0AbDNHBPblFHQUpEdFU)

feature extraction 0.6 min  
feature matching (exhaustive) 3.7 min  
reconstruction 7.5 min  
stereo 92 min  
fuse 5 min  
