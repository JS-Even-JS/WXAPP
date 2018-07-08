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
  #### 备注
  ```
  pages数组的第一项必须是tabBar的list数组的一员,否则无法显示tabBar菜单;
  ```
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
### 2.3 逻辑层js文件
由于`前端也需要对来自后台的数据进行进一步处理，并且界面中的数据也可能因为用户触发一些操作而导致发生变化`，所以需要一个逻辑层来实现数据的加工和处理;<br/>
逻辑层将数据进行处理后发送给视图层，同时接收视图层的事件反馈;
* 2.3.1 用App函数注册小程序
  每个微信小程序必须在根目录下的app.js文件中进行`小程序的注册`，并且`只能注册一次`;注册小程序使用全局的App()函数,然后传递一个对象作为参数，对象的属性为一些钩子函数和一些特定的属性，如:<br/>
  a. onLaunch钩子，当小程序初始化的时候会首先进入onLaunch钩子函数，`只会触发一次`;onLaunch钩子中主要进行一些`本地存储(wx.getStorageSync()和wx.setStorageSync())`、`登录wx.login()`、`获取用户信息wx.getSetting()`等操作<br/>
  b. onShow钩子，当小程序启动之后(`onLaunch之后`)，或者从后台进入前台显示的时候，就会触发onShow钩子;<br/>
  c. onHide钩子，当小程序从前台进入后台的时候就会触发onHide钩子;<br/>
  d. globalData属性，用于设置一些全局的数据;<br/>
 
 * 2.3.2 用Page()函数注册页面
   每个页面必须使用Page()函数进行注册页面才会生效，也是传递一个对象作为参数，可以配置一些`页面的生命周期函数`、`自定义的事件处理函数`、`data属性用于定义页面中使用到的数据`;Page页面的生命周期钩子有:<br/>
   a. onLoad钩子，当页面加载完成就会调用该钩子函数，`一个页面只会调用一次`;<br/>
   b. onShow钩子，当页面显示时调用该钩子函数，每次打开页面都会调用一次;<br/>
   c. onReady钩子，当页面数据初次渲染完成调用该钩子函数，`一个页面只会调用一次`，代表页面已经准备妥当，可以和视图层进行交互了;<br/>
   d. onUnload钩子，当页面卸载的时候调用该函数;<br/>
除了可以在Page中配置一些页面的生命周期函数之外，我们还可以配置一些事件处理函数，例如:<br/>
```
<view bindtap="viewTap">单击测试</view>
Page({
  viewTap:function(){
    console.log("您点击了按钮!");
  }
});
```
当然，我们可以通过data属性来设置页面的初始数据，当页面中数据发生变化的时候，我们可以通过this.setData()方法，传递一个对象作为参数，对象的属性为要修改的data中的属性，属性值为变化后的数据，如:<br/>
```
Page({
  data:{
    motto: 'Hello World'
  },
  viewTap:function(){
    this.data.motto = "XiXi";// 这种方式是无法实现动态数据更新的，这样只能改变Model中的数据，但是View中的数据并不会动态更新;c
    this.setData({ // 只有通过this.setData()方法才能实现数据的动态更新
      motto:"Haha"
    });
  }
})
```
### 2.4 页面描述文件wxml
* 2.4.1 wxml常用的标签 <br/>
  wxml文件中常使用的标签有: `<view>标签`、`<image>标签`、`<text>标签`;<br/>
* 2.4.2 wxml中的数据绑定 <br/>
  wxml使用{{}}来进行数据的双向绑定，页面中的动态数据均来自Page({})方法中配置的data，如:<br/>
  ```
    <text class="user-motto">{{motto}}</text>
  ```
* 2.4.3 wxml条件渲染 <br/>
  a. wx:if条件渲染,wx:if的属性值用一个双引号进行包裹，并且要将内部表达式放在{{}}中，否则会被当做一个字符串进行处理，其也有wx:elif来表示else if的情况，还有wx:else表示else，不过wx:else不用跟任何属性值,如: <br/>
  ```
  <view wx:if="{{length > 5}}">1</view>//当length值大于5的时候显示该组件
  <view wx:elif="{{length > 2}}">2</view>//当length值小于5且大于2的时候,显示该组件
  <view wx:else>3</view> //当length值小于2的时候，显示该组件,wx:else不需要跟任何属性值
  ```
  b. block wx:if条件渲染 <br/>
  上面的wx:if是控制一个组件的渲染，当需要控制多个组件的时候，我们就需要使用到<block wx:if></block>了，如:<br/>
  ```
   <block wx:if="{{condition}}">
      <view> view1</view>
      <view> view2</view>
   </block>
  ```
 * 2.4.4 wxml列表渲染 <br/>
   a. wx:for 列表渲染,我们只需要让wx:for的值等于"{{data中的数组变量}}"即可，其中有index变量表示数组的索引，item表示数组的元素，如: <br/>
   ```
    <view wx:for="{{users}}">
      {{index}}-{{item.name}}
    </view>
   ```
   b. 当然我们除了可以使用默认的index和item之外，我们还可以重命名，可以通过wx:for-index="新的索引名"，wx:for-item="新的变量名"，如:<br/>
   ```
    <view wx:for="{{users}}" wx:for-index="id" wx:for-item="user">
       {{id}}-{{user.name}}
    </view>
   ```
   c. wx:for嵌套，如输出一个乘法表<br/>
   ```
    <view wx:for="{{[1,2,3,4,5,6,7,8,9]}}" wx:for-item="i">
      <view wx:for="{{[1,2,3,4,5,6,7,8,9]}}" wx:for-item="j">
          <view wx:if="{{i <= j}}">
              {{i}} * {{j}} = {{i * j}}
          </view>
      </view>
    </view>
   ```
   d. block wx:for 也可以使用<block>标签进行多个组件渲染;<br/>
  
 * 2.4.5 使用模板  
   a. 定义模板，定义模板也是在wxml文件中进行，并且使用<template>标签，通过name属性给模板命名，<template>模板内部可以定义一些变量，然后在使用模板的时候将数据传入即可，如：<br/>
 ```
   <template name="userTemp">
    <view>
        <view>姓名:{{item.name}}</view>//这里定义了一个item变量，传递数据的时候也必须传递一个数据并赋值给item
    </view>
   </template> 
 ```
  b. 使用模板，使用模板的时候也是使用<template>标签，但是需要添加is属性，属性值为模板名称，同时添加一个data属性，将数据传入模板中，如:<br/>
  ```
   <view wx:for="{{users}}" wx:for-index="id" wx:for-item="user">
      <template is="userTemp" data="{{item:user}}"></template>//将user对象赋值给item变量，模板内部就可以使用这个item变量了
   </view>
  ```
* 2.4.6 引入其他页面
  引入其他页面有两种方式，一种是通过import的方式，另一种是通过include的方式，如:
  ```
    <import src="template.wxml"/>
    <include src="header.wxml"/>
  ```
### 2.5 页面的事件
  * 2.5.1 事件类型
    事件类型分为:`冒泡事件`、`非冒泡事件`;
    冒泡事件:`touchstart`、`touchmove`、`touchcancel`、`touchend`、`tap(相当于click事件)`、`longtap(长按事件)`;<br/>
    非冒泡事件: `<form>的submit事件`、`<input>的input事件`、`<scroll-view>的scroll事件`;
  * 2.5.2 事件绑定
    绑定事件的时候，需要在事件名前加上bind或者catch，其中bind开头的事件绑定不会阻止事件冒泡，catch开头的事件绑定则会阻止事件冒泡;如:<br/>
    ```
        <view class="fuView" bindtap="test">
            fuView
            <view class="ziView" catchtap="testBubble">
                 ziView
            </view>
      </view>
    如果ziView中使用的是bindtap来绑定事件，那么当用户点击ziView的时候，tap事件就会冒泡到fuView元素上;
    如果ziView中使用的是catchtap来绑定事件，那么当用户点击ziView的时候，tap事件就不会冒泡到fuView元素上;
    ```
  * 2.5.3 事件对象
    我们绑定事件处理函数的时候，不能通过`事件处理函数(event)`的方式给事件处理函数传递对象，而是直接写事件处理函数的名字即可，否则会报错;<br/>
    事件对象会自动传递到事件处理函数中，我们只需要定义一个event参数进行接收即可,常见的事件对象属性有:<br/>
    a. type属性，返回当前触发的事件类型，如tap;<br/>
    b. timeStamp属性，返回一个毫秒数，表示从该页面打开到触发事件所经过的毫秒数;<br/>
    c. target属性，返回一个触发事件的源组件，其有id(触发事件的组件id)、dataset(表示触发事件的组件对象上data-属性名设置的数据)、offsetLeft(触发事件的组件对象的水平偏移量)、offsetTop(触发事件的组件对象的垂直偏移量)等属性;<br/>
    d. currentTarget属性，返回的事件绑定组件对象，和target对象一样，具有id、dataset、offsetLeft、offsetTop等属性;<br/>
    e. touches属性,保存触摸点的信息，其是一个数组，用于存放触摸点，每个触摸点都有pageX、pageY属性(距离文档左上角的距离)和clientX、clientY属性(距离页面可视区(屏幕去除导航条)左上角的距离);<br/>
  * 2.5.4 微信小程序像素问题
    微信小程序中，提供了一种rpx单位，即responsive pixel，可以根据屏幕宽度进行自适应，其规定任何屏幕中，750rpx都等于设备实际宽度，即不管在什么设备下，750rpx宽度就能占满全屏;而如果给元素设置为设备的实际分辨率，那么也能让元素占满全屏，如iPhone5屏幕的实际分辨率为320px*568px，那么给元素width设置为320px也能让元素宽度占满全屏，所以在iPhone5下，1px===2.34375rpx;<br/>
    微信小程序规定，任何设备的实际宽度都是20rem;如iPhone5下，320px === 750rpx === 20rem,所以 16px === 37.5rpx === 1rem;<br/>
  * 2.5.5 让页面高度占满全屏
    可以通过给页面根元素page设置一个height值为100%,微信小程序中会默认将wxml中的内容加载到<page>元素中;
 ## 第三章 本地存储和页面跳转
 ### 将数据保存到本地
 * 3.1 保存数据到本地的接口，其实就是通过键值对的形式将数据保存到本地，微信提供了两个接口，一个是异步的;另一个是同步的:
 ①wx.setStorage(),这是一个异步接口,其参数是一个对象，对象中可以配置5个属性，如:<br/>
   a. key,本地缓存中的key名称;<br/>
   b. data,本地缓存中key对应的数据，可以是字符串，也可以是对象;<br/>
   c. success,接口调用成功的回调函数;<br/>
   d. fail,接口调用失败的回调函数;<br/>
   e. complete,接口调用结束的回调函数，不管是失败还是成功都会调用该回调函数;<br/>
  注意，如果两次保存数据的时候，key值相同，那么第二次保存的数据会覆盖调掉上一次保存的数据;<br/>
 ②wx.setStorageSync(),这是一个同步接口,因此不需要success、fail、complete等回调函数,其只需要传递两个参数，key和data即可，如:<br/>
   wx.setStorageSync(KEY,DATA);<br/>
 ### 从本地缓存中获取数据
 * 3.2 和保存数据一样，获取数据也提供了两个接口，一个是同步的，一个是异步的，如:<br/>
 ①wx.getStorage(),这是一个异步接口，用法和setStorage()差不多，获取到的数据会放在回调函数的参数中(res)，如:<br/>
  res = {data:key对应的内容}<br/>
 ②wx.getStorageSync(),这是一个同步接口，传入要获取的key名称，即可获取到key对应的值;<br/>
 ### 从本地缓存中清除数据
 * 3.3 和保存数据一样，清除数据也提供了两个接口，一个是同步的，一个是异步的，如:<br/>
 ①wx.clearStorage(),这是一个异步接口，不需要传递任何参数，即可清除所有的缓存;<br/>
 ②wx.clearStorageSync(),这是一个同步接口，也不需要传递任何参数，即可清除所有的缓存;<br/> 
 ### 页面跳转
 * 3.4 页面跳转，有两种方式跳转，如:<br/>
 ①wx.navigateTo接口，这个接口会保留当前页面，并跳转到应用中的某个页面，也就是说跳转前的页面仍然保留在内存中，没有被销毁，在跳转到的新页面中，可以通过wx.navigateBack接口返回到跳转前的页面;跳转或的页面的左上角会自带返回按钮;<br/>
 ②wx.redirectTo接口，这个接口跳转前会关闭跳转前的页面;跳转后的页面中没有返回按钮;<br/>
 ## 第四章 表单相关控件
 ### 用form组件收集信息
 * 4.1 form组件特殊属性，如:<br/>
   ①report-submit:是否返回formId用于发送模板消息;<br/>
   ②bindsubmit:绑定submit提交事件，当点击提交按钮的时候就会触发指定的事件处理函数，事件处理函数可以通过事件对象e.detail.value获取到整个表单内容的数据对象,不过要想点击提交按钮触发submit事件，这个提交按钮必须指定formType值为submit，formType="submit";<br/>
   ③bindreset:绑定reset重置事件，当点击重置按钮的时候就会触发指定的事件处理函数，同样这个重置按钮必须指定formType的值为reset,formType="reset"，点击重置按钮后并不是回到页面绑定时候的初始值，而是回到控件的默认值;<br/>
 * 4.2 radio和radio-group组件,如:<br/>
   ①radio组件是一个单选按钮组件，其必须放在radio-group组件中才能获取到单选按钮对应的值，因为我们必须将name属性设置到radio-group组件上，value属性设置在radio组件上，并且处于radio-group组件中的radio组件只能有一个被选中,name属性设置到radio组件上无效;<br/>
   ②radio-group组件作为一个容器组件，本身不需要设置value和checked属性，但是其可以绑定change事件，当用户选择不同的radio按钮的时候，就会触发对应的bindchange事件,事件处理函数中也可以通过事件对象e.detail.value获取到对应的单选按钮的属性值;<br/>
   ③radio组件可以设置value属性(radio组件对应的值)、checked属性(选中)、disabled属性(禁用);<br/>
 * 4.3 checkbox和checkbox-group组件<br/>
   ①checkbox和checkbox-group组件的用法和radio组件一致,只不过提交的时候checkbox的值是一个数组;<br/>
 * 4.4 picker组件<br/>
   picker组件就是所谓的下拉选择列表，其有三种模式，可以通过mode属性进行设置，如:<br/>
   ①selector,即默认为普通选择器，可以不设置，默认为selector，当mode值为selector的时候，range属性有效，其属性值为一个数组，即下拉选择列表项，同时可以给其设置一个value属性，value属性值为一个整数即对应数组中的索引值，可以给其绑定bindchange事件，当滑动下拉列表选择不同的值的时候，就会触发bindchange事件，可以通过事件对象e.detail.value获取到选择的索引值，然后在事件处理函数中改变索引值即可选择不同的下拉选项;<br/>
    同时要注意，我们必须在picker组件内部添加文字显示，然后点击picker组件中的文字即可弹出对应的下拉列表;<br/>
   ②date,当mode值为date的时候，就变成了一个日期选择器，其有一个value属性，属性值为一个日期，格式为YYYY-MM-DD，当打开日期选择器的时候就会默认选择到指定的日期上，即value的属性值;其也可以通过绑定bindchange事件，然后通过事件对象e.detail.value获取到选择的日期，然后通过this.setData()进行更新即可;同时还可以设置start和end属性，表示日期选择器的可滚动范围，即日期的起止时间;<br/>
   ③time,当mode值为time的时候，就变成了一个时间选择器，其有一个value属性，属性值为一个时间，格式为HH:MM，当打开时间选择器的时候就会默认选择到指定的时间上，即value的属性值;其也可以通过绑定bindchange事件，然后通过事件对象e.detail.value获取到选择的时间，然后通过this.setData()进行更新即可;<br/>
 ### 我们给picker组件添加上name属性，在提交表单的时候就可以捕获到对应picker中的属性值了;不过默认选择器selector获取到的是索引值<br/>
* 4.5 textarea组件
  ①textarea即多行文本输入框;<br/>
* 4.6 swiper轮播图组件
  ①swiper轮播图组件是一个容器组件，其中放置的组件会轮换显示，但是swiper组件中只能放置名为swiper-item的组件，其他组件则会被自动删除，当然swiper-item组件内部可以放置其他要显示的组件，比如image组件;<br/>
  ②swiper组件可以设置很多属性，如:<br/>
    a. indicator-dots:设置是否在界面中显示面板指示点，默认为false表示不显示;<br/>
    b. autoplay:设置是否自动切换swiper-item，默认为false即表示不自动播放;<br/>
    c. current:是一个索引值，默认为0表示显示第一个swiper-item;<br/>
    d. interval:是一个时间毫秒值，表示自动切换页面的时间间隔;<br/>
    e. duration:也是一个时间毫秒值，表示页面滑动动画时长;<br/>
    f. bindchange:可以绑定一个change事件，可以通过e.detail.current获取到当前的current，即切换到下一张图片对应的current;<br/>
    g. vertical:是一个布尔值，用于切换指示点的显示位置，默认为false即在水平方向显示,可以控制轮播图的滑动方向;  
 ## 第五章 微信小程序交互反馈
 ### 等待提示
 * 5.1 loading组件<br/>
   ①loading组件主要就一个属性即hidden，用于控制组件的显示和隐藏，同时其可以绑定一个bindchange事件，用于处理单击加载提示的事件;loading组件内可以添加文字，添加的文字会出现在loading组件中<br/>
   ②我们可以通过setInterval定时器，每隔一秒改变一下时间，实现倒计时退出;
 * 5.2 totast组件<br/>
   ①loading组件默认会有一个旋转的动画图标，在有的时候这种动画就不合事宜，所以又提供了一个toast组件，其不会有动画，但是会显示一个对勾;toast组件相对于loading组件有更多属性设置，如:<br/>
   a.hidden:用于控制组件的显示和隐藏;<br/>
   b.duration:设置一个时间毫秒值，表示多长时间之后自动触发bindchange事件;<br/>
   c.bindchange:可以绑定一个change事件，用于控制tast的显示和隐藏等操作;<br/>
 * 5.3 
   
