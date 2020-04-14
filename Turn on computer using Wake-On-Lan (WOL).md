### Turn on computer using Wake-On-Lan (WoL)

#### 1. Hardware settings

The Wake-on-LAN feature must be enabled in the computer's BIOS

#### 2. Software configuration

Install  `ethtool` to  query the WoL  status or to change the settings.

```shell
ethtool `interface` | grep Wake-on # interface means network card‘s name : query:[计]查询，n/v 质问，询问，表示怀疑
------------------------------------------------------------
Supports Wake-on:pumbag
Wake-on:d
```

The Wake-on values define what activity triggers wake up:`d`(disable),`g`(magic packet activity...). The value  `g` is required for WoL to work. If not, use the following command:

```shell
ethtool -s interface wol g
```

#### 3. Make it persistent

The command might not last beyond next reboot and in this case must be repeated via some mechanism.` 途径，进程` 

Install `cronie` or other packages ,

```shell
sudo pacman -S cronie
sudo systemctl enable cronie.service 
# need special attention `cronie.service`
```

then use the following command :

```shell
crontab -e # creat a schedule job 课程，日程，计划表;预订，安排v/n. NOTE: By default the `crontab` command uses the `vi` editor. To change it using : EDITOR=vin crontab -e
# then type:
@reboot /usr/bin/ethtool -s `interface` wol g 
```

