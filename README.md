# 站点状态监控
- 本项目可以直接部署，快速上线，纯静态无需服务器。基于 UptimeRobot api 时时监控主机、网站、端口等在线状态；
- 依赖 github 静态页面，天然支持穿透天朝防火墙，理论上任何暴露于公网的墙外网站和端口服务都可以监控。

## 在线体验：  

简化版：<https://tjys.vercel.app/>  
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/Uptime%20Status.PNG)


## 如何复用这个项目？  
### 1- fork 一份到你的 github 账号下；  
### 2- 修改配置文件：config.js，主要是修改 apikey 内容，强烈建议使用 Read-Only key,<https://uptimerobot.com/dashboard#mySettings> 如下图；  
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/warn.png.png)  
### 3- 绑定网站域名，恭喜部署完成！

#### 登录cloudflare主页，在主菜单右边，点击【网页】
![](https://cdn.jsdelivr.net/gh/qikaile/cdn/img/2021-02-15-01.png)

#### 进入后创建项目并绑定github账号，选择部署仓库
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/2021-02-15-02.png)
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/2021-02-15-03.png)

#### 部署
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/2021-02-15-04.png)

#### 访问域名，你也可以绑定自定义域名
![](https://cdn.jsdelivr.net/gh/Qikaile/cdn/img/2021-02-15-05.png)

你也可以使用Vercel部署网站，登录[vercel官网](https://vercel.com/)注册账号并绑定github,导入新项，选择导入Git存储库，选择个人账号，点击部署。


### 基于 Cloudflare Workers 搭建 UptimeRobot API 代理，以解决官网 API 跨域问题

Build an UptimeRobot API proxy based on **Cloudflare Workers** to solve the cross-domain issue of official API

```
const handleRequest = async ({ request }) => {
  let url = new URL(request.url);
  let response = await fetch('https://api.uptimerobot.com' + url.pathname, request);
  response = new Response(response.body, response);
  response.headers.set('Access-Control-Allow-Origin', '*');
  response.headers.set('Access-Control-Allow-Methods', '*');
  response.headers.set('Access-Control-Allow-Credentials', 'true');
  response.headers.set('Access-Control-Allow-Headers', 'Content-Type,Access-Token');
  response.headers.set('Access-Control-Expose-Headers', '*');
  return response;
}

addEventListener('fetch', (event) => {
  event.respondWith(handleRequest(event));
});
```

修改 `config.js` 中的 `ApiDomian` 为你的域名；

Modify `ApiDomian` in `config.js` to your domain;

## 说明：

本项目是来自原作的简化版：<https://github.com/yb/uptime-status>
