#restore environment

##[How I do a system restore?](http://askubuntu.com/questions/56095/how-i-do-a-system-restore)  
- [ ] Case1: TimeShift  
- [ ] Case2: Manual  

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
#Others(including Debian)
wget http://dl.dropbox.com/u/67740416/linux/timeshift-latest-i386.run (32-bit)
wget http://dl.dropbox.com/u/67740416/linux/timeshift-latest-amd64.run (64-bit)
``` 

###Case1-2: Systemback
[intro-ja](http://gihyo.jp/admin/serial/01/ubuntu-recipe/0402)  
[detail-en](https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/)  
GUIでもCLIでも使える  

CLIは簡単な設定、保存時はすべてのフォルダの内容を保存する(つまりそれだけメモリを食う)  
外部のファイルシステムとつながっている場合、おそらく保存するときは一度アンマウントする必要がある(2016.11.02確認、外部のファイルシステムについては自動で除外してくれるので気兼ねなく使える)  
```
#Install
sudo add-apt-repository -y ppa:nemh/systemback  #add-apt-repositoryがなければ↑のTimeShiftを参考に追加  
sudo apt-get update  
sudo apt-get install systemback  
(CUI) sudo apt-get install systemback-cli  
```
```
#Execution  
(GUI) find & click icon of systemback  
(CLI) sudo systemback-cli
```
###Case2: Manual
Add if Case1 failed  

###Case3: Simple Backup(SBackup)  
file backup  
save package list    
[[link](http://gihyo.jp/admin/serial/01/ubuntu-recipe/0004?page=3)]  

###Case4: dd
save full HDD image  

###Case5: Deja Dup


