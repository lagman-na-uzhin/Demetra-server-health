
```sh

cd $HOME && git clone -v https://github.com/lagman-na-uzhin/Demetra-server-health.git && mv Demetra-server-health serberbot && cd ./serverbot && chmod +x ./installsbot.sh
```
 4. Open ./config.py and insert your bot API and your bot name.
 5. Run script ./installsbot.sh for Ubuntu/Debian and ./installsbot_centos.sh for CentOS, source your bash or zsh to make bot start/stop commands working
```sh
./installsbot.sh
```
```sh
source ${HOME}/.bash_aliases
source ${HOME}/.zshrc
```

### if command alias dont work, use 

sudo systemctl stop serverbot
sudo systemctl start serverbot
sudo systemctl status serverbot


### Update
 1. Backup your old config and pull changes from git
```sh
cd $HOME/serverbot && mv config.py config.py.bak && git pull
```

### Update
 1.1 Update project from git
```sh
cd $HOME/serverbot && botstop && git pull && botstart
```
 2. Compare the configs and adjust if necessary
 3. Restart bot
```sh
botstop
botstart
```

### Start, stop or check bot status
If you make any changes in config you need to restart your bot. To start, stop or check status you can use commands in bash:
```sh
botstart
botstop
botstatus
```

### What to do if something not working?
If you get History load error, remove bot files from /tmp and from serverbot db dirs
```sh
sudo rm -rf /tmp/*.log
sudo rm -rf /tmp/*.png
sudo rm ${HOME}/serverbot/db/*
```
Find in bot.py telebot.logger.setLevel(logging.ERROR) and change ERROR to DEBUG, restart serverbot service and execute
```sh
$ sudo journalctl -e -u serverbot > ~/serverbot/servicelog.log
```
If near tools not working, make sure what you've near is /usr/bin, if not:
```
which near
near_path=$(which near)
sudo ln -s ${near_path} /usr/bin/near
```


