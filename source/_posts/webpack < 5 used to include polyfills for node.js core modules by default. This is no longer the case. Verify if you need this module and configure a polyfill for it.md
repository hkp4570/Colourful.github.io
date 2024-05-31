---
title: vue项目webpack < 5 used to include polyfills for node.js core modules by default. This is no longer the case. Verify if you need this module and configure a polyfill for it
date: 2024-05-31 17:32:10
categories:
  - 解决方案
tags:
  - vue@2 webpack@5
---



### 问题复现

启动vue@2.6版本的项目时突然报错，查看`webpack`文档。原来`webpack 5` 不再自动 polyfill Node.js 的核心模块，这意味着如果你在浏览器或类似的环境中运行的代码中使用它们，你必须从 NPM 中安装兼容的模块，并自己包含它们。[文档地址](https://webpack.docschina.org/configuration/resolve/#resolvefallback)

<!-- more -->

![image-20240531173830928](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/image-20240531173830928.png)

### 解决方案

在`vue.config.js`配置文件中如下配置。如果你想包含某个polyfill，则手动下载对应的包。否则设置为false。

```javascript
module.exports = defineConfig({
    transpileDependencies: true, devServer: {
        proxy: {
            "/v1": {
                target: ""
            }
        }
    }, configureWebpack: {
        resolve: {
            fallback: {
                'assert': false,
                'process': false,
                'url': false,
                'path-browserify': false,
                'util': false,
                "fs": false,
                "module": false,
                "v8": false,
                "path": require.resolve("path-browserify") // npm install path-browserify
            }
        }
    }
})
```

或者下载插件`node-polyfill-webpack-plugin`，该插件Polyfill Webpack5 中的 Node.js 核心模块。

```javascript
const NodePolyfillPlugin = require("node-polyfill-webpack-plugin")

module.exports = defineConfig({
    transpileDependencies: true, devServer: {
        proxy: {
            "/v1": {
                target: ""
            }
        }
    }, configureWebpack: {
        resolve: {
            fallback: {
                "module": false,
                "v8": false,
            }
        },
        plugins: [
            new NodePolyfillPlugin()
        ]
    }
})
```

