### 三大虛擬機

* Virtual Box

* VMware

    * player:免費版，沒有快照功能
  
    * workstation:商用版，需花錢購買，功能較完善
  
    * 原為Oracle公司,後被Red Hat收購,隨後被IBM收購
  
* Hyper-V

### 終端機指令
- windows:

    - `ipconfig /all` : 查看網路卡資訊

    - `netstat -rn` : 查看網路卡資訊
    
    - `netstat -an` : 查看實體機上哪些埠被打開
- Linux:

    - `echo` : 反映指令, 打什麼就傳回什麼
    
    - `echo hello (在此省略"1") > Desktop/1.txt` : 建立內文為hello的文本
    
    - `Desktop/1.txt`:
    
        * 若文字檔存在:清空內容
        
        * 若文字檔不存在:建立文字檔
    
    - `ifconfig` : 查看網路卡資訊
    
    - 關機3法
    
      - `reboot` : 重啟
    
      - `halt-p`:p-pause
    
      - `power off`
      
      - `shutdown`
    
    - `su` : 切換為系統管理員(在Linux中為`root`,提示符號為 `#`,若身分為`user`則為 `$`)
    
    - `yum install` : 安裝軟體指令
    
    - `systemctrl stop 伺服器名稱(E.g.ssh)d` : 關閉伺服器
    
    - `systemctrl stop 伺服器名稱(E.g.ssh)d` : 啟動伺服器
    
    - `systemctrl status 伺服器名稱(E.g.ssh)d` : 檢查伺服器狀態
    
    - `netstat -tulnp | grep 22` :
      
      - `t`: 檢查TCP連線
      
      - `u`: 檢查UDP連線
      
      - `l`: Listen
      
      - `n` : 不解析
      
      - `p` : process ID
      
      - `grep` : 過濾器
    
    
### Linux網路卡命名

![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/%E7%B6%B2%E8%B7%AF%E5%8D%A1%E5%91%BD%E5%90%8D.jpg)

### 遠端桌面連線方式

- 開啟方式 : `開始 → 搜尋列上輸入"mstsc"`

- 輸入欲連線到的電腦IP後加上冒號+埠號。

    - E.g.192.168.1.150:5566(從實體機遠端登入虛擬機時的練習)
    
### 再製

1. 完整再製 : 浪費磁碟空間但效能好

2. 連結再製 : 節省磁碟空間但效能差

### 網卡模式

![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/%E7%B6%B2%E8%B7%AF%E9%A1%9E%E5%9E%8B.jpg)

1. `NAT`: network address translation

   * centos可看到Internet上的機器，但Internet上的機器看不到centos。
   
   * 在Virtualbox內，centos看不到windows，windows也看不到centos。(但在VMware下，centos和windows可互相看到。)
   
   ![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/NAT.jpg)

2. `Host-only模式`

   * centos和windows可互相看到，但centos不能看到Iternet上的機器。
   
   ![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/hostOnly.jpg)
   
3. `Bridge`:橋切設定

   * 一般不會開，除非要測試。
   
   ![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/Bridge.jpg)

4. `內部網路`

    - 虛擬機內部網路名稱相同就可以相連。
    
    ![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/%E5%85%A7%E9%83%A8%E7%B6%B2%E8%B7%AF.jpg)
    
### Linux提供的三種標準I/O

1. standard input (STDIN) 代號 0：標準輸入，預設為鍵盤

2. standard output (STDOUT) 代號 1：標準輸出，預設為終端機視窗

3. standard error (STDERR) 代號 2：標準錯誤輸出，預設為終端機視窗

### 實作成果-架設ssd server

![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/%E7%AC%AC%E4%BA%8C%E5%91%A8%E7%B5%90%E6%9E%9C.jpg)

### 網頁打開沒畫面之除錯方式

1. ping 127.0.0.1

2. ping 自己的IP位址 (由ipconfig查找)

3. ping 內定路由位址 (由`ip route show`查找)

4. ping 8.8.8.8 (成功的話代表網路暢通)

5. ping www.nqu.edu.tw(任意網址)

* 如果第4點到第5點失敗的話代表 DNS 解析出問題

    * 解決方案: 輸入`gedit/etc/resolve.conf`來更改設定檔 (要先用su切換成root)。
    
    * 補充: `gedit/etc/resolve.conf &`可將此動作丟至背景執行，終端機就可以繼續使用。

### 終端機指令

* Windows:

    * `cls`: 清除終端機屏幕。
    
    * `ls` : list，列出目錄和檔案。

* Linux:

    * `yum upgrade -y`: 將系統軟體更新。
    
    * `clear`: 清除終端機屏幕。
    
    * 查詢系統核心:
    
       * `uname`: 顯示作業系統 (Linux)。

       * `uname -a`: 顯示較多核心資訊。

       * `uname -r`: release，顯示釋出的版本。
    
    * `yum groupinstall 'Development Tools'` : 安裝整套軟體。
    
    * `sudo yum install gcc -y`: "sudo"以超級使用者執行此行命令，執行完後身分回到user，在此為安裝gcc的動作。
    
    * 在Linux終端機中執行C語言程式
    
      * `cat test.c` : concatenate，顯示文件內容。
      
      * `cat tset.c | head -n 2`: 顯示前兩行。
      
      * `cat tset.c | head -n 2 |tail -n 1`: 顯示文件的前兩行的最後一行。
      
      * `cat tset.c | head -n 2 |tail -n 1 | awk '{print $2}'`: 顯示文件的前兩行的最後一行的第二段。
      
      ![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/concatenate.jpg)
      
      ![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/%E5%8D%B0%E5%87%BA%E6%89%80%E8%A6%81%E7%A8%8B%E5%BC%8F%E7%A2%BC.jpg)
      
    * `chmod`-change mode-Linux中使用此指令可將文字檔變成執行檔。
      
      * `chmod -x`: 拿掉執行此檔案的權限。
      
      * `chmod +x`: 賦予執行此檔案的權限。
      
      * `chmod +w`: 賦予書寫此檔案的權限 (write)。
      
      * `chmod +r`: 賦予讀取此檔案的權限 (read)。
      
    * `file 檔名(如a.out)`
      
      * 使用此指令可檢閱檔案的本質。
    
      * 在Linux中不可以只憑副檔名就判斷檔案的本質。
      
    * 確認伺服器是否開啟的兩個方法: 
    
      1. `sudo systemctl status httpd`
      
      2. `sudo netstat -tunlp | grep 80` : 80號埠是網頁伺服器。
      
    * `echo "hi" > /var/www/html/hi.htm`:將文字輸出到網頁，/var/www/html/hi.htm為網頁根目錄，">"為 "導向" 之意。
      
      ![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/%E5%B0%87%E6%96%87%E5%AD%97%E8%BC%B8%E5%87%BA%E5%88%B0%E7%B6%B2%E9%A0%81.jpg)
      
    * `yum install http -y --nogpgcheck`:解決簽證問題。
    
    * `systemctl stop firewalld`:關閉 防火牆
    
      
### 隨手筆記

* Linux終端機中:

   * ctrl+a: 可跳到目前正在輸入的指令最前方。
   
   * ctrl+e: 可跳到目前正在輸入的指令最後方。
   
### 實作成果-架設hppt server

![](https://github.com/ayd0122344/Linux-note/blob/master/%E5%9C%96%E6%AA%94/%E7%AC%AC%E4%B8%89%E5%91%A8%E7%B5%90%E6%9E%9C.jpg)

> 伺服端為ssh，客戶端為putty