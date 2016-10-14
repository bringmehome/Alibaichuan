/*
Title: ximalaya
Description: ximalaya
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
  <li class="active"><a href="#method-content">Method</a></li>
  <li><a href="#method-content2">状态码</a></li>
</ul>
   
<div id="method-content">

<div class="outline">

* [initTaeSDK](#initTaeSDK)

* [showLogin](#showLogin)

* [getUserInfo](#getUserInfo)

* [logout](#logout)

* [showTaokeItemById](#showTaokeItemById)

* [showDetailByURL](#showDetailByURL)

* [openMyCart](#openMyCart)

* [myOrdersPage](#myOrdersPage)

* [showMyCardCouponsPage](#showMyCardCouponsPage)
</div>

##**概述**

百川是阿里巴巴旗下的无线开放平台，基于世界级的后端服务和成熟的商业组件，快速搭建App和提供卓越用户体验，开拓广告、商品、生活服务等无线新商业。此版本实现了阿里百川的基础功能：手淘授权登陆、退出登陆、获取登录者的信息、打开购物车、打开我的订单、通过itemid打开宝贝详情等

>使用须知

1、此模块依賴安全图片模块，安全圖片是阿里的一種身份認證機制，每個證書(或者bundle:iOS包名)對應一個安全圖片，測試時候我們均使用平臺默認的證書，打包时選擇测试版

2、首先，去[GITHUB](https://github.com/bringmehome/Alibaichuan/tree/master/Custom%20Module)下载Custom Module模块，导入到自定义模块，(android和iOS兩個<而且iOS的雲編譯和自定義loader所用的還不一樣>)

3、使用步骤参考[接入指南](https://github.com/bringmehome/Alibaichuan/#bindyilai)


#**initTaeSDK**<div id="initTaeSDK"></div>

    初始化模块信息，打开页面require完成就去执行

    initTaeSDK(param, function(ret, err))

##params

isvcode：

- 类型：字符串
- 默认值：无
- 描述：自定义ISVCode,用于服务器订单跟踪。(如果服务器不做处理，可以随便传)

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //初始化成功信息
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 1000                     //错误码
    message:"user is not exist"     //错误描述
}
```

##示例代码

```js
var alibaichuan = null;
apiready = function() {
    alibaichuan = api.require('alibaichuan');
    initSDK();
};
function initSDK() {
    var param = {
        isvcode : "feelinglife"
    };
    alibaichuan.initTaeSDK(param,function(ret, err) {
        if (ret) {
            alert(JSON.stringify(ret));
        } else {
            alert(JSON.stringify(err));
        }
    });
}
```

##补充说明

    无

##可用性

    Android系统, iOS系統

    可提供的1.1.0及更高版本

<div id="showLogin"></div>
#**showLogin**

    打开手淘授权登陆

    showLogin(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    userNick:"rocke"                //用户昵称
    avatarUrl:"http://..."          //用户头像
    authCode:"2mp9..."              //授权码
    loginTime:"1449932770044s"      //登陆时间
    otherInfo:""                    //其他
    userId:"AAE..."                 //用户ID
    isLogin:true                    //是否登陆，true/false
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 1000                     //错误码
    message:"user is not exist"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.showLogin(function(ret, err) {
    if (ret) {
        alert("登录success:" + JSON.stringify(ret));
    } else {
        alert("登录error:" + JSON.stringify(ret));
    }
});
```

##补充说明

    无

##可用性

    Android系统, iOS系統

    可提供的1.1.0及更高版本

<div id="getUserInfo"></div>
#**getUserInfo**

    获取已经登陆的用户的相关信息

    getUserInfo(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    userNick:"rocke"                //用户昵称
    avatarUrl:"http://..."          //用户头像
    authCode:"2mp9..."              //授权码
    loginTime:"1449932770044s"      //登陆时间
    otherInfo:""                    //其他
    userId:"AAE..."                 //用户ID
    isLogin:true                    //是否登陆，true/false
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.getUserInfo(function(ret, err) {
    if (ret) {
        alert("用户信息 ret - " + JSON.stringify(ret));
    } else {
        alert("用户信息 err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统, iOS系統

    可提供的1.1.0及更高版本

<div id="logout"></div>
#**logout**

    退出登陆

    logout(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.logout(function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统, iOS系統

    可提供的1.1.0及更高版本


<div id="showTaokeItemById"></div>
#**showTaokeItemById**

    通过itemid打开宝贝

    showTaokeItemById({params}, function(ret, err))

##params

isvcode：

- 类型：字符串
- 默认值：无
- 描述：自定义ISVCode,用于服务器订单跟踪。(如果服务器不做处理，可以随便传)

itemid：

- 类型：字符串
- 默认值：无
- 描述：宝贝的id，itemid为打开宝贝详情后，看到浏览器里有id一项，如"https://item.taobao.com/item.htm?id=45535180986",这里的id就是itemid

- 注：商品id.支持标准的商品id，eg.37196464781；同时支持openItemId，eg.AAHd5d-HAAeGwJedwSnHktBI；必填，不允许为null；

mmpid：

- 类型：字符串
- 默认值：无
- 描述：阿里妈妈的pid，如果你还没有开通 [阿里妈妈-淘宝联盟账号](http://media.alimama.com/user/limit_status.htm?spm=0.0.0.0.yoiYny)，要去阿里妈妈开通账号并且补全账号信息以及绑定支付宝, 因为分销的商品最后是返回到阿里妈妈的账号，并通过支付宝提现拿到的

nativeview：

- 类型：boolean
- 默认值：false
- 描述：是否唤起手机淘宝客户端打开详情页，true：使用手淘客户端打开， false：使用H5页面打开(仅支持android版)


##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90001                    //错误码
    message:"Parameter is null"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    isvcode : "feeling",
    itemid : "537687037290", //或openid:AAEsXyhFACIB6LoMMaYjZqhF
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
```

##补充说明

    无

##可用性

    Android系统, iOS系統

    可提供的1.1.0及更高版本


<div id="showDetailByURL"></div>
#**showDetailByURL**

    通过URL打开宝贝详情

    showDetailByURL({params}, function(ret, err))

##params

url：

- 类型：字符串
- 默认值：无
- 描述：商品URL地址

mmpid：

- 类型：字符串
- 默认值：无
- 描述：阿里妈妈的pid，如果你还没有开通 [阿里妈妈-淘宝联盟账号](http://media.alimama.com/user/limit_status.htm?spm=0.0.0.0.yoiYny)，要去阿里妈妈开通账号并且补全账号信息以及绑定支付宝, 因为分销的商品最后是返回到阿里妈妈的账号，并通过支付宝提现拿到的


##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90001                    //错误码
    message:"Parameter is null"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    url : "https://item.taobao.com/item.htm?id=537687037290",
    mmpid : "mm_112712463_0_0"
};
alibaichuan.showDetailByURL(param, function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统，iOS系统

    可提供的1.0.3及更高版本

<div id="openMyCart"></div>
#**openMyCart**

    打开我的购物车

    openMyCart(function(ret, err))

##params

isvcode：

- 类型：字符串
- 默认值：无
- 描述：自定义ISVCode,用于服务器订单跟踪。(如果服务器不做处理，可以随便传)   

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    isvcode: "feelinglife"
};
alibaichuan.openMyCart(param, function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.1.0及更高版本

<div id="myOrdersPage"></div>
#**myOrdersPage**

    打开我的订单

    myOrdersPage({params}, function(ret, err))

##params

status：

- 类型：数字
- 默认值：无
- 描述：默认跳转页面, 0：全部；1：待付款；2：待发货；3：待收货；4：待评价。 若传入的不是这几个数字，则跳转到“全部”页面且“allOrder”失效 

isAllOrder：

- 类型：boolean
- 默认值：无
- 描述：true：显示全部订单，建议填true，不管status传什么都填true

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    status: 2,
    isAllOrder:true
};
alibaichuan.myOrdersPage(param, function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统, iOS系統

    可提供的1.1.0及更高版本

<div id="showMyCardCouponsPage"></div>
#**showMyCardCouponsPage**<div id="7"></div>

    打开我的卡券包

    showMyCardCouponsPage(function(ret, err))

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
//无返回值
alibaichuan.showMyCardCouponsPage(function(ret, err) {
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.1.0及更高版本

<div id="method-content2">
<div class="outline">

[状态码](#errcode)

</div>

<div id="errcode"></div>
#**错误码**

code | 描述
:-----------  | :-------------:
0 | 请求成功
90000 | 用户未登陆
90001 | 参数为空
其他 | 阿里返回的code和错误提示
