<p align="center">
  <a href="https://github.com/whyour/qinglong">
    <img width="150" src="https://qinglong.whyour.cn/qinglong.png">
  </a>
</p>

<h1 align="center">青龙</h1>

<div align="center">

Python/JavaScript/Shell/Typescript 定时任务管理

[![docker version][docker-version-image]][docker-version-url] [![docker pulls][docker-pulls-image]][docker-pulls-url] [![docker stars][docker-stars-image]][docker-stars-url] [![docker image size][docker-image-size-image]][docker-image-size-url] [![donate][donate-image]][donate-url]

[donate-image]: https://img.shields.io/badge/donate-wechat-green?style=flat
[donate-url]: https://qinglong.whyour.cn/nice.png
[docker-pulls-image]: https://img.shields.io/docker/pulls/whyour/qinglong?style=flat
[docker-pulls-url]: https://hub.docker.com/r/whyour/qinglong
[docker-version-image]: https://img.shields.io/docker/v/whyour/qinglong?style=flat
[docker-version-url]: https://hub.docker.com/r/whyour/qinglong/tags?page=1&ordering=last_updated
[docker-stars-image]: https://img.shields.io/docker/stars/whyour/qinglong?style=flat
[docker-stars-url]: https://hub.docker.com/r/whyour/qinglong
[docker-image-size-image]: https://img.shields.io/docker/image-size/whyour/qinglong?style=flat
[docker-image-size-url]: https://hub.docker.com/r/whyour/qinglong
</div>

<p align="center">
  <img width="49%" src="https://qinglong.whyour.cn/login.png">
  <img width="49%" src="https://qinglong.whyour.cn/home.png">
</p>


  ## 一、安装青龙主程序

### 1.拉取面板
```bash
docker pull whyour/qinglong:latest
```
### 2.创建容器
```bash
~docker run -dit \
  -v /ql/config:/ql/config \
  -v /ql/log:/ql/log \
  -v /ql/db:/ql/db \
  -v /ql/repo:/ql/repo \
  -v /ql/raw:/ql/raw \
  -v /ql/scripts:/ql/scripts \
  -v /ql/jbot:/ql/jbot \
  -v /ql/ninja:/ql/ninja \
  -p 5700:5700 \
  -p 5701:5701 \
  --name qinglong \
  --hostname qinglong \
  --restart unless-stopped \
  whyour/qinglong:latest~
  ```
  新版命令：
  ```bash
docker run -dit \
-v $PWD/ql:/ql/data \
-p 5700:5700 \
--name qinglong \
--hostname qinglong \
--restart unless-stopped \
whyour/qinglong:latest
```
  
  
  记得放行5700和5701端口
  
  ### 3.登录青龙面板
  （1）浏览器进网址：http://ip:5700（ip指你的服务器公网ip）
  
  （2）默认账号密码admin，输入后点击登录，会显示密码已重置。
  
  （3）查看重置后的密码，去FinalShell输入指令：
  ```bash
  cat /root/ql/config/auth.json
  ```
  或者  
  ```bash
  cat /ql/config/auth.json
  ```
  复制显示出来代码里password后面双引号中的内容（密码），返回浏览器重新登录面板。
  
  ## 二、安装Ninja界面
  
  1.shell界面依次输入
  
 ```docker exec -it qinglong bash ```     ##进入青龙容器，qinglong为容器名称
 
 ```git clone https://github.com/MoonBegonia/ninja.git /ql/ninja ```    ##拉取ninja 
 
 ```cd /ql/ninja/backend ```    ##进入ninja后端文件夹
 
 ```pnpm install ```   ##安装ninja
 
 ```pm2 start ```    ##启动ninja
 
 2.添加启动任务到extra，随容器启动extra.sh
 
 在青龙面板-配置文件-extra.sh
 ```bash
 cd /ql/ninja/backend
 pm2 start
 ```
 3.访问http://IP:5701  扫码添加cookie，当然也可以在环境变量中手动添加
 
 ## 附录——定时任务库（收集于网络）
 
 1.【Faker集合仓库】国外服务器命令指令：
 ```bash
 ql repo https://github.com/shufflewzc/faker2.git "jd_|jx_|gua_|jddj_|getJDCookie" "activity|backUp" "^jd[^_]|USER|ZooFaker_Necklace.js|JDJRValidator_Pure|sign_graphics_validate"
```
 时间：自定义
 
 2.【怨念集合仓库】国外服务器命令:
 ```bash
 ql repo https://github.com/yuannian1112/jd_scripts.git "jd_|jx_|getJDCookie" "activity|backUp" "^jd[^_]|USER|utils"
 ```
 
 3.【更新longzhuzhu仓库】
 ```bash
 ql repo https://ghproxy.com/https://github.com/nianyuguai/longzhuzhu.git "qx" 
```
4.【更新i-chenzi仓库】  
  
```bash
ql repo https://ghproxy.com/https://github.com/monk-coder/dust.git "i-chenzhe|normal|member|car" "backup"  
```
 5.【更新lxk仓库】 
  
```bash
ql repo https://ghproxy.com/https://github.com/chinnkarahoi/jd_scripts.git "jd_|jx_|getJDCookie" "activity|backUp" "^jd[^_]|USER"  
```

6.【更新whyour仓库】指令
```bash
ql repo https://ghproxy.com/https://github.com/whyour/hundun.git "quanx" "tokens|caiyun|didi|donate|fold|Env"  
```
