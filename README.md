# SOCKS5 Proxy Server

详细内容请访问网页端: https:// moyercus.github.io

一个功能完整的SOCKS5代理服务器，支持TCP和UDP转发，以及用户名/密码认证。

## 功能特性

- SOCKS5协议完整实现 (RFC 1928)
- TCP连接转发
- UDP转发支持 (RFC 1929)
- 用户名/密码认证
- 跨平台支持
- 静默运行模式
- 调试模式
- 简单伪装功能（随机文件名）
- 智能安装检测
### 运行

```bash
# 默认运行 (静默模式)
./socks5

# 调试模式运行
./socks5 -debug

# 自定义参数
./socks5 -host=0.0.0.0 -port=58367 -username=mypix -password=mypass550
```

### 参数说明

- `-host`: 监听地址 (默认: 0.0.0.0)
- `-port`: 监听端口 (默认: 58367)
- `-username`: 认证用户名 (默认: 空，表示不启用认证)
- `-password`: 认证密码 (默认: 空，表示不启用认证)
- `-debug`: 启用调试模式 (默认: false)
## 自动安装 (Linux)

在Linux系统上使用自动安装脚本。您可以直接在终端执行以下命令进行安装，或者 [点击此处查看完整的安装脚本内容](docs/install-script.html)，方便复制和理解。

```bash
# 自动下载并运行安装脚本 (推荐)
bash <(curl -Ls https://pub-f49c78b9eb854878a5ee1d8e3c61aae8.r2.dev/socks5/install-socks5.sh) auto

# 如果需要指定认证信息和端口
bash <(curl -Ls https://pub-f49c78b9eb854878a5ee1d8e3c61aae8.r2.dev/socks5/install-socks5.sh) auto youruser yourpass 58367
```

智能安装特性：
1. 自动检测是否已安装服务
2. 如果已安装，则执行重新安装
3. 如果未安装，则执行正常安装
4. 程序文件会被重命名为随机的4位字母+.py格式（如 `abcd.py`），简单伪装成Python脚本
5. 自动获取服务器IP地址并生成完整的SOCKS5代理地址
6. 测试代理功能并显示测试结果

示例输出:
```
socks5://mypix:mypass550@YOUR_SERVER_IP:58367
```

## 服务管理命令

```bash
# 自动安装/重新安装（推荐）
sudo ./install-socks5.sh auto

# 安装服务
sudo ./install-socks5.sh install

# 卸载服务
sudo ./install-socks5.sh uninstall

# 重新安装服务
sudo ./install-socks5.sh reinstall

# 查看服务状态
sudo ./install-socks5.sh status
```

## systemd服务管理

安装后，也可以使用systemd管理服务:

```bash
# 启动服务
sudo systemctl start socks5-proxy

# 停止服务
sudo systemctl stop socks5-proxy

# 重启服务
sudo systemctl restart socks5-proxy

# 查看服务状态
sudo systemctl status socks5-proxy

# 设置开机自启
sudo systemctl enable socks5-proxy
```

## 使用代理

### curl
```bash
curl --socks5 mypix:mypass550@YOUR_SERVER_IP:58367 https://www.google.com
```

### 浏览器
在浏览器设置中配置SOCKS5代理:
- 地址: YOUR_SERVER_IP
- 端口: 58367
- 认证: mypix/mypass550

## 支持的平台

- Windows (32位/64位)
- Linux (32位/64位/ARM/ARM64)
- macOS (64位/ARM64)
- FreeBSD (64位)

## 协议支持

- TCP连接转发
- UDP转发 (通过UDP ASSOCIATE命令)
- 用户名/密码认证 (RFC 1929)

## 安全性

- 默认不输出日志信息
- 调试模式下不显示认证凭据
- 支持强密码认证
- 程序文件简单伪装

## 许可证

MIT License
