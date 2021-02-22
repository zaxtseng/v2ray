## AWS选择
左侧点击实例,启用实例.

选择AWS Marketplace,搜索Debian.

选择Debian9.选择符合条件的免费套餐.审核和启动.

## 秘钥创建
![1.png](https://i.loli.net/2021/01/13/lZkP3Uf9BMWKd4r.png)

启用后,会提示需要先生成一个私人秘钥,选择创建新秘钥对.随便写一个名称.点击生成.保存起来.此秘钥是唯一连接当前实例的密码.
### 秘钥转换
此秘钥格式为pem.需要转换格式.下载putty.安装后打开puttygen.此软件用来转换秘钥格式.

![2.png](https://i.loli.net/2021/01/13/NQcEA8h7HunlCmd.png)

点击上面的conversions, import key.将下载好的pem秘钥导入.

点击右下角按钮save private key.保存为ppk格式.(此格式用putty可以直接使用.)

再次点击上面的conversions,选择export openSSH.存储好.(Xshell使用)

## 创建账单警报
此时,再看实例已经创建完成.

![3.png](https://i.loli.net/2021/01/13/B87LmzVZy5wgMe3.png)

点击创建账单警报,防止免费流量用完扣费.

![4.png](https://i.loli.net/2021/01/13/CZIq9V41BTmsWna.png)

两处打钩,填入报警的邮箱.点击保存.

## 连接Xshell
回到EC界面.点击正在运行的实例.复制公网IP.

下载Xshell.新建连接,用户名admin(或者root),主机填入刚刚复制的IP.

![5.png](https://i.loli.net/2021/01/13/Ry43Y9gM8aeXSBd.png)

![6.png](https://i.loli.net/2021/01/13/JzPp1l4c3iVrkmE.png)

点击左侧用户身份验证.方法改为public Key.用户秘钥点击浏览,点击导入,将之前生成的最后一个秘钥放入,选中,点击确定.

最后连接.

## 使用脚本
在Xshell界面,输入`sudo -s`,使用root身份.

```js
//ss脚本
bash <(curl -s -L https://git.io/ss.sh)
//v2ray脚本
bash <(curl -s -L https://git.io/v2ray.sh)
```
将上述命令粘贴到Xshell.回车.

![7.png](https://i.loli.net/2021/01/13/uFXItenh7WjcU8s.png)

输入1,回车.安装.

弹出端口号,记住,后面安全组要用到.继续疯狂回车.

结束运行.后保存最后的配置信息.信息里的ss连接保存下来.客户端要用.

可输入`ss status`查看是否运行.

另附上所有命令
```js
ss menu 管理 Shadowsocks (同等于直接输入 ss)

ss info 查看 Shadowsocks 配置信息

ss config 更改 Shadowsocks 配置

ss qr 生成 Shadowsocks 配置二维码链接

ss status 查看 Shadowsocks 运行状态

ss start 启动 Shadowsocks

ss stop 停止 Shadowsocks

ss restart 重启 Shadowsocks

ss update 更新 Shadowsocks

ss update.sh 更新 Shadowsocks 管理脚本

ss uninstall 卸载 Shadowsocks
```
## 安全组
回到AWS的EC界面.点击左侧安全组.

选择Debian的编辑入站安全组.

![7.png](https://i.loli.net/2021/02/22/SZ1PRDkw6nqAFXL.png)

将之前的端口号复制进去.

![8.png](https://i.loli.net/2021/02/22/ot12s7n8JD65WM9.png)

或者选择所有流量,全部,确定.
## 客户端
去官网下载客户端.

复制之前保存的SS连接.

打开后右下角右键选择服务器,从剪贴板导入URL.确定.

系统代理选择全局,PAC模式选择更新本地PAC,更新完成后系统代理更改为PAC模式.
## 可用账号
g =>v2ray

544 => ss

