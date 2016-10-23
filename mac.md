# MAC技巧

### 访问windows的共享目录
```
点击 Finder 前往菜单中的「前往服务器」（或快捷键 command+k）
在连接服务器对话框中输入「smb://Windows主机的IP地址」
```

### 自动关机
```bash
# 设定2014年7月11日15:00分关机
sudo shutdown -h 1407111500
```


### 显示或隐藏文件
需重启Finder才能生效，鼠标单击窗口左上角的苹果标志-->强制退出-->Finder-->重新启动
```bash
# 显示
defaults write com.apple.finder AppleShowAllFiles  YES

# 不显示
defaults write com.apple.finder AppleShowAllFiles  NO
```

### Finder快捷键
```bash
* Shift + Command + G：定位到指定路径
* Shift + Command + A：定位到应用程序（Applications）
* Shift + Command + C：定位的计算机（Computer）
* Shift + Command + D：定位到桌面（Desktop）
* Shift + Command + I： 定位到 iDisk
* Shift + Command + K：定位到网络（Network）
* Shift + Command + T：添加当前目录到 Dock 最喜爱部分
* Shift + Command + U：定位到实用工具（Utilities）
* Shift + COmmand + N：新建文件夹
* Command + 上       ：跳转至当前文件夹的上一层
```
