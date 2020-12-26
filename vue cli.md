## 命令
1.**vue serve**
- vue serve 的缺点就是它需要安装全局依赖，这使得它在不同机器上的一致性不能得到保证。因此这只适用于快速原型开发。
2.**vue build**

## 插件
Vue CLI 使用了一套基于插件的架构。如果你查阅一个新创建项目的 package.json，就会发现依赖都是以 @vue/cli-plugin- 开头的。
插件可以修改 webpack 的内部配置，也可以向 vue-cli-service 注入命令。在项目创建的过程中，绝大部分列出的特性都是通过插件来实现的。
**vue add 命令**
- 如果你想在一个已经被创建好的项目中安装一个插件，可以使用 vue add 命令：vue add eslint

## vue.config.js
1. devServer 字段配置开发服务器
