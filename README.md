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

访问 [<[https://dash.cloudflare.com/profile](https://dash.cloudflare.com/profile/api-tokens)>](https://dash.cloudflare.com/profile/api-tokens)在页面下方找到 Global API Key，点击右侧的 View 查看 Key，并保存下来 ，在页面下方找到 Global API Key，点击右侧的 View 查看 Key，并保存下来
