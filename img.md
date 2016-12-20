#**开发者入驻**

1、首先需要加入百川，[http://baichuan.taobao.com/](http://baichuan.taobao.com/)，按要求一步一步填写过来，成功后如下图

![](https://dn-nw49fjfa.qbox.me/0f4d76112e4cdba2a83a.png)

#**开通阿里妈妈**

1、开通阿里妈妈会员，获取淘客PID（返利用），[打开阿里妈妈传送门](http://media.alimama.com/user/limit_status.htm?spm=a219a.7395903.0.0.zr6Ni5),显示以下界面则说明开通成功

![](https://dn-nw49fjfa.qbox.me/f1e4be609babcf782736.png)

2、此时再回来[查看证书权限管理](http://console.baichuan.taobao.com/applications.htm)，是不是已经有了，这个id在调用showTaokeItemById接口的时候需要用到

![](https://dn-nw49fjfa.qbox.me/01c66849baf9a9dd50dd.jpg)

![](https://dn-nw49fjfa.qbox.me/9da20198ca197003e540.jpg)

#**加入淘宝联盟**

1、用于查看收益，并把收益转入支付宝，点此加入淘宝联盟[http://pub.alimama.com/?spm=0.0.0.0.CrMksN](http://pub.alimama.com/?spm=0.0.0.0.CrMksN)

![](https://dn-nw49fjfa.qbox.me/725a6da38693d438b626.png)

![](https://dn-nw49fjfa.qbox.me/e6c93ce827ce06e69c82.png)

这个和开店一样，需要人工审核，审核时间也有点长，一般1-2个工作日


#**开始开发**

1、接口使用参考github：[https://github.com/bringmehome/Alibaichuan](https://github.com/bringmehome/Alibaichuan/tree/master/Demo),里面的测试demo

注意要在config.xml文件里添加这一句" < preference name="urlScheme" value="tbopen23256171"/ > ",其中tbopen23256171是tbopen+appkey, appkey是在阿里百川的平台上可以找到

![](https://dn-nw49fjfa.qbox.me/01c66849baf9a9dd50dd.jpg)

![](https://dn-nw49fjfa.qbox.me/d1a147ded18e86012d0e.png)

效果

![](https://dn-nw49fjfa.qbox.me/f0a7b5f535eba54f70cc.png)

```js
<feature name="alibaichuan">
	<param name="urlScheme" value="tbopen23256171"/>
</feature>
```

2、引入百川模块

![](https://dn-nw49fjfa.qbox.me/c792001777ad49366cf2.png)

3、生成Android版本APP，点击下载，到本地

![](https://dn-nw49fjfa.qbox.me/2ae870f21df992485035.png)

4、检查是否申请了初级电商权限和开通了后台阿里百川的功能，高级电商非必须

![](https://dn-nw49fjfa.qbox.me/2ed91beec42839f1fdd9.png)

![](https://dn-nw49fjfa.qbox.me/ca0ec4e0797d30119e61.png)

5、获取安全图片 yw_1222.jpg，Android的通过apk文件获取，iOS通过bundleid获取

![](https://dn-nw49fjfa.qbox.me/ff7e04ad512b7321d43f.jpg)

下载安全图片

![](https://dn-nw49fjfa.qbox.me/52095ad311b01e7b2450.jpg)

替换Custom Module模块中zip包里的安全图片[Custom Module](https://github.com/bringmehome/Alibaichuan/tree/master/Custom%20Module)

android版本的替换如下(替换res/drawable文件夹下的图片)，iOS版本替换target目录下的文件

![](https://dn-nw49fjfa.qbox.me/1209bfd9979bef45bc18.png)

重新压缩自定义模块，直接在commonkey文件夹上点击压缩,并上传到自定义模块

![](https://dn-nw49fjfa.qbox.me/37cb2cd7e257a517b4f8.png)

4、上传自定义模块，**iOS和android两个zip包**

![](https://dn-nw49fjfa.qbox.me/992cc013a95b37390970.png)

5、并勾选自定义模块，能在已添加模块中看到即可

![](https://dn-nw49fjfa.qbox.me/b351127e5d2a7f0ddd1b.png)

