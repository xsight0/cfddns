# cfddns
动态vps需部署ddns之cloudflare版
## 自建DDNS解决动态IP服务器访问问题

*   把域名接入cloudflare
*   获取Global API Key
*   设置用于 DDNS 解析的二级域名，流量不经过CDN(云朵变灰)
*   下载 DDNS 脚本
*   修改 DDNS 脚本并补充相关信息
*   设置定时任务


### 把域名接入cloudflare

打开[cloudflare](https://www.cloudflare.com/zh-cn/)，登陆账号添加网站按照提示操作

### 获取Global API Key

访问 [<(https://dash.cloudflare.com/profile/api-tokens)>](https://dash.cloudflare.com/profile/api-tokens)在页面下方找到 Global API Key，点击右侧的 View 查看 Key，并保存下来 ，在页面下方找到 Global API Key，点击右侧的 View 查看 Key，并保存下来
![微信图片_20250918152507](https://raw.githubusercontent.com/xsight0/cfddns/d7fc5a924f2f431f62336a141480e6b9e86f26e2/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20250918152507.png)


### 设置用于 DDNS 解析的二级域名，流量不经过CDN(云朵变灰)

添加一条A记录，例如：hkt.test.com，Proxy status设置成DNS only
![截图_20250918152857](https://raw.githubusercontent.com/xsight0/cfddns/refs/heads/main/jietu_20250918152857.png)

###下载 DDNS 脚本###
执行以下命令下载脚本并赋予执行权限：

```bash
curl https://raw.githubusercontent.com/xsight0/cfddns/refs/heads/main/cfddns.sh > /root/cfddns.sh && chmod +x /root/cfddns.sh
```

###修改 DDNS 脚本并补充相关信息
下载好这个
最好用 finalshell.exe 等工具下载先来编辑
主要修改几个地方
```bash
# 填写Cloudflare Global API Key
CFKEY=你的Global API Key

# 填写Cloudflare登录邮箱
CFUSER=你的邮箱地址

# 填写一级域名（如example.com）
CFZONE_NAME=你的主域名

# 填写二级域名前缀（如ddns）
CFRECORD_NAME=你的二级域名前缀
```
###设置定时任务
一句话实现
```bash
echo '*/2 * * * * /root/cfddns.sh >> /var/log/cf-ddns.log 2>&1' | crontab -
```
这个是2分钟一次 一般够用了
日志地址在
/var/log/路径下 用 finalshell.exe 文件管理看 
