# v2rayA-Ubuntu-Setup
Ubuntu系统使用v2rayA代理配置

## 一、软件安装

### 1. 添加公钥

```bash
sudo mkdir -p /etc/apt/keyrings
wget -qO - https://apt.v2raya.org/key/public-key.asc | sudo tee /etc/apt/keyrings/v2raya.asc
```

### 2. 添加软件源并下载软件

```bash
echo "deb [signed-by=/etc/apt/keyrings/v2raya.asc] https://apt.v2raya.org/ v2raya main" | sudo tee /etc/apt/sources.list.d/v2raya.list
sudo apt update
sudo apt install v2raya xray
```

## 二、软件使用

### 1. 启动v2rayA

单次启动：

```bash
sudo systemctl start v2raya.service
```

设置开机自启动：

```bash
sudo systemctl enable v2raya.service
```

### 2. 配置v2rayA Web Panel软件订阅

打开软件，初次打开需要注册用户名密码：

<img src="/image/111.png" width="300">

注册登陆后，会弹出对话框，选择`导入`，填入订阅地址，`确定`：

<img src="/image/222.png" width="400">
<img src="/image/333.png" width="400">

此时在SUBSCRIPTION栏中会显示已添加的订阅，操作中的`修改`可以更新订阅地址，页面右上的`导入`可以添加新的订阅地址：

<img src="/image/444.png" width="800">

选中一个节点，页面左上的`PING`可以测试连接：

<img src="/image/555.png" width="800">

操作中选择`连接`，节点会显示为红色，再选择页面左上的`就绪`使其变为`启动`和`正在运行`，节点会显示为蓝色：

<img src="/image/666.png" width="800">

### 3. 配置代理

选择页面右上的`设置`，弹出窗口的左下`地址与端口`可以查看代理端口：

<img src="/image/777.png" width="800">
<img src="/image/888.png" width="300">

按照信息，在Ubuntu系统设置内将`网络`->`网络代理`设置为`手动`，填入HTTP、HTTPS、Socks地址与端口（v2rayA没有提共FTP代理）：

<img src="/image/999.png" width="500">

其中`127.0.0.1`代表默认的本地回环地址，表示该代理仅允许本机访问。
