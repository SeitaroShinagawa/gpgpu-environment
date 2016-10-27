#restore environment

##[How I do a system restore?](http://askubuntu.com/questions/56095/how-i-do-a-system-restore)  
- [ ] Case1: TimeShift  
- [ ] Case2: manual  

###Case1: [TimeShift](http://www.teejeetech.in/p/timeshift.html)
システム復旧に使えるライブラリ  
保存する環境(Snapshot) はdefaultでroot partitionの`/timeshift`以下に保存される  
CDへの保存も可能。usbへの保存が可能か、また初期化されたOSから修復が可能かどうかは未確認-->出きるっぽい(29 January 2015 at 21:15のcommentの回答より)  
userの保存したドキュメントや画像、音声ファイルはdefaultで保存対象から除外されるので安心して復元できる  

注意点  
1. uninstall前にすべてのSnapshotを消す  
2. Snapshotを保存するのにGUIが必要

How to Install  
```  
#Ubuntu  
sudo apt-get install software-properties-common     #for using add-apt-repository  
sudo apt-add-repository -y ppa:teejee2008/ppa
sudo apt-get update  
sudo apt-get install timeshift  
```  
```
#Others including Debian  

``` 



