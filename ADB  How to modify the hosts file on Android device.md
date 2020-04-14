### ADB / How to modify the hosts file on Android device

(without ROOT)

#### 1. install adb

```shell 
sudo pacman -S android-tools # or just type adb ,this is ok too
### NOTE:adb needs `root or sudo` permission 
```

#### 2. turn on USB debugging in the developer setting, then connect the phone and run 

```shell
sudo adb devices
---------------------------------------
List of devices attached
a519f224	device
###`devicse` means everything is OK. must use root or sudo!
sudo adb pull /system/etc/hosts /home/mentha
sudo vim /home/mentha/hosts
sudo adb push /home/mentha/hosts /system/etc/
```



