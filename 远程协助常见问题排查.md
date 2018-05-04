# 远程协助常见问题排查
- **常见问题**

> 一.TV端未接收到push消息，具体表现为没有出现授权框
> * 可能原因一-----网络原因<br/>
 排查步骤：<br/>
 1.登录225天津服务器，连接数据库<br/>
 2.use tvdoctor;    select * from apiRecent;<br/>
 3.通常情况下会获取4次pushid【记录前两次为system启动方式，后两次为自启方式】。<br/>
 4.如果某一次的push返回为  receive a push message successful   则表明，push后台已经推送消息到电视<br/>

 >* 备注：如排查原因一为正常，则可将问题反馈至刘鹏、谢纯定处，多次出现因后台push版本发布而无法顺利推送的情况<br/>

 > * 可能原因二-----时间戳问题【1分钟之内】<br/>
 排查步骤：<br/>
 1.登录服务器输入date 查看时间 <br/>
 2.如果时间差值在一分钟以上，执行  ntpdate time.nuri.net  同步时间 <br/>

  > * 可能原因三-----找不到远程TV问题<br/>
 排查步骤：<br/>
 1.登录 http://scup.push.skysrt.com/login# <br/>
 2.根据激活id，查询设备信息，得到mac地址 <br/>
 3.根据mac地址反查设备信息，是否得到多个激活id<br/>
 4.找刘鹏组处理<br/>

   > * 可能原因四-----TVID为空问题<br/>
 排查步骤：<br/>
 1.复制服务器代码getTVId.php至在线php服务器<br/>
 2.尝试访问接口，看是否能够正确获取到当前电视的tvid <br/>


 > 二.TV接收到push消息，具体表现为出现授权框，但连接不上pc
 > * 可能原因一-----本地存储的tvid（pushid）与访问服务器所得到的不一致<br/>
 排查步骤：<br/>
 1.串口命令   am start -n com.tianci.push/.MainActivity   查看本地存储的tvid以及相对应的system  pushid <br/>
 2.pc连接时，打开控制台看日志，对比两者的tvid<br/>
 3.pushid的对比需要参照可能原因一的步骤进行<br/>
 4.发现不一致的问题，需要协调 谢纯定/田纪胜 进行处理<br/>

 > * 可能原因二-----代理服务器挂机<br/>
 排查步骤：<br/>
 1.登录服务器 tail -f /var/log/tvdoctor.log <br/>
 2.是否存在tvdoctor.log文件，若不存在，重启代理服务器 cd tvdoctor/      ./TVDoctor.bin &      或者    sh -x shell/detect.sh<br/>
 3.如若还存在问题，重启整个服务器  reboot <br/>

  > * 可能原因三-----websocket问题<br/>
 排查步骤：<br/>
 1.连接时pc端提示websocket错误 <br/>
 2.检查pc是否为内网，更换网络<br/>
 



