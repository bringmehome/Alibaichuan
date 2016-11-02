/*
Title: alibaichuan
Description: alibaichuan
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
  <li class="active"><a href="#method-content">Method</a></li>
</ul>
   
<div class="outline">

* [initTaeSDK](#initTaeSDK)

* [showLogin](#showLogin)

* [getUserInfo](#getUserInfo)

* [logout](#logout)

* [showTaokeItemById](#showTaokeItemById)

* [showDetailByURL](#showDetailByURL)

* [openMyCart](#openMyCart)

* [myOrdersPage](#myOrdersPage)

* [openShopPage](#openShopPage)

* [addToCartPage](#addToCartPage)

* [状态码](#errcode)
</div>

###**双十一了，我也来凑热闹，降价促销！什么时候促销结束呢？看心情，也许明天吧，手慢无。**

##**概述**

百川是阿里巴巴旗下的无线开放平台，基于世界级的后端服务和成熟的商业组件，快速搭建App和提供卓越用户体验，开拓广告、商品、生活服务等无线新商业。此版本实现了阿里百川的基础功能：手淘授权登陆、退出登陆、获取登录者的信息、打开购物车、打开我的订单、通过itemid打开宝贝详情等

>使用须知

1、此模块依賴安全图片模块，安全圖片是阿里的一種身份認證機制，每個證書(或者bundle:iOS包名)對應一個安全圖片，建议使用自己的证书测试

2、首先，去[GITHUB](https://github.com/bringmehome/Alibaichuan/tree/master/Custom%20Module)下载Custom Module模块，导入到自定义模块，(android和iOS兩個<而且iOS的雲編譯和自定義loader所用的還不一樣>)

3、使用步骤参考[接入指南](https://github.com/bringmehome/Alibaichuan/#bindyilai)

<div id="initTaeSDK"></div>
#**initTaeSDK**

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
  "userNick": "sin",                //用户昵称
  "avatarUrl": "http://wwc...",     //用户头像
  "userId": "AAEe...",              //用户ID
  "isLogin": true                   //是否登陆，true/false
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
  "userNick": "sin",                //用户昵称
  "avatarUrl": "http://wwc...",     //用户头像
  "userId": "AAEe...",              //用户ID
  "isLogin": true                   //是否登陆，true/false
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 9000                //错误码
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
    code : 9000                //错误码
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
//如果nativeview为false，且交易成功，则有返回值

{
    "code":999,
    "ordercode":"2551899489323387" //订单编号
}
```

err：

- 类型：JSON对象

内部字段：

```js
//如果nativeview为false，且交易失败，则有返回值

{
  "code": 10010,
  "message": "alipay支付失败，信息为：使用支付宝支付失败，支付宝错误码为 4000, 含义为订单支付失败"
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    isvcode : "feeling",
    itemid : "537687037290", //或openid:AAHyOaTIADoqwaqgX6Kr_lTS
    mmpid : "mm_119457865_0_0",
    nativeview: true
};
alibaichuan.showTaokeItemById(param, function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```


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
- 描述：商品URL地址, 或者优惠券地址

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
    code : 9001                    //错误码
    message:"Parameter is null"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    url : "http://h5.m.taobao.com/ump/coupon/detail/index.html?sellerId=2081981169&activityId=8314c70c51674cff90a7a010ae7d4274",
    mmpid : "mm_119457865_0_0",
    nativeview:false
};
alibaichuan.showDetailByURL(param, function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});
```

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
    code : 9000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    isvcode: "feeling",
    nativeview:false
};
alibaichuan.openMyCart(param, function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##可用性

    Android系统，iOS系统

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
    code : 9000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    status: 2,
    isAllOrder:true,
    nativeview:true
};
alibaichuan.myOrdersPage(param, function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##可用性

    Android系统，iOS系统

    可提供的1.2.0及更高版本

<div id="openShopPage"></div>
#**openShopPage**

    打开商家店铺

    openShopPage({params}, function(ret, err))

##params

shopid：

- 类型：字符串
- 默认值：无
- 描述：商家店铺ID 

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
    code : 9000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    shopid : "64185146",
    nativeview:false
};
alibaichuan.openShopPage(param, function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});
```

##可用性

    Android系统

    可提供的1.2.0及更高版本

<div id="addToCartPage"></div>
#**addToCartPage**

    打开添加购物车的页面

    addToCartPage({params}, function(ret, err))

##params

itemid：

- 类型：字符串
- 默认值：无
- 描述：宝贝的id，itemid为打开宝贝详情后，看到浏览器里有id一项，如"https://item.taobao.com/item.htm?id=45535180986",这里的id就是itemid

- 注：商品id.支持标准的商品id，eg.37196464781；同时支持openItemId，eg.AAHd5d-HAAeGwJedwSnHktBI；必填，不允许为null；

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
    code : 9000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    itemid : "540384005662"
    // itemid : "AAHyOaTIADoqwaqgX6Kr_lTS"
};
alibaichuan.addToCartPage(param, function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});
```

##可用性

    Android系统

    可提供的1.2.0及更高版本

<div id="errcode"></div>
#**错误码**

code | 描述
:-----------  | :-------------:
0 | 请求成功
999 | 交易成功
9000 | 用户未登陆
9001 | 参数为空
其他 | 阿里返回的code和错误提示
