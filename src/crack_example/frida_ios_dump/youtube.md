# YouTube的ipa

此处介绍，具体如何用`frida-ios-dump`去砸壳`YouTube`的ipa文件：

* 概述
  ```bash
  ./dump.py com.google.ios.youtube
  ```

## 详解

先查看出Youtube的包名：

```bash
➜  frida-ios-dump git:(master) ideviceinstaller -l -o list_user
CFBundleIdentifier, CFBundleVersion, CFBundleDisplayName
rn.notes.best, "11122019", "爱思极速版"
com.suiyi.foodshop1, "4911", "食行生鲜"
com.cisco.anyconnect, "4.6.03052", "AnyConnect"
com.baidu.BaiduMobile, "10.5.5.10", "百度"
com.ishuyin.iShuYin, "1.22", "爱书音"
com.evernote.iPhone.Evernote, "358974", "印象笔记"
com.alipay.iphoneclient, "10.1.2.091512", "支付宝"
ctrip.com, "8.3.0", "携程旅行"
com.Qting.QTTour, "8.0.1.4", "蜻蜓FM"
com.360buy.jdmobile, "7.3.6", "京东"
com.taobao.tmall, "10948419", "手机天猫"
com.netease.cloudmusic, "876", "网易云音乐"
com.tencent.mqq, "7.2.9.404", "QQ"
com.crifan.ShowSysInfo, "1", "ShowSysInfo"
com.tencent.xin, "8.0.16.35", "微信"
com.google.ios.youtube, "17.08.2", "YouTube"
developer.apple.wwdc-Release, "801.5.2", "Developer"
com.ss.iphone.ugc.Aweme, "179011", "抖音"
com.3WRHBBSBW4.com.rileytestut.AltStore, "1", "AltStore"
```

其中有我们要找的`YouTube`的详细信息：

* com.google.ios.youtube, "17.08.2", "YouTube"
  * 包名: `com.google.ios.youtube`
  * 版本: `17.08.2`
  * 名称: `YouTube`

砸壳的具体过程和输出日志：

```bash
➜  frida-ios-dump git:(master) pwd
/Users/crifan/dev/DevSrc/iOS/AloneMonkey/frida-ios-dump

➜  frida-ios-dump git:(master) ./dump.py com.google.ios.youtube
Start the target app com.google.ios.youtube
Dumping YouTube to /var/folders/2f/53mn2kn920dfq4ww2gdqfpxc0000gn/T
[frida-ios-dump]: Load widevine_cdm_secured_ios.framework success.
[frida-ios-dump]: Module_Framework.framework has been loaded.
start dump /private/var/containers/Bundle/Application/ECB295AB-1355-46D1-8580-273B2CE98802/YouTube.app/YouTube
YouTube.fid: 100%|██████████████████| 16.3M/16.3M [00:00<00:00, 17.7MB/s]
start dump /private/var/containers/Bundle/Application/ECB295AB-1355-46D1-8580-273B2CE98802/YouTube.app/Frameworks/widevine_cdm_secured_ios.framework/widevine_cdm_secured_ios
widevine_cdm_secured_ios.fid: 100%|█| 3.44M/3.44M [00:00<00:00, 24.2MB/s]
start dump /private/var/containers/Bundle/Application/ECB295AB-1355-46D1-8580-273B2CE98802/YouTube.app/Frameworks/Module_Framework.framework/Module_Framework
Module_Framework.fid: 100%|███████████| 114M/114M [00:03<00:00, 36.6MB/s]
Localizable.strings: 190MB [00:44, 4.45MB/s]
0.00B [00:00, ?B/s]
Generating "YouTube.ipa"
```
