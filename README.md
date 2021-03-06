# 阿里百川接入指南


APICloud平台使用阿里百川的教程，包含入驻阿里百川，以及注册阿里妈妈的PID

因为此模块需要用到以下三个东西：

1、阿里妈妈的淘客PID

2、加入淘宝联盟，用于查看收益，并把收益转入支付宝

3、生成SDK，因为打正式包的时候需要

>指南目录

* [绑定依赖的模块](#bindyilai)

* [开始开发](#开始开发)

* [打正式包](#打正式包)

* [开发者入驻](#开发者入驻)

* [阿里妈妈淘客](#阿里妈妈淘客)

* [加入淘宝联盟](#加入淘宝联盟)

##**概述**

首先建议使用自己的证书，包括安卓和iOS的

<div id="bindyilai"></div>

#**绑定依赖的模块**<div id="bindyilai"></div>

首先需要确定，你现在是否已经生成了Android的证书，[前去查看](http://www.apicloud.com/certificate)，下图所示则说明没有生成证书

![](./img/zs.jpg)

1. 先自己生成证书

2. 如果已经生成了证书，那么请看[打正式包](#打正式包),

<div id="打正式包"></div>

#**打正式包**

打正式包之前需要先[入驻阿里](#开发者入驻)，加入[淘宝联盟](#加入淘宝联盟)，并得到[阿里妈妈的pid](#阿里妈妈淘客)

>然后继续

1、将正式工程添加android证书，并引入百川模块

![](./img/01.png)

2、生成APP，点击下载，到本地

![](./img/02.png)

3、检查是否开通了阿里百川的功能

![](./img/bcfw.png)

4、获取安全图片 yw_1222.jpg

![](./img/yw1222.jpg)

下载安全图片

![](./img/dowlyw.jpg)

替换Custom Module模块中zip包里的安全图片[Custom Module](https://github.com/bringmehome/Alibaichuan/tree/master/Custom%20Module)

android版本的替换如下(替换res/drawable文件夹下的图片)，iOS版本替换target目录下的文件

![](./img/thyw1222.png)

重新压缩自定义模块，直接在commonkey文件夹上点击压缩,并上传到自定义模块

![](./img/yasuokey.png)

4、上传自定义模块，**iOS和android两个zip包**

![](./img/sczdy.png)

5、并勾选自定义模块，能在已添加模块中看到即可

![](./img/ytjmk.png)

<div id="开始开发"></div>

#**开始开发**

1、手机需要安装手机淘宝，这个应该大部分人都有吧

2、接口使用参考github：[https://github.com/bringmehome/Alibaichuan](https://github.com/bringmehome/Alibaichuan/tree/master/Demo/widget),里面的测试demo

注意要在config.xml文件里添加这一句" < preference name="urlScheme" value="tbopen23277247"/ > ",其中tbopen23277247是tbopen+appkey, appkey是在阿里百川的平台上可以找到

![](./img/tbopenkey.png)

效果

![](./img/tbopenkey01.png)

```js
  <feature name="alibaichuan">
    <param name="urlScheme" value="tbopen23277247"/>
  </feature>
```

3、测试登录

![](./img/16.png)

4、买个东西看看，

首先，看看这个东西能返现多少钱，[传送门](http://pub.alimama.com/myunion.htm?spm=a219t.7473494.1998155389.3.ocD5gU#!/promo/self/items)

我准备买个乐高，网址https://item.taobao.com/item.htm?spm=a219t.7664554.1998457203.254.FDU0Gt&id=38922866272

填入传送门里的网址，看看98块钱，返现4.9，棒棒的

![](./img/22.png)

5、通过接口买了,

```js
function showTaokeItemById() {
	var param = {
	    isvcode : "feeling",
	    itemid : "537687037290",
	    mmpid : "mm_112712463_0_0",
	    nativeview: true //仅支持android版
	};
	alibaichuan.showTaokeItemById(param, function(ret, err) {
	    if (ret) {
	        alert("ret - " + JSON.stringify(ret));
	    } else {
	        alert("err - " + JSON.stringify(err));
	    }
	});
}
```

这里教个省钱的测试方法，选中购买，到了付款界面退出，然后在去购物车找到这个订单，取消购买，

看看是否能拿到钱了，果然有了，但是是显示订单失效，当然了，你取消了嘛

![](./img/23.png)

给你看看成功的订单，

![](./img/24.png)

另外，阿里的规则（每月1号结算上一个月成功订单的返现金额，20号将钱给你，到时候你要到结算中心，把他提现转到支付宝）

<br/>
<br/>

[回去继续看APICloud文档](http://docs.apicloud.com/端API/开放SDK/alibaichuan)

<br/>
<br/>



>其他问题请联系作者邮箱(88635653@qq.com)


<div id="开发者入驻"></div>

#**开发者入驻**

1、首先需要加入百川，[http://baichuan.taobao.com/](http://baichuan.taobao.com/)，按要求一步一步填写过来，成功后如下图

![](./img/03.png)

<div id="阿里妈妈淘客"></div>

#**阿里妈妈淘客**

1、开通阿里妈妈会员，[http://media.alimama.com/user/limit_status.htm?spm=a219a.7395903.0.0.zr6Ni5](http://media.alimama.com/user/limit_status.htm?spm=a219a.7395903.0.0.zr6Ni5),显示以下界面则说明开通成功

![](./img/07.png)

2、此时再回来[查看证书权限管理](http://console.baichuan.taobao.com/applications.htm)，是不是已经有了，这个id在调用[showTaokeItemById接口](http://docs.apicloud.com/%E7%AB%AFAPI/%E5%BC%80%E6%94%BESDK/alibaichuan#showTaokeItemById)的时候需要用到

![](./img/huoqmmid.jpg)

![](./img/mmid.jpg)

<div id="加入淘宝联盟"></div>

#**加入淘宝联盟**

1、点此加入淘宝联盟[http://pub.alimama.com/?spm=0.0.0.0.CrMksN](http://pub.alimama.com/?spm=0.0.0.0.CrMksN)

![](./img/09.png)

![](./img/10.png)

这个和开店一样，所以需要人工审核，审核时间也有点长，一般1-2个工作日

(完)

如果看到这里，你已经疯了，请联系QQ：88635653，备注：求药，治百川模块