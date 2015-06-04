# Laravel-Homestead-Installation

[hackpad版本](https://revivera.hackpad.com/Laravel-Homestead-vKNxF9sWuEk)


1. 安裝 [virtualbox](https://www.virtualbox.org/wiki/Downloads) ,  [Vagrant](http://www.vagrantup.com/downloads.html)
2. 下指令 vagrant box add laravel/homestead
3. git clone https://github.com/laravel/homestead.git Homestead (把 code Homestead 放到你想放的目錄)
4. ssh-keygen -t rsa -C "you@homestead" (設定 ssh key, 一直按enter就好)
5. 編輯 Homestead/src/stubs/Homestead.yaml
<pre>
    ip: "192.168.10.132" # 虛擬機區網ip
    memory: 1024 
    cpus: 1
    provider: virtualbox
    
    authorize: ~/.ssh/id_rsa.pub # 剛產的 key
    
    keys:
        - ~/.ssh/id_rsa  # 剛產的  key 
    
    folders:
        - map: /Users/sakilu/Documents/www.sakilu.com/var/www/AgentECBack # 自己電腦的專案目錄
          to: /home/vagrant/Code/Laravel # 虛擬機裡的專案目錄
          # 上面這個路徑自己長出來
    
    sites:
        - map: agentecback.dev # 網址 記得去 /etc/hosts 增加一行 127.0.0.1 agentecback.dev(我本機是取這)
          to: /home/vagrant/Code/Laravel/public # 虛擬機 public 目錄
    
    databases:
        - homestead
    
    variables:
        - key: APP_ENV
      value: local
</pre>
6. Homestead目錄下執行 sh init.sh.會把剛改的Homestead.yaml 複製到 ~/.homestead/Homestead.yaml 供vagrant使用
7. Homestead目錄下執行 vagrant up.  虛擬機開啟
8. 使用putty等ssh連線連到虛擬機.    ssh key為 上面剛建立的 id_rsa檔案 # mac使用 vssh
9. 虛擬機重新啟動 nginx
10. [phpstorm xdebug路徑設置](http://stackoverflow.com/questions/22484304/how-to-setup-xdebug-properly-in-phpstorm-for-laravel-web-app-that-run-in-vagrant)
