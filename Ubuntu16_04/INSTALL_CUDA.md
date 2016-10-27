#INSTALL CUDA
1. Install CUDA libraries    
2. Install Nvidia Driver  

##Install CUDA libraries
- [x] Case1: `sudo apt-get install nvidia-cuda-toolkit (cuda7.5 in Ubuntu16.04)`  
- [x] Case2: Download from Nvidia  

##Install Nvidia Driver
- [x] Case1: "Add driver" in Software&Update of desktop GUI (Safest but inconvenient from commandline)  
- [x] Case2: Download from Nvidia (Be careful to use)  

###Case2: Download from Nvidia
####1. Select suitable driver-version to your GPGPU  
Latest is not the best. Check your GPGPU name and find the best choice from [Nvidia](http://www.nvidia.co.jp/Download/index.aspx?lang=en)  

How to show your GPGPU  
```
lspci | grep -i nvidia
```
or  
```
sudo lshw -c display| grep product
```

