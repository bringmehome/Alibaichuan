# 阿里百川接入指南
APICloud平台使用阿里百川的教程

包含入驻阿里百川，以及注册阿里妈妈的PID

##**概述**


>准备工作

1、创建一个APICloud项目，空工程即可，不要添加证书，并引入百川模块，下图chromeDebug是方便调试用，不是必须，使用方法下面会介绍

![](./img/01.png)

2、生成APP，点击下载，到本地

![](./img/02.png)

>开发者入驻

1、首先需要加入百川，[http://baichuan.taobao.com/](http://baichuan.taobao.com/)，按要求一步一步填写过来，成功后如下图

![](./img/03.png)

>阿里妈妈淘客

1、开通阿里妈妈会员，[http://media.alimama.com/user/limit_status.htm?spm=a219a.7395903.0.0.zr6Ni5](http://media.alimama.com/user/limit_status.htm?spm=a219a.7395903.0.0.zr6Ni5),显示以下界面则说明开通成功

![](./img/07.png)

2、此时再回来查看证书权限管理[http://my.open.taobao.com/](http://my.open.taobao.com/)

![](./img/08.png)

>加入淘宝联盟

1、点此加入淘宝联盟[http://pub.alimama.com/?spm=0.0.0.0.CrMksN](http://pub.alimama.com/?spm=0.0.0.0.CrMksN)

![](./img/09.png)

![](./img/10.png)

这个和开店一样，所以需要人工审核，审核时间也有点长，一般1-2个工作日

>开始开发

1、手机需要安装手机淘宝，这个应该大部分人都有吧

2、接口使用参考github：[https://github.com/bringmehome/Alibaichuan](https://github.com/bringmehome/Alibaichuan),里面的测试demo

3、测试登录

![](./img/16.png)


>以上是打测试包的时候用的，正式包需要生成SDK拿到安全图片文件yw_1222.jpg，然后联系作者生成自定义模块。作者邮箱(rocke@feeling.life)

2、生成SDK包，按照以下三个步骤（此步骤目前不是必须）

![](./img/04.png)

选择以下组件

![](./img/05.png)

成功后如下图所示，下载好了后备用

![](./img/06.png)


>其他问题请联系作者邮箱(rocke@feeling.life)

>chrome查看log

1、打开chrome，输入chrome://inspect/#devices，就能看到制作的网页

当然页面必须包含chromeDebug模块，
```js
var chromedebug = null;
apiready = function() {
	chromedebug = api.require('chromeDebug');
	openchromelog();
};
function openchromelog() {
	chromedebug.openDebug(function(ret, err) {
		if (212 == ret.code) {
			alert(JSON.stringify(ret));
		} else {
			console.log(ret);
		}
	});
}
```

![](./img/11.png)

2、点击inspect，首次打开应该是白板如下

![](./img/12.png)

你需要翻墙了，用vpn工具翻墙，我喜欢用赛风，因为免费的嘛，

![](./img/13.png)

3、连接成功后，你再次点击inspect，需要等待一会，如果不行那就要多试几次，因为免费的软件总归没那么稳定。等出现以下界面，即可

![](./img/14.png)

![](./img/15.png)



[回去继续看APICloud文档](http://docs.apicloud.com/端API/开放SDK/alibaichuan)
