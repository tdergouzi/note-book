# NodeJS



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

