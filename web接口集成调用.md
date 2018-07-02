# web接口集成调用

**框架引用**
> 1.webappdemo引用地址<br>
> * git：https://github.com/xavier0509/newWebappdemo.git<br>
> * 将该目录下的所有文件复制到工作目录下（开发仅仅是对index.html页面以及相对应的css和js进行更改）

> 2.重写html页面以及js脚本
> * html内容需要包含在一个id = "deviceready" 的div中【此id名可进行更改，但需要在js中进行监听】，在js文件中，将对其进行监听 <br>
> * demo中的js/index.js可作为一个完整的参考例子，包含所有的接口调用方式<br>
> * 开发的重点在于对triggleButton:function()函数的重写/修改<br>
> *  在此之前的函数可归结为事件的监听加载过程，针对返回、主页键等进行自定义处理<br>
（receivedEvent: function(id)的内容根据需求进行增减）<br>

> 在完成页面开发之后，先自行在本地服务器上进行测试，代码上传到服务器上，在电视上通过CordovaTest.apk进行测试。在确认没有问题之后，发出邮件给运维人员进行正式环境(https://webapp.skysrt.com) 的部署。

- **接口调用方法【建议在酷开5.5（含）以上的版本使用】**


**系统启动、获取信息类**
<table>
  <tr>
    <th width=40%, bgcolor=yellow >调用方法</th>
    <th width=10%, bgcolor=yellow>功能说明</th>
    <th width=30%, bgcolor=yellow>所需参数</th>
    <th width="20%", bgcolor=yellow>结果/备注</th>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startLocalMedia </td>
    <td> 启动本地媒体  </td>
    <td>  无 </td>
    <td>  打开本地媒体界面 4.x的版本不支持</td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startTVSetting </td>
    <td> 启动电视设置 </td>
    <td>  无 </td>
    <td> 打开电视设置界面  4.x的版本不支持</td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startSourceList</td>
    <td> 启动信号源  </td>
    <td>  无 </td>
    <td>  打开信号源选择界面 4.x的版本不支持</td>
  </tr>
   <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startUserSetting </td>
    <td> 启动账户中心  </td>
    <td>  无 </td>
    <td>  启动用户账户中心 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startNetSetting </td>
    <td> 启动网络设置 </td>
    <td>   </td>
    <td> 打开网络设置界面  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startBlueToothSetting </td>
    <td> 启动蓝牙设置  </td>
    <td>   </td>
    <td>  打开蓝牙设置界面 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startMessageBox </td>
    <td> 启动消息盒子 </td>
    <td>   </td>
    <td> 酷开5.5版本以上才具有消息盒子功能  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startSystemUpgrade </td>
    <td> 启动系统升级  </td>
    <td>   </td>
    <td>  打开系统的升级页面 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.getDeviceLocation </td>
    <td> 获取定位信息 </td>
    <td>   </td>
    <td> 设备定位信息的json串  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.getUserAccessToken</td>
    <td> 获取accesstoken  </td>
    <td>   </td>
    <td>  用户的token值 登录前提下才有token </td>
  </tr>
  
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.getDeviceInfo</td>
    <td> 获取设备信息  </td>
    <td>   </td>
    <td> 含有屏幕尺寸（panel）、机芯（chip）、机型（model）、mac地址、安卓版本（androidsdk）、酷开版本（version）、激活id（activeid）、电视id（devid）、chipid等信息的json串 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.isNetConnected </td>
    <td> 获取网络连接状态 </td>
    <td>   </td>
    <td> true（联网状态）/false（无网络状态）  </td>
 </tr>
 
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.hasCoocaaUserLogin </td>
    <td> 用户是否登录  </td>
    <td>   </td>
    <td>  true：已经登录        false：未登录 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.getUserInfo</td>
    <td> 获取用户信息 </td>
    <td>   </td>
    <td> 当前用户的信息json串  </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.setCoocaaUserLogout</td>
    <td> 退出登录 </td>
    <td>   </td>
    <td> 退出当前登录账户  </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.getBaseInfo</td>
    <td> 获取设备baseinfo </td>
    <td>   </td>
    <td> 获取baseinfo，包括内存信息、存储信息  </td>
  </tr>
  </table>


   **影视、主页相关**
  <table>
  <tr>
    <th width=40% bgcolor=yellow >调用方法</th>
    <th width=10% bgcolor=yellow>功能说明</th>
    <th width=30% bgcolor=yellow>所需参数</th>
    <th width="20%", bgcolor=yellow>结果/备注</th>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startMovieHistory </td>
    <td>  启动影视历史  </td>
    <td>  无 </td>
    <td> 打开影视历史界面4.x的版本不支持</td>
 </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startMovieList </td>
    <td> id跳转影视列表  </td>
    <td>  参数listid为输入/获取到的影视id </td>
    <td> 跳转打开该id的影视列表  </td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startMovieDetail </td>
    <td> id跳转影视详情   </td>
    <td> 参数detailid为输入/获取到的影视详情id  </td>
    <td>  跳转打开该id的影视详情 </td>
  </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startMovieMemberCenter </td>
    <td> 启动影视会员中心  </td>
    <td>   </td>
    <td>  启动打开影视会员中心 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startMovieHome</td>
    <td> 启动影视主页 </td>
    <td>   </td>
    <td> 打开影视主页面  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startMovieTopic</td>
    <td>  id启动影视专题页  </td>
    <td>  参数topicid为输入/获取到的影视专题的id </td>
    <td>  跳转打开该id对应的影视专题页 </td>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startMyCoupon</td>
    <td>  启动我的优惠券列表  </td>
    <td>  参数：sign--约定的业务线对应sign值/openId--用户的openid/appId--对应业务的appid值/businessLine--movie、education、allMovie/business_type--0、1、-1</td>
    <td>  启动我的优惠券 </td>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAllCoupon</td>
    <td>  启动优惠券列表  </td>
    <td>  参数：sign--约定的业务线对应sign值/openId--用户的openid/appId--对应业务的appid值/businessLine--movie、education、allMovie/business_type--0、1、-1</td>
    <td>  启动优惠券 </td>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startHomeTap</td>
    <td>  跳转主页指定tab  </td>
    <td>  参数：actionName为需要启动的action名【此方法涉及3个不同action】/tabid为指定tab的id值</td>
    <td>  6.x系统actionName为“coocaa.intent.action.HOME”，5.x系统先判断一下persist.service.homepage.pkg这个prop，如果值是com.tianci.movieplatform，那么action是coocaa.intent.action.HOME.Translucent  否则 action就是coocaa.intent.movie.home</td>
  </tr>
  </table>
  
  
  **应用圈相关**
  <table>
  <tr>
    <th width=40%, bgcolor=yellow >调用方法</th>
    <th width=10%, bgcolor=yellow>功能说明</th>
    <th width=30%, bgcolor=yellow>所需参数</th>
    <th width="20%", bgcolor=yellow>结果/备注</th>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startAppStore</td>
    <td> 启动应用圈	 </td>
    <td>   </td>
    <td> 打开应用圈  </td>
 </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startMyGames</td>
    <td> 启动我的游戏  </td>
    <td>   </td>
    <td>  打开我的游戏界面 4.x的版本不支持</td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startMyApps</td>
    <td> 启动我的应用 </td>
    <td> mode: child / 其他，代表启动的是哪个模式下的程序  </td>
    <td> 启动我的应用界面 4.x的版本不支持 </td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAppStoreBD</td>
    <td> 启动应用圈榜单	  </td>
    <td>  rankId为榜单id </td>
    <td>  跳转打开应用圈榜单页面 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startAppStoreSort</td>
    <td> id跳转应用圈分类	 </td>
    <td> sortid为输入/获取到的应用圈分类id  </td>
    <td> 跳转到该id对应的应用圈分类页面  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAppStoreList</td>
    <td> id跳转应用圈列表  </td>
    <td>  参数listid为输入/获取到的应用圈列表id </td>
    <td>  跳转到该id对应的应用圈列表 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startAppStoreDetail</td>
    <td> id跳转应用圈详情 </td>
    <td>  detailid为输入/获取到的应用圈详情id </td>
    <td> 跳转到该id对应的应用圈详情页面  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAppStoreZone</td>
    <td> id跳转应用圈专题  </td>
    <td>  zoneid为输入/获取到的应用圈专题id </td>
    <td>  跳转到该id对应的应用圈专题页面 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startOrCreateDownloadTask</td>
    <td> 跳转或下载一个任务 </td>
    <td>  1.下载路径
2.MD5校验值
3.下载文件名称
4.下载的包名
5.appid
6.icon图片地址 </td>
    <td> 打开或者在应用圈中进行下载  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startGameCenter</td>
    <td> 启动酷游吧  </td>
    <td>   </td>
    <td>  打开酷游吧界面 </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startGameArsenal</td>
    <td> 启动游戏军火库 </td>
    <td>   </td>
    <td> 打开酷游吧游戏军火库页面  </td>
 </tr>
 <tr>
    <td bgcolor=#00FF00> coocaaosapi.startGameCenterList</td>
    <td> 启动游戏列表页 </td>
    <td>  gamelistid为游戏列表页id / gametitleid为列表页title</td>
    <td> 打开游戏列表页  </td>
 </tr>
 <tr>
    <td bgcolor=#00FF00> coocaaosapi.startGameCenterDetail</td>
    <td> 启动游戏详情页 </td>
    <td>  gamedetailid为详情页id </td>
    <td> 打开游戏详情页  </td>
 </tr>

 <tr>
    <td bgcolor=#00FF00> coocaaosapi.startAppShop</td>
    <td> 启动酷开商城首页  </td>
    <td>  </td>
    <td>   </td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAppShopList</td>
    <td> 启动酷开商城列表页    </td>
    <td> 参数id为输入/获取到的商城列表id   title为列表页title </td>
    <td> 启动商城列表页  </td>
  </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAppShopDetail</td>
    <td> 启动购物图文详情页  </td>
    <td>  id为图文详情页id </td>
    <td>   </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startAppShopZone</td>
    <td> 启动酷开商城专题页 </td>
    <td>   专题页id</td>
    <td>   </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAppShopZoneList</td>
    <td> 启动酷开商城专题列表页    </td>
    <td>   </td>
    <td>   </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startAppShopVideo</td>
    <td> 启动酷开商城视频详情页 </td>
    <td>   视频页id，url，名称</td>
    <td>   </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startAppShopBUYING</td>
    <td> 启动购物酷开商城活动列表页    </td>
    <td> 活动列表页id  </td>
    <td>   </td>
  </tr>
 </table>
 

  
  
   **监听调用**
  <table>
  <tr>
    <th width=40%, bgcolor=yellow >调用方法</th>
    <th width=10%, bgcolor=yellow>功能说明</th>
    <th width=30%, bgcolor=yellow>所需参数</th>
    <th width="20%", bgcolor=yellow>结果/备注</th>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.addPurchaseOrderListener</td>
    <td> 支付状态监听  </td>
    <td> </td>
    <td>  在回调函数中处理监听事件 </td>
 </tr>
 <tr>
    <td bgcolor=#00FF00> coocaaosapi.removePurchaseOrderListener</td>
    <td> 移除支付状态监听  </td>
    <td> </td>
    <td>   </td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.addUserChanggedListener</td>
    <td> 账户状态变更监听	  </td>
    <td>   </td>
    <td>  在回调函数中处理监听事件 </td>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.removeUserChanggedListener</td>
    <td> 移除账户状态变更监听   </td>
    <td>   </td>
    <td>   </td>
  </tr>
 
 <tr>
    <td bgcolor=#00FF00> coocaaosapi.addUSBChangedListener</td>
    <td> USB状态监听	 </td>
    <td> </td>
    <td> 在回调函数中处理监听事件  </td>
 </tr>
 <tr>
    <td bgcolor=#00FF00> coocaaosapi.removeUSBChangedListener</td>
    <td> 移除USB状态监听【u盘】  </td>
    <td> </td>
    <td>   </td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.addNetChangedListener</td>
    <td> 网络状态变更监听	  </td>
    <td>   </td>
    <td> 在回调函数中处理监听事件  </td>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.removeNetChangedListener</td>
    <td> 移除网络状态变更监听   </td>
    <td>   </td>
    <td>   </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.addAppTaskListener</td>
    <td> APK下载监听	 </td>
    <td> </td>
    <td> 在回调函数中处理监听事件  </td>
 </tr>
 <tr>
    <td bgcolor=#00FF00> coocaaosapi.removeAppTaskListener</td>
    <td> 移除APK下载监听   </td>
    <td> </td>
    <td>   </td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.addCommonListener;
        }) </td>
    <td> 通用监听【新浏览器】	  </td>
    <td>   </td>
    <td> 在回调函数中处理监听事件  </td>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> coocaaosapi.removeCommonListener;
        }) </td>
    <td> 移除通用监听【新浏览器】   </td>
    <td>   </td>
    <td>   </td>
  </tr>
  </table>
  
  
   **业务相关**
  <table>
  <tr>
    <th width=40%, bgcolor=yellow >调用方法</th>
    <th width=10%, bgcolor=yellow>功能说明</th>
    <th width=30%, bgcolor=yellow>所需参数</th>
    <th width="20%", bgcolor=yellow>结果/备注</th>
  </tr>
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.notifyJSMessage</td>
    <td> Web页面消息上传	 </td>
    <td> webInfoStr为字符串  </td>
    <td>   </td>
 </tr>
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.notifyJSLogInfo</td>
    <td> Web日志提交上传	  </td>
    <td> eventId为字符串，是日志项名称
Ddata是json形式的字符串。允许为空，但必须传”{}”  </td>
    <td>   </td>
  </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.getPropertiesValue</td>
    <td> 获取属性  </td>
    <td>  参数为propertiesKey的属性名 </td>
    <td>   </td>
  </tr>

 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.startCommonWebview</td>
    <td> 启动web播放器 </td>
    <td>  视频id,视频uri,悬浮框tips,播放器高height,播放器宽width,广告曝光第三方的call_url,视频类型type,视频name, </td>
    <td>   </td>
  </tr>
  
  
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.notifyJSLogResumeInfo</td>
    <td> 用于活动中心的曝光事件，可采集时长，与notifyJSLogPauseInfo成对出现</td>
    <td> eventId日志项名称、ddata拓展参数</td>
    <td> 此方式为非实时提交，可能会有丢失，建议仅作参考  </td>
 </tr>
 
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.notifyJSLogPauseInfo</td>
    <td> 用于活动中心的曝光事件，可采集时长，与notifyJSLogResumeInfo成对出现  </td>
    <td> 只有 eventId日志项名称 </td>
    <td> 此方式为非实时提交，可能会有丢失，建议仅作参考  </td>
  </tr>
   
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.getAppInfo</td>
    <td> 获取app相关信息  </td>
    <td> 参数传递一个对象，key为"pkgList",value为应用包名的数组。即{pkgList:["com.tianci.user","com.tianci.movieplatform"]} </td>
    <td>   </td>
  </tr>
   
 <tr>
    <td bgcolor=#eeeeee> coocaaosapi.setBusinessData</td>
    <td> 设置Business相关信息【无回调】  </td>
    <td> cc_type区分同步、异步。默认为异步（async）,只有传sync时才会更改;cc_data为json形式的字符串 </td>
    <td> 如需要得到返回结果，采用getBusinessData</td>
  </tr>
  
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.getBusinessData</td>
    <td> 获取Business相关信息【有回调】</td>
    <td>cc_type区分同步、异步。默认为异步（async）,只有传sync时才会更改;cc_data为json形式的字符串</td>
    <td></td>
 </tr>
 
  <tr>
    <td bgcolor=#00FF00> coocaaosapi.startParamAction</td>
    <td> 启动传参action页面</td>
    <td>包名、版本号、startActivity、action、action名、拓展参数[{key1:"value1"},{key2:"value2"}]</td>
    <td></td>
 </tr>
  
  </table>
  
