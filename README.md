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
第一步需要编写的是 Controller 和 Router，  

```js
// app/controller/home.js
const Controller = require('egg').Controller;

class HomeController extends Controller {
  async index() {
    this.ctx.body = 'Hello world';
  }
}

module.exports = HomeController;
```

配置路由映射：

```js
// app/router.js
module.exports = app => {
  const { router, controller } = app;
  router.get('/', controller.home.index);
};
```

加一个配置文件：

```js
// config/config.default.js
exports.keys = <此处改为你自己的 Cookie 安全字符串>;
```

此时目录结构如下：  

```
hello-egg
├── app
│   ├── controller
│   │   └── home.js
│   └── router.js
├── config
│   └── config.default.js
└── package.json
```

现在可以启动应用来体验下

```shell
npm run dev
open http://localhost:7001
```

### 静态资源
Egg 内置了 static 插件，线上环境建议部署到 CDN，无需该插件。

static 插件默认映射 /public/* -> app/public/* 目录

此处，我们把静态资源都放到 app/public 目录即可：

```
app/public
├── css
│   └── news.css
└── js
    ├── lib.js
    └── news.js
```

访问：`http://127.0.0.1:7001/public/image/lake.jpg`  
