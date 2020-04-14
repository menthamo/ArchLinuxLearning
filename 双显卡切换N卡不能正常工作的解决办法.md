### 双显卡切换N卡不能正常工作的解决办法

#### 1.双显卡切换

```shell
sudo pacman -S nvidia bbswitch optimus-manager-qt
# nividia为Nvidia的闭源驱动
# bbswitch就是切换显卡用的
# optimus-manager-qt就是管理器啦，可以在托盘上方便的切换要用的显卡（我这里用的是KDE，如果你用的是gnome或其他的话，安装optimus-manager-qt就行啦）
NOTE:
1. 使用自定义内核需要在后面加上dkms，即：sudo pacman -S nvidia-dkms bbswitch-dkms
2. optimus-manager-qt是AUR中的包，但如果你配置了archlinuxcn源的话，就可以向上面一样直接pacman安装，如果没有的话，使用yay -S optimus-manager-qt就可以安装
```

#### 2.N卡运行出错

describe: when switch to nvidia,steam can't open

```shell
steam
-------------------------------------------------
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
```

replacing mesa-libgl and lib32-mesa-libgl with nvidia-libgl and lib32-nvidia-libgl solved the issue.

```shell
sudo pacman -S nvidia-libgl lib32-nvidia-libgl
```

