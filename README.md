# WXAPP
# 微信小程序开发
## 第一章 初识微信小程序
1.1 搭建微信小程序开发环境
* 1.1.1 下载微信小程序开发工具<br/>
  所谓搭建微信开发环境就是，安装微信官方提供的微信小程序开发工具，其下载url地址为:(https://developers.weixin.qq.com/miniprogram/devtools/download.html)

1.2 创建第一个微信小程序
* 1.2.1 获取微信小程序的AppID <br/>
  开发者开发好的微信小程序必须要有AppID才能进行发布，可以点击以下url地址进行小程序注册并获取AppID，如:
  (https://mp.weixin.qq.com/wxopen/waregister?action=step1)
  小程序注册成功后，开发者可以在，设置-->开发设置 中，查看到自己的微信小程序的AppID，如我的微信小程序ID为wx9b17e456fc633ca2
* 1.2.2 创建项目<br/>
  打开微信小程序开发工具，填入 项目所在目录(微信小程序的根目录)、AppID、项目名称 并勾选建立普通快速启动模板，点击确定即可创建一个微信小程序，如:
  ![](https://github.com/JS-Even-JS/WXAPP/blob/master/res/create_wx_app.png)
### 备注
    * 勾选建立普通快速启动模板后，开发工具就会自动创建一些微信小程序的模板结构，包含了微信小程序的必备文件;
    * 如果没有勾选，那么创建的项目中就不会添加任何文件，进入项目之后开发工具就会提示app.json文件出错，因为小程序打开时就会去寻找名为app.json的文件;

* 1.2.3 微信小程序的主要文件<br/>
  微信小程序项目根目录下面会包含2个目录和4个文件,分别为:pages目录、utils目录、app.js、app.json、app.wxss、project.config.json,如:
  ![](https://github.com/JS-Even-JS/WXAPP/blob/master/res/wx_app_project_structure.png)
  .js后缀的是脚本文件，.json后缀的是配置文件、.wxss后缀的是样式表文件，微信小程序会读取这些文件，并生成小程序实例.
  
 ## 第二章 微信小程序架构分析
 2.1 微信小程序框架结构
 * 2.1.1 目录结构<br/>
   一个微信小程序的页面是由一个`页面描述文件`、一个`页面逻辑文件`、一个`样式表文件`来进行描述的。
