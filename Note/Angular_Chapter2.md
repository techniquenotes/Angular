## 2.1 Angular 概述

AngularJS v1.x 官网：https://angularjs.org/

Angular v2.x~v8.x 官网：https://angular.io/

Angular中文镜像网站：https://angular.cn/

### 搭建Angular开发环境

前提：Node.js V10.x  以上

```java
C:\Users\lenovo>node -v
v18.19.0
```

#### 下载并安装脚手架工具

默认仓库：`registry.npmjs.com`

```java
npm i -g @angular/cli
```

#### 运行脚手架工具创建空白项目

```java
ng new myngapp01
```

最新版没有生成`app.module.ts`，修改命令

https://github.com/angular/angular/issues/52751

```java
D:\Angular_Learning\Project>ng new myngapp01 --no-standalone --routing --ssr=false
```

#### 进入空白项目并运行开发服务器

```java
cd myngapp01
npm start
```

#### 客户端访问测试         

```java
http://127.0.0.1:端口号
```

## 2.2 搭建开发环境

### 使用第三方NPM下载仓库

查看当前NPM默认的下载仓库地址

```java
C:\Users\lenovo>npm config get registry
https://registry.npmjs.org/
```

修改NPM默认的下载仓库地址为国内镜像网站

```java
C:\Users\lenovo>npm config set registry https://registry.npm.taobao.org

C:\Users\lenovo>npm config get registry
https://registry.npm.taobao.org
```

安装脚手架工具

```java
C:\Users\lenovo>npm i -g @angular/cli
npm ERR! code CERT_HAS_EXPIRED
npm ERR! errno CERT_HAS_EXPIRED
npm ERR! request to https://registry.npm.taobao.org/@angular%2fcli failed, reason: certificate has expired

npm ERR! A complete log of this run can be found in: C:\Users\lenovo\AppData\Local\npm-cache\_logs\2024-03-15T08_44_01_384Z-debug-0.log
```

解决

https://blog.csdn.net/maoge_666/article/details/136038003

淘宝镜像过期，更换新镜像

```java
C:\Users\lenovo>npm config list
; "builtin" config from D:\Nodejs\node_modules\npm\npmrc

prefix = "C:\\Users\\lenovo\\AppData\\Roaming\\npm"

; "user" config from C:\Users\lenovo\.npmrc

registry = "https://registry.npm.taobao.org"

; node bin location = D:\Nodejs\node.exe
; node version = v18.19.0
; npm local prefix = C:\Users\lenovo
; npm version = 10.2.3
; cwd = C:\Users\lenovo
; HOME = C:\Users\lenovo
; Run `npm config ls -l` to show all defaults.

C:\Users\lenovo>npm cache clean --force
npm WARN using --force Recommended protections disabled.

C:\Users\lenovo>npm config set registry https://registry.npmmirror.com

C:\Users\lenovo>npm config list
; "builtin" config from D:\Nodejs\node_modules\npm\npmrc

prefix = "C:\\Users\\lenovo\\AppData\\Roaming\\npm"

; "user" config from C:\Users\lenovo\.npmrc

registry = "https://registry.npmmirror.com"

; node bin location = D:\Nodejs\node.exe
; node version = v18.19.0
; npm local prefix = C:\Users\lenovo
; npm version = 10.2.3
; cwd = C:\Users\lenovo
; HOME = C:\Users\lenovo
; Run `npm config ls -l` to show all defaults.

C:\Users\lenovo>npm i -g @angular/cli

added 232 packages in 11s
```

### 运行脚手架工具创建空白项目

```java
D:\Angular_Learning\Project>ng new myngapp01
? Which stylesheet format would you like to use? CSS
? Do you want to enable Server-Side Rendering (SSR) and Static Site Generation (SSG/Prerendering)? Yes
CREATE myngapp01/angular.json (2853 bytes)
CREATE myngapp01/package.json (1272 bytes)
CREATE myngapp01/README.md (1090 bytes)
CREATE myngapp01/tsconfig.json (936 bytes)
CREATE myngapp01/.editorconfig (290 bytes)
CREATE myngapp01/.gitignore (590 bytes)
```

## 2.3 搭建环境

### 进入并启动项目

```java
cd myngapp01
npm start
```

<img src="https://cdn.jsdelivr.net/gh/techniquenotes/photohouse/Angular202403162222839.png" alt="image-20240316131534143" style="zoom:50%;" />

官方组件`appcomponent.ts`，定义在`app.component.html`







