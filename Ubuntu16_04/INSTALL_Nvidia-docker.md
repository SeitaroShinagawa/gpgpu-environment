#Install Nvidia docker
[nvidia-docker](https://github.com/NVIDIA/nvidia-docker)  

*references*  
- [NVIDIA Dockerで簡単にGPU対応のTensorFlow入りコンテナを作る方法](http://www.muo.jp/2016/05/nvidia-docker-tensorflow.html#2016_05_nvidia-docker-tensorflowfn-requirements)  
- [Ubuntu14.04.3でnvidia-docker使ってCaffeをインストールしてみた](http://qiita.com/daxanya1/items/f04c7f75a6d2ecb92b23)  
- [Docker ドキュメント日本語化プロジェクト](http://docs.docker.jp/index.html)  
- [Dockerコマンドメモ](http://qiita.com/curseoff/items/a9e64ad01d673abb6866)  
- [DockerでPythonの実行環境を作ったメモ](http://www.mwsoft.jp/programming/numpy/docker.html)  
- ([Dockerチートシート～便利で使えるコマンドまとめました～](https://academy.gmocloud.com/docker/20151126/911))  

  

##Nvidia dockerの特徴、何が出来るか
- 最低限のgpu環境でインストール可能、Dockerなので自分用のイメージ、コンテナを作って自由に環境構築が可能  
- 最新版のNvidia-driverとCUDAを入れておけばNvidia-docker内で好きなバージョンにダウングレードも可能  
- コンテナ内部からGPUを呼ぶ設定が簡単にできるので手間がかからない  
- 複数マシンでコンテナを共有できる  
- 設定はDockerfile内に記述することで思い通りの環境を作れる  

##注意点  
- 非GPUマシンと混ぜるのは危険?(未検証)  
- 通常のDockerと混ぜるのも危険?(未検証)  
- Docker groupメンバーはsudoメンバーである必要がある可能性がある(未検証)  

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

##Others
- DockerはDockerfileから読み込専用のImageをつくり、Imageからコンテナを作る。コンテナをImage化することも可能。コンテナをtarファイルにexportすることも可能。  
- Imageは親Imageの上に子Imageを作成可能。(pyenvでいうvirtualenvが可能)  
- Dockerは原則sudoが無いと使えないが、docker groupを作成し、各ユーザをグループに追加すればsudoなしでDocker daemonが起動できる(Nvidia-dockerは未検証)  
  - [ ] Imageの削除permissionの付与が可能かどうか確認  
  - [ ] containerの操作のpermisshonの付与が可能かどうか確認  

##Under Consideration
- Dockerとメモリ消費について[link](http://stackoverflow.com/questions/24702233/docker-container-and-memory-consumption)  
Q. 同じImageから大量のコンテナを起動した場合、膨大なハードドライブ容量が必要になるだろうが、Dockerはこれをどう処理しているのか?Imageと変更がない静的部分はImage内の容量をshareしている形になるのか?  
A. Dockerはkernel levelでリソースを共有している(リンク先の図を参照) 100個同じ処理を行いそれぞれ保存すると100倍のリソースを食う。アプリも同様に同時に起動すれば100倍のRAMを食う。  

- Dockerのメモリ消費の表示について[link](https://github.com/docker/docker/issues/10824)  
解決済みのようだが未読  

-  



