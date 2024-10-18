---
title: ssh快捷登录
publishDate: '2024-10-15'
isFeatured: true
seo:
  title: ssh快捷登录
  description: ssh设置快捷登录
---
ssh user@host是不是太麻烦了？
来搞快捷代理吧
来看看下面的命令
```
ssh vps
```
vps替代了user跟host
怎么搞的呢，其实不难
```
vim .ssh.config
```
添加以下内容
```
Host <名称>
Hostname <ip或域名>
Port <端口>
User <用户>
```
就可以使用ssh <名称>进行连接了
不想用密码也可以用密钥，还更安全
先搞一个rsa key
```
ssh-keygen
```
一路回车即可
不必手动复制密钥，可以使用ssh-copy-id
```
ssh-copy-id -i ~/.ssh/id_rsa.pub vps
```
