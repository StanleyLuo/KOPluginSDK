###简介：
竞技台插件SDK（框架）， 主要提供了在免安装的情况下，运行KO对战游戏的能力。

###运行Demo
Demo 分为TV版和手机版

HostDemo.Mobile：手机版的demo源码

HostDemo.TV：TV版的demo源码

**demo中有编译错误， 目的是提醒开发者进行必要的设置**

1. 把"竞技台"的插件包（不能改名，必须为KoMobileArena.apk或者KoTvArena.apk)， 放置到sd卡的根目录。
2. 直接安装 KOPluginHostDemo.TV.apk，  运行, 点击 启动竞技台插件 按钮；

或者，

Import Eclipse 工程KOPluginHostDemo， 直接运行, 点击启动竞技台插件 按钮

###集成插件
1. 如果自行处理插件下载，下载好后调用下面的方法：
```java
    PluginOpener.startPlugin(this, apkFullPath, mUseHostNativeLibs, new OnPluginLoadListener());
```
  mUseHostNativeLibs 一般为false， 如果宿主已经包含了插件的所有so，设置为true
  
2. 如果使用SDK进行插件下载，使用以下代码:
```java
   Intent intent = new Intent(this, KoStartUpActivity.class);
   intent.putExtra(KoStartUpActivity.KEY_DOWNLOAD_URL, mPluginDownloadUrl);
   File dir = new File(mLocalPluginDirPath);
    if (!dir.exists()) {
       dir.mkdirs();
    }
   intent.putExtra(KoStartUpActivity.KEY_FILE_PATH, mLocalPluginDirPath);
   intent.putExtra(KoStartUpActivity.KEY_FILE_NAME, mApkFileName);
   startActivity(intent);
```
