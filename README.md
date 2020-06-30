# hello-egg
一步步创建第一个egg项目

### 初始化项目
先来初始化目录结构

```
$ mkdir hello-egg
$ cd hello-egg
$ npm init
$ npm i egg --save
$ npm i egg-bin --save-dev
```
添加 `npm scripts` 到 `package.json`  

```
{
  "name": "egg-example",
  "scripts": {
    "dev": "egg-bin dev"
  }
}
```

### 编写Controller
