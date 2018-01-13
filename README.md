# wxSportCrawler
一套抓取微信运动真实数据、并将微信运动数据用于活动/场景的程序

关键字：微信运动、微信步数、运动步数、wechat sport、wechat step、微信硬件

Demo：
http://wxsportdemo.grplpl.com/

### 功能描述
**1、抓取个人的微信运动数据，形成实时数据、日数据、累计数据和其他按照需求进行统计的数据**

具体可以看Demo截图

(1)当前时间的步数实时显示

![](//dn-cnode.qbox.me/FtknJahVHz6mJCL9MjL5LOsrYnBU)


(2)月步数按日显示

![](//dn-cnode.qbox.me/FiB1opFZqjTEe2fPOgHrfnkddLiI)


(3)日实时步数排行榜

![](//dn-cnode.qbox.me/FhnBZbyxMy1jLpiYUlnh63vuwx3-)


(4)累计步数排行榜

![](//dn-cnode.qbox.me/FocGicpPFWds_LqVNegIerQ_Was1)


**2、每日定时由个人号机器人提示日步数，加强活动粘性**

Demo截图

![](//dn-cnode.qbox.me/FohyK-FBSbL5N-s68y5K6lH8WRh2)

### 各种流程图

**1、个人微信端报名流程图**

![](//dn-cnode.qbox.me/Fn1C6DJH-IhK_BH_019Rk44VlItZ)


**2、客户服务器拉取数据流程图**

![](//dn-cnode.qbox.me/Fn0gzn7Weo4JCv4O8ZHORsAaH-Io)


**3、群发日提醒到个人微信端流程图**

![](//dn-cnode.qbox.me/FsHwaZ6HKajmQgmQcXQBwtzRnLu5)


### 技术综述和难点

(1)如何抓取微信运动数据

通过抓取微信PC客户端的Cookie，攻克抓取微信运动数据的技术难点。

看下图，通过fiddler抓取到微信PC端的https的登陆cookie。

![](//dn-cnode.qbox.me/FtqlfporF4JnYR8iH8G5WAd9UFcC)


(2)服务器端程序，模拟登陆到微信PC客户端，轮询各个微信号的微信运动数据，抓取到本地数据库。

这步没有多少难点，只要熟悉模拟登陆即可完成。

但是程序的**稳定性**是一个很大的考验。实际开发中遇到了cookie过期、抓取超时等问题，花了很长时间一一解决。

(3)服务器端程序需对外提供Restful接口（需认证），给用户调取微信运动数据。

这步没有难点，就在于如何设计这个认证的接口。

(4)与微信个人Bot相关的开发

下面简称“微信个人号Bot”为“Bot”。

这里解释一下，因为按照流程图1和3，都需要用到一个微信个人号（就是普通的微信号）来实现报名和群发功能，所以这个Bot必须是一个实现了全功能的微信模拟登陆模拟操作的Bot。思路其实和github上已经有的不少项目是一样的。

我这里实现的Bot，在稳定性方面要稍微强一点。实际开发上，会遇到无规律掉线（这个最恐怖）、群发控制等问题，需要一点一点解决。

Bot的报名成功提示图：

![](//dn-cnode.qbox.me/FqTV5BCfjz5IYVEgW2NyKYJ5tSF1)


### 商务合作

这里已经实现了一个可用的API，可提供有限的试用。

具体请联系我，QQ 14707685，注明“微信运动数据”。

请关注这个项目，https://github.com/klausgao/wxSportCrawler/
