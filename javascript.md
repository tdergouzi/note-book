# JavaScript



## 什么是 JavaScript 语言？



JavaScript 是轻量脚本语言（script language）

JavaScript 也是一种嵌入式（embeded）语言

宿主环境（host）主要为浏览器和 Node

JavaScript 语言版本，比如 ECMAScritp 5.1 和 ES6

JavaScript 程序可采用事件驱动（event-driven）和非阻塞式设计（non-blocking），用于服务器端高并发环境











































## NodeJS 

### npm

1. 安装运行依赖项

```sh
npm install <package-name>
```

2. 安装开发依赖项

```sh
npm install <package-name> --save-dev
```

开发依赖是仅用于开发的程序包，在生产环境不需要。例如测试的软件包 webpack Babel 等。

生产环境中，安装依赖的时候，`npm install` 默认开始开发部署，所以需要 `npm install --production` 声明，以避免安装开发依赖。

3. 安装对等依赖项

```sh
npm install <package-name> --save-peer
```

安装依赖时，依赖库与另一个依赖库的依赖库产生冲突，为避免冲突和重复安装，可以用对等依赖的方式。结果如下：

```sh
.
├──package.json
├──src
│  └──index.js
└──node_modules
   └──peer-dependencies-plugin-core
   └──peer-dependencies-plugin
      └──node_modules
         └──peer-dependencies-plugin-core
```

将 `peer-dependencies-plugin-core` 设置为 `peerDependencies`，再 `npm install peer-dependencies-plugin`

```sh
{
  ...
  "peerDependencies": {
    "peer-dependencies-plugin-core": "^1.0.0"
  }
  ...
}
```

```sh
.
├──package.json
├──src
│  └──index.js
└──node_modules
   └──peer-dependencies-plugin-core
   └──peer-dependencies-plugin
```





