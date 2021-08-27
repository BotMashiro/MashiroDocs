# 快速开始

## 环境

Mashiro需要Python3作为运行时的环境，尽管理论上任意Python 3.6以上的版本都可以运行，我们仍然推荐您使用最新的Python 3.9版本，因为Mashiro基于Python 3.9的进行开发。您可以从[Python组织官网](https://python.org/)获取最新的Python下载。

同时，Mashiro需要go-cqhttp作为QQ的客户端，您可以从这里获取最新的[Release](https://github.com/Mrs4s/go-cqhttp)。



## 安装

### 部署go-cqhttp

1. 从[go-cqhttp](https://github.com/Mrs4s/go-cqhttp)的官方仓库获取最新的[Release](https://github.com/Mrs4s/go-cqhttp/releases/latest)

2. 解压并进入解压后的文件夹

3. 在此文件夹打开终端，并键入

   `Windows:`

   ```powershell
   .\go-cqhttp.exe
   ```
   `Linux:`

   ```bash
   ./go-cqhttp
   ```

4. 您将会得到以下信息

   ```bash
   未找到配置文件，正在为您生成配置文件中！
   请选择你需要的通信方式:
   > 1: HTTP通信
   > 2: 正向 Websocket 通信
   > 3: 反向 Websocket 通信
   > 4: pprof 性能分析服务器
   > 5: 云函数服务
   请输入你需要的编号，可输入多个，同一编号也可输入多个(如: 233)
   您的选择是:
   ```

   这里输入"2"后回车

   ```bash
   默认配置文件已生成，请修改 config.yml 后重新启动!
   ```

   再次回车退出程序

5. 打开同目录下的config.yml文件

   首先我们在此设置QQ账号信息，按照注释进行相应配置即可

   ```yaml
   account: # 账号相关
     uin: 1233456 # QQ账号
     password: '' # 密码为空时使用扫码登录
     encrypt: false  # 是否开启密码加密
   ```

   如果您是在公网环境下进行使用，我们强烈推荐您设置token

   ```yaml
   # 默认中间件锚点
   default-middlewares: &default
     # 访问密钥, 强烈推荐在公网的服务器设置
     access-token: ''
   ```

   最后在此设置服务器IP和端口信息，如果您不熟悉go-cqhttp，此块内容可以保持不动

   ```yaml
   servers:
     # 添加方式，同一连接方式可添加多个，具体配置说明请查看文档
     #- http: # http 通信
     #- ws:   # 正向 Websocket
     #- ws-reverse: # 反向 Websocket
     #- pprof: #性能分析服务器
     # 正向WS设置
     - ws:
         # 正向WS服务器监听地址
         host: 127.0.0.1
         # 正向WS服务器监听端口
         port: 6700
   ```

6. 我们再次使用终端启动go-cqhttp(详见[第一步](#部署go-cqhttp))，若提示成功登录，则go-cqhttp的部署完成。若您在部署过程中遇到其他问题，欢迎前去[go-cqhttp帮助中心](https://docs.go-cqhttp.org/)查询。

