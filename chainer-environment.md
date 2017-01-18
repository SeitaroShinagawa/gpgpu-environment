GTX1080でchainer使うときの注意メモ  

1. nvcc error  
```
RuntimeError: `nvcc` command returns non-zero exit status. 
command: ['nvcc', '--cubin', '-arch', 'sm_61', '/tmp/tmpNKaTa0/kern.cu']
return-code: 1
stdout/stderr: 
nvcc fatal   : Value 'sm_61' is not defined for option 'gpu-architecture'
```
https://wyldeplayground.net/cuda-toolkit-8-0-44-on-gtx-1080-under-ubuntu-16-04/  

2. NaN happens on calculating convolution layer  
See cudnn settings, older version cudnns may cause wrong effect.  

