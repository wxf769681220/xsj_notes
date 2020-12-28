## 使用命令1
**vue serve**
**vue build**
**vue create --help**
**vue add**
- 如果你想在一个已经被创建好的项目中安装一个插件，可以使用 vue add 命令：
**vue ui** 
- 通过 vue ui 命令使用 GUI 运行更多的特性脚本。
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
- 
- 如果出于一些原因你的插件列在了该项目之外的其它 package.json 文件里，你可以在自己项目的 package.json 里设置  vuePlugins.resolveFrom 选项指向包含其它 package.json 的文件夹。如果你有一个 .config/package.json 文件：
{
  "vuePlugins": {
    "resolveFrom": ".config"
  }
}
- 如果你需要在项目里直接访问插件 API 而不需要创建一个完整的插件，你可以在 package.json 文件中使用 vuePlugins.service 选项：
{
  "vuePlugins": {
    "service": ["my-commands.js"]
  }
}

## vue.config.js
1. devServer 字段配置开发服务器

## HMTL 和 静态资源
**html-webpack-plugin** 
htmlWebpackPlugin.options.[options]
选项：
	title: 'Webpack App'（默认）用于生成的HTML文档的标题
	filename: 'index.html'（默认） 
	template:  ''  C:\Users\Admin\Desktop\chegao\node_modules\html-webpack- plugin\lib\loader.js!C:\Users\Admin\Deskto p\chegao \public\index.html  
	publicPath: 用于脚本和链接标签的 publicPath
	hash：false（默认）如果是，true则将唯一的webpack编译哈希值附加到所有包含的脚本和CSS文件中。这对于清除缓存很有用。
- public/index.html 文件是一个会被 html-webpack-plugin 处理的模板。在构建过程中，资源链接会被自动注入。（preload/prefetch            manifest 和图标链接  JavaScript 和 CSS 文件的资源链接）
- index 文件被用作模板，所以你可以使用 lodash template 语法插入内容：
	<%= VALUE %> 用来做不转义插值；
	<%- VALUE %> 用来做 HTML 转义插值；
	<% expression %> 用来描述 JavaScript 流程控制。
**静态资源导入方式**

- 在 JavaScript 被导入或在 template/CSS 中通过相对路径(必须以 . 开头) 被引用。这类引用会被 webpack 处理。该资源将会被包含进入 webpack 的依赖图中。在其编译过程中，所有诸如 <img src="...">、background: url(...) 和 CSS @import 的资源 URL 都会被解析为一个模块依赖。如：url(./image.png) 会被翻译为 require('./image.png')
- 放置在 public 目录下或通过绝对路径被引用。这类资源将会直接被拷贝，而不会经过 webpack 的处理。



	

                        