#INSTALL CUDA
1. Install CUDA libraries    
2. Install Nvidia Driver  

##Install CUDA libraries
- [x] Case1: `sudo apt-get install nvidia-cuda-toolkit (cuda7.5 in Ubuntu16.04)`  
- [x] Case2: Download from Nvidia  

If you use before CUDA8.0, make sure that your gcc version is under 4.9.  

##Install Nvidia Driver
- [x] Case1: "Add driver" in Software&Update of desktop GUI (Safest but inconvenient from commandline)  
- [x] Case2: Download from Nvidia (Be careful to use)  

###Case2: Download from Nvidia
####1. Select suitable driver-version to your GPGPU  
- The latest is not the best. Check your GPGPU name and find the best choice from [Nvidia](http://www.nvidia.co.jp/Download/index.aspx?lang=en)  
  - Your GPGPU name can be seen by `lspci | grep -i nvidia` or `sudo lshw -c display| grep product`.  
  - e.g.)If you use TeslaK40m, Linux-64bit, you should select 367.55 for CUDA8 or 352.99 for CUDA7.5  
  - e.g.)If you use GeForce xxxxx Series GTX TITAN, Linux-64bit, you should select xxx.xx for CUDA8 or xxx.xx for CUDA7.5(add later...)  

####2. Install
*Caution!!*  Don't install driver before installing CUDA. Otherwise, your system may be broken.(cause login loop, destroy dependencies, etc.)  
*Caution!!*  Keep your Nvidia-driver. it is necessary for fixing when something wrong happens.  
```
sudo chmod 755 NVIDIA-Linux-x86_64-xxx.xx.run
sudo ./NVIDIA-Linux-x86_64-xxx.xx.run -Z
```
-Z option is to disable nouveau.  
You can see other options by `--help` or `-A`(show advanced option)  

Check the driver and cuda work correctly.  
```
nvidia-smi  
nvcc   
<some code using CUDA>  
```
If you download and use CUDA deb from Nvidia, you can check by deviceQuery.  
```
cd /usr/local/cuda-7.5/bin/cuda-install-samples/NVIDIA_CUDA-7.5_Samples/1_Utilities/deviceQuery/
make
./deviceQuery
```
*If nvidia-smi fails after rebooting, re-install Nvidia-driver.*  

