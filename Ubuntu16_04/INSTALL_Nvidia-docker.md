#Install Nvidia docker
[nvidia-docker](https://github.com/NVIDIA/nvidia-docker)  

*references*  
- [NVIDIA Dockerで簡単にGPU対応のTensorFlow入りコンテナを作る方法](http://www.muo.jp/2016/05/nvidia-docker-tensorflow.html#2016_05_nvidia-docker-tensorflowfn-requirements)  
- [Ubuntu14.04.3でnvidia-docker使ってCaffeをインストールしてみた](http://qiita.com/daxanya1/items/f04c7f75a6d2ecb92b23)  
- [Docker ドキュメント日本語化プロジェクト](http://docs.docker.jp/index.html)  
- [Dockerコマンドメモ](http://qiita.com/curseoff/items/a9e64ad01d673abb6866)  

##Nvidia dockerの特徴、何が出来るか
- 最低限のgpu環境でインストール可能、Dockerなので自分用のイメージ、コンテナを作って自由に環境構築が可能  
- 最新版のNvidia-driverとCUDAを入れておけばNvidia-docker内で好きなバージョンにダウングレードも可能  
- コンテナ内部からGPUを呼ぶ設定が簡単にできるので手間がかからない  
- 複数マシンでコンテナを共有できる  
- 設定はDockerfile内に記述することで思い通りの環境を作れる  

##注意点  
- 非GPUマシンと混ぜるのは危険?(未検証)  
- 通常のDockerと混ぜるのも危険?(未検証)  

##How to Install
1. Install CUDA,Nvidia-driver
2. Install Docker  
3. Install Nvidia-docker  

##Usage Example  
```
#cuda7.5のイメージを使いnvidia-smiを起動して閉じる  
nvidia-docker run -rm nvidia/cuda:7.5-devel nvidia-smi  
```
See [here](https://github.com/NVIDIA/nvidia-docker/wiki/CUDA) for detail of CUDA version.  



