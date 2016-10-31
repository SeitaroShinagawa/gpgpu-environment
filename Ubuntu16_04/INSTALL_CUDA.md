#INSTALL CUDA
[CUDA7.5]
1. Install CUDA libraries    
2. Install Nvidia Driver  
[CUDA8.0]
1. Install Nvidia Driver
2. Install CUDA libraries

[ref]:https://devtalk.nvidia.com/default/topic/955414/-solved-how-to-install-titan-x-pascal-driver-on-top-of-cuda-8-/


##Install Nvidia Driver
- [x] Case1: "Add driver" in Software&Update of desktop GUI (Safest but inconvenient from commandline)  
- [x] Case2: Download from Nvidia (Be careful to use)  

###Case2: Download from Nvidia
####1. Select suitable driver-version to your GPGPU  
- The latest is not the best. Check your GPGPU name and find the best choice from [Nvidia](http://www.nvidia.co.jp/Download/index.aspx?lang=en)  
  - Your GPGPU name can be seen by `lspci | grep -i nvidia` or `sudo lshw -c display| grep product`.  
  - e.g.)If you use TeslaK40m, Linux-64bit, you should select 367.55 for CUDA8 or 352.99 for CUDA7.5  
  - e.g.)If you use GeForce GTX TITAN X(900 Series), Linux-64bit, you should select 367.57 for CUDA8 or CUDA7.5  

####2. Install
*Caution!!*  Don't install driver before installing CUDA. Otherwise, your system may be broken.(cause login loop, destroy dependencies, etc.) -> may be only if you install CUDA7.5 with Ubuntu15 or earlier?  
*Caution!!*  Keep your Nvidia-driver. it is necessary for fixing when something wrong happens.  
```
#wGUI means your Ubuntu is Ubuntu desktop or Ubuntu server which already installed ubuntu-desktop  
(wGUI)sudo service lightdm stop  or  sudo stop lightdm  #stop Xserver
(wGUI)sudo init 3                                       #run level stopping X server(Just in case)
sudo chmod 755 NVIDIA-Linux-x86_64-xxx.xx.run           #Nvidia-driver to be exectable  
sudo ./NVIDIA-Linux-x86_64-xxx.xx.run -Z                #-Z: disable noveau
(wGUI)sudo reboot  or  sudo service lightdm start  or  sudo start lightdm  #start your X server
```
You can see other options by `NVIDIA-Linux-x86_64-xxx.xx.run --help` or `NVIDIA-Linux-x86_64-xxx.xx.run -A`(show advanced option)  

##Install CUDA libraries  
- [x] Case1: `sudo apt-get install nvidia-cuda-toolkit (cuda7.5 in Ubuntu16.04)`  
- [x] Case2: Download from Nvidia and use apt-get  
- [x] Case3: Download from Nvidia and use runfile  

*If you use before CUDA7.5, make sure that your gcc version is under 4.9.*  

###Case2: Download from Nvidia and use apt-get
```  
sudo dpkg -i cuda-repo-ubuntu1604-8-0-local_8.0.44-1_amd64.deb`
sudo apt-get update  
sudo apt-get install cuda  
```  
###Case3: Download from Nvidia and use runfile  
CUDA8.0 example is below,  
```
wget https://developer.nvidia.com/compute/cuda/8.0/prod/local_installers/cuda_8.0.44_linux-run  
sudo sh cuda_8.0.44_linux.run
```

##Check the driver and cuda work correctly.  
```
nvidia-smi  
nvcc   
<some code using CUDA>  
```
If you download and use CUDA deb from Nvidia, you can check by deviceQuery.  
```
[CUDA7.5]cd /usr/local/cuda-7.5/bin/cuda-install-samples/NVIDIA_CUDA-7.5_Samples/1_Utilities/deviceQuery/
[CUDA8.0]

make
./deviceQuery
```
*If nvidia-smi fails after rebooting, re-install Nvidia-driver.*  

