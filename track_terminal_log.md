#Track Terminal Log
[[link](http://ja.stackoverflow.com/questions/3216/%E3%82%BF%E3%83%BC%E3%83%9F%E3%83%8A%E3%83%AB%E3%81%AE%E6%93%8D%E4%BD%9C%E3%83%AD%E3%82%B0%E3%82%92%E8%87%AA%E5%8B%95%E3%81%A7%E6%AE%8B%E3%81%97%E3%81%9F%E3%81%84)]  
[[link2](http://dev.classmethod.jp/operation/logging_operation_using_script_and_psacct/)]  
- [x] Process Accounting Utility apt-get install acct  
- [ ] script command 

How to track libraries (when, who installed)  

```
sudo apt-get install acct

#Start watching
/etc/init.d/acct start
#Stop watching
/etc/init.d/acct stop
```
##How to use
###過去に実行が終了したコマンド情報  
```
lastcomm   
例: [-hpV] [-f file] [command] ... [user] ... [terminal] ...  
[--forwards] : 表示を昇順にする(defaultは降順)    
[--file <file>] :   
[--strict-match] : 厳密に一致する文字列に検索を絞る(他のコマンドと一緒に使う)
[--print-controls] :   
[--user <name>] : 特定のユーザのコマンド履歴
[--tty <name>] : 特定の接続の履歴
[--command <name>] : 特定のコマンドに絞った情報
[--debug]
[--show-paging]
```
実行例
```
lastcomm --tty pts/18
lastcomm --strict-match --command vim
```


###接続時間の表示  
```
ac
例: [-dhpVy] [-f <file>] [people]
[--daily-totals] [-d] : 一日ごとの接続時間
[--individual-totals] 
[--file <file>]
[--complain] 
[--reboots] 
[--supplants] 
[--timewarps] 
[--print-year]
[--compatibility]
[--print-zeros]
[--debug]
[--tw-leniency <value>]
[--tw-suspicious <value>]
```
実行例  
```
ac -d -p
```
###サマリー
```
sa
Usage: sa [ options ] [ file ]
options: 
[-abcdfiljkmnprstuDKP]
[-v <num>]
[--version]
[--help]
[--other-acct-file <name>] 
[--other-usracct-file <name>]
[--print-seconds]
[--dont-read-summary-files] 
[--debug]
[--separate-times] 
[--other-savacct-file <name>] 
[--percentages]
[--print-ratio]
[--print-users] : ユーザごとに履歴を表示   
[--merge] 
[--user-summary] : ユーザごとサマリーを表示
[--list-all-names] 
[--not-interactive] 
[--threshold <num>]
[--sort-ksec] 
[--sort-tio] 
[--sort-sys-user-div-calls] 
[--sort-avio]
[--sort-cpu-avmem] 
[--sort-num-calls] 
[--sort-real-time] 
[--ahz hz]
[--show-paging] 
[--show-paging-avg]
```
