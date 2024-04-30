---
title: android 暗码（secretCode）小试牛刀
date: 2018-09-20 22:21:39
tag: android
---

# 暗码的由来
知道这个东西是有次输入 ` *#*#4636#*#* ` 进入手机使用情况统计，统计电池用量，app使用信息啥的，于是好奇，为什么在拨号界面输入这个就能进入一个界面呢？经过一番查找资料，得知这是android内置的SecretCode。系统内置了一些SecretCode，当然也可以自己自定义一些暗码来玩一些骚操作，启动我们的app或者一些隐藏的调试界面什么的。接下来我们动手吧，看看怎么实现一个暗码。
<!--more-->
只需要在AndroidManifest.xml中注册广播就可以接收到暗码
```java
<receiver android:name=".SecretReceiver">
    <intent-filter>
        <action android:name="android.provider.Telephony.SECRET_CODE" />
        <data android:scheme="android_secret_code" android:host="1024" />
    </intent-filter>
</receiver>

```
这样就注册了一个code是1024的暗码，然后再编写一个广播接收器就可以接收到这个暗码（注意不能和系统内置的暗码重合，重合的话优先处理系统已经实现好的逻辑，我们自己定义的并不会生效）

```java
public class SecretReceiver extends BroadcastReceiver{
    private static final String ACTION ="android.provider.Telephony.SECRET_CODE";
    private static final String SECRET_CODE = "1024";
    @Override
    public void onReceive(Context context, Intent intent) {
        if(intent.getAction().equals(ACTION)){
            if(intent.getData().getHost().equals(SECRET_CODE)){
                Intent target = new Intent(context, MainFragmentActivity.class);
                target.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
                context.startActivity(target);
                //todo 也可以实现自己的逻辑
            }
        }
    }
}
```

# 备注暗码大全
常见机型进入工程模式的指令码（未实测）
* 华为：` *#*#121314#*#* `
* 努比亚：` *#8604# ` 
* 魅族：` *#*#3646633#*#* `
* 小米：` *#*#6484#*#* 或 *#*#64663#*#* `
* 三星：` *#0*# `
* HTC：` *#*#3424#*#* `
* 联想：` ####1111# `
* 中兴：` *983*3640# ` 
* 索尼：` *#*#7378423#*#* ` 
* vivo：` *#558# `
* OPPO：` *#36446337# `
* 一加：` *#36446337# `
* 乐视：` *#*#3646633#*#* `
* ZUK：` *#*#1111#*#* `
* Moto：` *#*#372#*#* `
* 酷派：` *20060606# `
* 360手机：` *20121220# `
