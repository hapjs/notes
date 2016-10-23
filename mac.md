# MAC技巧

切换到super user：
```bash
sudo su
```

访问windows的共享目录：
```
点击 Finder 前往菜单中的「前往服务器」（或快捷键 command+k）
在连接服务器对话框中输入「smb://Windows主机的IP地址」
```

Option 键表示“把当前动作应用到该程序的所有窗口”

自动关机：
```bash
# 设定2014年7月11日15:00分关机
sudo shutdown -h 1407111500
```


显示Mac隐藏文件：
```bash
defaults write com.apple.finder AppleShowAllFiles  YES
```

不显示Mac隐藏文件：
```
defaults write com.apple.finder AppleShowAllFiles  NO
```

注：需重启Finder才能生效，鼠标单击窗口左上角的苹果标志-->强制退出-->Finder-->重新启动


