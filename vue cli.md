## 使用命令1
**vue serve**
**vue build**
**vue add**
**vue ui** 
**vue-cli-service serve [options] [entry]**
选项：
	--mode    指定环境模式 (默认值：development)
- 命令会启动一个开发服务器 (基于 webpack-dev-server) 并附带开箱即用的模块热重载 (Hot-Module-Replacement)。
- 除了通过命令行参数，你也可以使用 vue.config.js 里的 devServer 字段配置开发服务器。
**vue-cli-service build [options] [entry|pattern]**
选项：
	--mode        指定环境模式 (默认值：production)
	--dest        指定输出目录 (默认值：dist)
	--modern      面向现代浏览器带自动回退地构建应用
	--target      app | lib | wc | wc-async (默认值：app)
	--name        库或 Web Components 模式下的名字 (默认值：package.json 中的 "name" 字段或入口文件名)
	--no-clean    在构建项目之前不清除目标目录
	--report      生成 report.html 以帮助分析包内容
	--report-json 生成 report.json 以帮助分析包内容
	--watch       监听文件变化
- 会在 dist/ 目录产生一个可用于生产环境的包，带有 JS/CSS/HTML 的压缩，和为更好的缓存而做的自动的 vendor chunk splitting。它的 chunk manifest 会内联在 HTML 里。
**vue-cli-service inspect**
选项：
	--mode    指定环境模式 (默认值：development)
- vue-cli-service inspect 来审查一个 Vue CLI 项目的 webpack config。
 
 ## 使用命令2
- 有些 CLI 插件会向 vue-cli-service 注入额外的命令。例如 @vue/cli-plugin-eslint 会注入 vue-cli-service lint 命令。

## 插件
- Vue CLI 使用了一套基于插件的架构。如果你查阅一个新创建项目的 package.json，就会发现依赖都是以 @vue/cli-plugin- 开头的。
  插件可以修改 webpack 的内部配置，也可以向 vue-cli-service 注入命令。在项目创建的过程中，绝大部分列出的特性都是通过插件来     实现的。 
- 如果出于一些原因你的插件列在了该项目之外的其它 package.json 文件里，你可以在自己项目的 package.json 里设置  vuePlugins.resolveFrom 选项指向包含其它 package.json 的文件夹。

## vue.config.js
1. devServer 字段配置开发服务器
