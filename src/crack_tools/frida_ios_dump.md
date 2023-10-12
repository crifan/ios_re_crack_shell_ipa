# frida-ios-dump

* frida-ios-dump
  * 一句话描述：Pull a decrypted IPA from a jailbroken device
  * Github
    * AloneMonkey/frida-ios-dump: pull decrypted ipa from jailbreak device
      * https://github.com/AloneMonkey/frida-ios-dump

## 下载

* 下载命令
  ```bash
  git clone https://github.com/AloneMonkey/frida-ios-dump.git
  ```
* 下载后的文件的说明
  * `dump.py`：最核心的文件，用来砸壳的Python脚本
  * `requirements.txt`：Python依赖包的列表
    * 后续安装依赖的库，需要用到

## 初始化环境

* 先安装Frida
  * 概述
    * （Win/Mac等）电脑端
      ```bash
      pip install frida
      ```
    * （iOS/Android等）移动端
      * iPhone
        * `Cydia` -> 添加源 https://build.frida.re -> 安装插件：`Frida`
  * 详解
    * [安装Frida · 逆向调试利器：Frida](https://book.crifan.org/books/reverse_debug_frida/website/install_upgrade/install_frida.html)
* 再去安装依赖的其他的库
  * 直接用官网的依赖文件`requirements.txt`去安装
    ```bash
    sudo pip install -r requirements.txt
    ```
  * 或已知需要哪些库，手动安装
    ```bash
    pip install paramiko scp tqdm
    ```
* USB端口转发
  * 目的：方便本地直接访问对应端口，即可映射为，实际的iOS设备
  * 步骤
    * 概述
      ```bash
      iproxy 2222 22
      ```
    * 详解
      * [frida-ios-dump砸壳TikTok的ipa的实例](../crack_example/frida_ios_dump/tiktok.md)

## 使用=砸壳

* 概述
  * 查看app包名或app名称
    * 方式1：`frida-ps`
      ```bash
      frida-ps -Uai
      ```
    * 方式2：`ideviceinstaller`
      ```bash
      ideviceinstaller -l -o list_user
      ```
  * 开始砸壳
    * 命令
      ```bash
      ./dump.py iOSAppPackageOriOSAppName
      ```
    * 举例
      ```bash
      ./dump.py com.zhiliaoapp.musically

      ./dump.py com.ss.iphone.ugc.Aweme

      ./dump.py com.google.ios.youtube
      ./dump.py YouTube
      ```
* 详解
  * 详见后续章节：[frida-ios-dump实例](../crack_example/frida_ios_dump/README.md)
