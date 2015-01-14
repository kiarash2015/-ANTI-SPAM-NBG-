telegram-bot
============

A Telegram Bot based on plugins using [tg](https://github.com/vysheng/tg).

Multimedia
----------
- When user sends image (png, jpg, jpeg) URL download and send it to origin.
- When user sends media (gif, mp4, pdf, etc.) URL download and send it to origin.
- When user sends twitter URL, send text and images to origin. Requires OAuth Key.
- When user sends youtube URL, send to origin video image.

![http://i.imgur.com/0FGUvU0.png](http://i.imgur.com/0FGUvU0.png) ![http://i.imgur.com/zW7WWWt.png](http://i.imgur.com/zW7WWWt.png) ![http://i.imgur.com/zW7WWWt.png](http://i.imgur.com/kPK7paz.png)

Default enabled commands
------------
```
!9gag -> send random image from 9gag
!echo [whatever] -> echoes the msg
!get (value_name) -> retrieves variables saved with !set
!set [value_name] [data] -> Set value
!img [topic] -> search image with Google API and sends it
!loc (location) -> Gets information about a location, maplink and overview
!stats -> Numer of messages by user
!time [area] -> Displays the local time in an area
!version -> Shows bot version
!google terms -> Searches Google
!help -> Lists all available commands
```

Installation
------------
```bash
# Tested on Ubuntu 14.04, for other OSs check out https://github.com/vysheng/tg#installation
$ sudo apt-get install libreadline-dev libconfig-dev libssl-dev lua5.2 liblua5.2-dev libevent-dev unzip git
$ cd /tmp
$ wget http://luarocks.org/releases/luarocks-2.2.0.tar.gz
$ tar -xzvf luarocks-2.2.0.tar.gz 
$ cd luarocks-2.2.0/
$ ./configure 
$ make && sudo make install
$ sudo luarocks install oauth
$ sudo luarocks install luasocket
```
```bash
# After those dependencies, lets install the bot
$ cd $HOME
$ git clone https://github.com/yagop/telegram-bot.git --recursive
$ cd telegram-bot/tg
$ ./configure && make && cd ..
$ ./launch.sh # Will ask you for a phone number & confirmation code.
```

Enable more [`plugins`](https://github.com/yagop/telegram-bot/tree/master/plugins)
-------------
See the plugins list with `!plugins` command.

Enable a disabled plugin by `!plugins enable [name]`.

Disable an eanbled plugin by `!plugins disable [name]`.

Those commands require a privileged user, privileged users are defined inside `data/config.lua` (generated by the bot), stop de bot and edit if necessary.


Run it as a daemon
------------
If your linux/unix comes with [upstart](http://upstart.ubuntu.com/) you can run the bot by this way
```bash
$ sed -i "s/yourusername/$(whoami)/g" etc/telegram.conf
$ sed -i "s_telegrambotpath_$(pwd)_g" etc/telegram.conf
$ sudo cp etc/telegram.conf /etc/init/
$ sudo start telegram # To start it
$ sudo stop telegram # To stop it
```

Contact me
------------
You can contact me [via Telegram](https://telegram.me/yago_perez) but if you have an issue please [open](https://github.com/yagop/telegram-bot/issues) one.
