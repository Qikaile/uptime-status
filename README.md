# 站点状态监控
- 本项目可以直接部署，快速上线，纯静态无需服务器。基于 UptimeRobot api 时时监控主机、网站、端口等在线状态；
- 依赖 github 静态页面，天然支持穿透天朝防火墙，理论上任何暴露于公网的墙外网站和端口服务都可以监控。

## 在线体验：  

简化版：<https://tjys.now.sh/>  
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/Uptime Status.PNG)


## 如何复用这个项目？  
1- fork 一份到你的 github 账号下；  
2- 修改配置文件：config.js，主要是修改 apikey 内容，强烈建议使用 Read-Only key,<https://uptimerobot.com/dashboard#mySettings> 如下图；  
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/warn.png.png)  
3- 绑定网站域名，恭喜部署完成！

## 说明：

本项目是来自原作的简化版：<https://github.com/yb/uptime-status>
