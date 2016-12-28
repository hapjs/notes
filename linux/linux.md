# linux 学习笔记

### 查找占用指定端口的进程然后杀掉它
```bash
lsof -i :端口号
kill -p 进程号
```

### 查看本机外网ip
```bash
curl ifconfig.me
```

### 打印当前目录的结构树
```bash
find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
find . -print | sed -e 's;[^/]*/;|---- ;g;s;----|;    |;g'
```
