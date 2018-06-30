# WXAPP
# 微信小程序开发
## 第一章 初识微信小程序
### 1.1 搭建微信小程序开发环境
* 1.1.1 下载微信小程序开发工具<br/>
  所谓搭建微信开发环境就是，安装微信官方提供的微信小程序开发工具，其下载url地址为:(https://developers.weixin.qq.com/miniprogram/devtools/download.html)

### 1.2 创建第一个微信小程序
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
### 2.1 微信小程序框架结构
* 2.1.1 目录结构<br/>
   一个微信小程序的页面是由一个`页面描述文件`、一个`页面逻辑文件`、一个`样式表文件`来进行描述的。
   pages目录是用于存放小程序中的页面的，项目刚创建好的时候其下默认有2个子目录，分别是`index`和`logs`目录，分别代表index首页和logs日志页面，
   里面存放着与当前页面相关的一些文件，一个页面通常包含4种不同扩展名文件: `页面中的逻辑文件(.js)`、`页面中的结构文件(.wxml)`、`页面中的样式文件(.wxss)`、`页面中的配置文件(.json)`;<br/>
   为了方便开发者减少配置项，框架特别约定描述页面的这4个文件必须具有相同的路径和文件名，即`必须放在对应的页面目录下并且文件名必须与页面名称保持一致`;<br/><br/>
   
* 2.1.2 项目根目录主体文件<br/>
   a. app.js，这个微信小程序的主逻辑文件，在项目中必不可少，这个文件主要用于`注册小程序`;<br/>
   b. app.json，这个是微信小程序的主配置文件，在项目中必不可少，这个文件主要用于`对微信小程序进行全局配置`;<br/>
   c. app.wxss，这个是微信小程序的主样式表文件，在项目中`可以不要`，主样式表中设置的样式`可以在其他页面中共享`;<br/><br/>
   
* 2.1.3 页面文件<br/>
   微信小程序的页面和项目根目录下的主体文件差不多，主要是多了一个wxml文件，因为每个页面有对应的页面结构，如:<br/>
   a. 页面名称.js，这个是页面的逻辑文件，用于编写JavaScript代码，控制页面逻辑，每个页面`必须要有这个文件`;<br/>
   b. 页面名称.wxml，这个是页面的结构描述文件，用于设计页面的布局和进行数据的绑定，每个页面`必须要有这个文件`;<br/>
   c. 页面名称.wxss，这个是页面的样式表文件，用于定义当前页面使用到的样式，如果当前页面中所使用到的样式都定义在了app.wxss中，那么可以省略这个文件;<br/>
   d. 页面名称.json，这个是页面的配置文件，如果页面没有什么特殊的配置，那么可以省略该文件，只使用app.json中的配置即可;<br/><br/>
   
### 2.2 配置文件详解  
* 2.2.1 主配置文件app.json<br/>
  主配置文件主要是对当前项目进行一些全局配置，包括`项目有哪些页面组成`、`窗口的表现`、`网络超时时间`、`设置多tab`;<br/>
  a. 通过pages属性配置页面路径，其值是一个数组，微信小程序中所使用到的页面都必须在app.json中进行配置才会生效,数组中的每一项是代表页面路径的字符串，其格式为"pages/页面名称/页面文件名"，文件名不需要写后缀，因为框架会自动寻找对应的.wxml、.wxss、.js、.json文件并进行编译和组合;<br/>
     
  a. 通过pages属性配置页面路径，其值是一个数组，微信小程序中所使用到的页面都必须在app.json中进行配置才会生效,数组中的每一项是代表页面路径的字符串，其格式为"pages/页面名称/页面文件名"，文件名不需要写后缀，因为框架会自动寻找对应的.wxml、.wxss、.js、.json文件并进行编译和组合;<br/>
  其中位于pages数组中的第一项表示小程序的初始页面，即小程序的首页;<br/>
  b. 通过window属性配置窗口状态,如:<br/>
  ![](https://github.com/JS-Even-JS/WXAPP/blob/master/res/app_config.png)<br/>
  c. 通过tabBar属性配置窗口底部的tabBar，所谓tabBar就是指小程序底部有一个可以用于切换页面的tab栏，tabBar至少要配置2个tab，最多配置5个tab，每个tab可以配置文字和图标，图标显示在tab的上方，文本显示在tab的下方，其主要配置如下:<br/>
  ![](https://github.com/JS-Even-JS/WXAPP/blob/master/res/tabBar_config.png)
  ![](https://github.com/JS-Even-JS/WXAPP/blob/master/res/tabBar.png)<br/>
  d. 通过networkTimeout属性配置网络超时时间，如:<br/>
  ```
  "networkTimeout":{
    "request":10000,//设置wx.request网络请求接口的超时时间
    "downloadFile":10000,//设置wx.uploadFile上传文件接口的超时时间
    "debug":true//开启debug模式
  }
  ``` 
* 2.2.2 页面配置文件的配置<br/>
  因为我们可能需要`在不同的页面显示不同的标题`等，所以每个页面也可能需要一个自己的配置文件，而且页面中配置项会覆盖掉app.json中配置的内容;<br/>
  不过，`页面的配置文件中只能配置app.json中的window的配置内容`，所以`页面的配置文件中无须指定window属性，而是直接在花括号内配置`;
  ```
  pages/index/index.json
  {
    "navigationBarTitleText": "首页",
    "navigationBarTextStyle": "black",
    "navigationBarBackgroundColor": "#eeeeee",
    "backgroundTextStyle": "light"
  }
  ```
