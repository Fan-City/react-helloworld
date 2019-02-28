# 案例截图
![](https://git.michaelxu.cn/classroom/react/helloworld/raw/develop/assets/img/HotUpdateProcess.jpg)

# 代码编辑器：[Visual Studio Code](https://code.visualstudio.com/)
 * ESLint: JS,JSX,ES6 代码语法检测
 
 ```
 //以下命令均在项目目录中执行
 $ npm install eslint --save-dev
 $ npm install eslint-plugin-react --save-dev
 $ npm install babel-eslint --save-dev
 $ vi .eslintrc //参考http://npm.taobao.org/package/eslint-plugin-react
 {  
    "parser": "babel-eslint",  
    "ecmaFeatures": {    
        "jsx": true,    "modules": true  
    },  
    "env": {   
         "es6": true  
    },  
    "plugins": [    
        "react"  
    ]
 }
 ```
 
 * React Native Tools：微软官方出的插件
 * Babel ES6/ES7 
 * Reactjs code snippets：react 的代码提示
 * Dash 搜索在线文档
 * Git History 图形化 git log 查看
 * Auto Close Tag：自动闭合标签
 * Auto Rename Tag：自动重命名标签，配合上面的插件使用
 * Path Intellisense：文件路径提示补全
 * Typings autoinstaller 自动根据package.json中的依赖，下载对应的接口文件
 
 ```
 //以下在VSCode配置文件里设置
 "javascript.validate.enable": false, //屏蔽VSCode自带代码检测
 "files.associations": {"*.js":"javascriptreact"} //设置默认打开.js文件为javascriptReact

 ```
# FTP 工具：FileZilla
# 浏览器：Chrome
# 版本管理／工作台: [GitLab](http://git.michaelxu.cn)
# 环境搭建(MAC)

### 安装 Homebrew
[Homebrew](https://brew.sh/), Mac系统的包管理器，用于安装 NodeJS 和 macOS 没有预装，但你需要的东西。

```/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"```

修改 Homebrew 源（因为默认是链接国外服务器，速度会很慢，此处修改为国内服务器）

```
vi ~/.bash_profile
export HOMEBREW_BOTTLE_DOMAIN=http://7xkcej.dl1.z0.glb.clouddn.com
```

>在Max OS X 10.11（El Capitan)版本中，homebrew在安装软件时可能会碰到/usr/local目录不可写的权限问题。可以使用下面的命令修复（记住）：

>`sudo chown -R 'whoami' /usr/local`

### 安装 Git (建议下载 [sourcetree](https://www.sourcetreeapp.com/) 代替)
>Git 是一个分布式版本控制系统，本地永远保存完整版本库，只把修改的内容推送给协作者

`brew install git `

安装完成后，还需要最后一步设置，在命令行输入：
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
创建一个版本库(即目录，里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”)
```
$ mkdir learngit
$ cd learngit
$ git init
```
>瞬间Git就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository），细心的读者可以发现当前目录下多了一个.git的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了，不过当git地址更改了，可以手动修改里面文件相应地址。如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用ls -ah命令就可以看见。

编写一个readme.txt文件，内容如下：
```
Git is a version control system.
Git is free software.
```
第一步，用命令git add告诉Git，把文件添加到仓库：

`$ git add readme.txt`

执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

第二步，用命令git commit告诉Git，把文件提交到仓库（可以多次 add , 只 commit 一次）：
```
$ git commit -m "wrote a readme file"
[master (root-commit) cb926e7] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```
第三部，用命令git push 告诉Git，把文件推送到远程仓库：

```
$ git push
```

### 安装 Node
使用Homebrew来安装[Node.js](https://nodejs.org/en/)

`brew install node`

>React Native目前需要NodeJS 5.0或更高版本。本文发布时Homebrew默认安装的是最新版本，一般都满足要求。

安装完node后建议设置npm源以加速后面的过程。注意：不要使用cnpm，它是npm复制版本，使用国内的源，但是安装的模块路径比较奇怪，packager不能正常识别！

    npm config set registry https://registry.npm.taobao.org --global
    npm config set disturl https://npm.taobao.org/dist --global
    
> node升级
> ```
> #npm install -g n
> #sudo n stable
>```

### Yarn、React Native的命令行工具（react-native-cli）

[Yarn](http://yarnpkg.com/) 是Facebook提供的替代npm的工具，可以加速node模块的下载。React Native的命令行工具用于执行创建、初始化、更新项目、运行打包服务（packager）等任务。

`npm install -g yarn react-native-cli` // -g 代表对可执行命令进行全局设置

安装完yarn后同理也要设置镜像源：

	yarn config set registry https://registry.npm.taobao.org --global
	yarn config set disturl https://npm.taobao.org/dist --global

> 如果你看到EACCES: permission denied这样的权限报错，那么请参照上文的homebrew译注，修复/usr/local目录的所有权（参考：https://developer.apple.com/videos/play/wwdc2015/706/）：

>`sudo chown -R 'whoami' /usr/local`

安装完yarn之后就可以用yarn代替npm了，例如用yarn代替npm install命令，用yarn add 某第三方库名代替npm install --save 某第三方库名。

### 安装 Xcode
React Native目前需要[Xcode](https://developer.apple.com/download/) 8.0 或更高版本。你可以通过App Store或是到[Apple开发者官网](https://developer.apple.com/download/)上下载。这一步骤会同时安装Xcode IDE和Xcode的命令行工具。

>虽然一般来说命令行工具都是默认安装了，但你最好还是启动Xcode，并在Xcode | Preferences | Locations菜单中检查一下是否装有某个版本的Command Line Tools。Xcode的命令行工具中也包含一些必须的工具，比如git等。

### 安装Android Studio
React Native目前需要Android Studio2.0或更高版本。

> Android Studio需要Java Development Kit [JDK] 1.8。你可以在命令行中输入 javac -version来查看你当前安装的JDK版本。如果版本不合要求，则可以到[官网](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)上下载。

Android Studio包含了运行和测试React Native应用所需的Android SDK和模拟器。

>除非特别注明，请不要改动安装过程中的选项。比如Android Studio默认安装了 Android Support Repository，而这也是React Native必须的（否则在react-native run-android时会报appcompat-v7包找不到的错误）。

安装过程中有一些需要改动的选项：
- 选择Custom选项：
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-custom-install.png)

- 勾选Performance和Android Virtual Device
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-additional-installs.png)

- 安装完成后，在Android Studio的启动欢迎界面中选择Configure | SDK Manager。
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-configure-sdk.png)

- 在SDK Platforms窗口中，选择Show Package Details，然后在Android 6.0 (Marshmallow)中勾选Google APIs、Android SDK Platform 23、Intel x86 Atom System Image、Intel x86 Atom_64 System Image以及Google APIs Intel x86 Atom_64 System Image。
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-android-sdk-platforms.png)

- 在SDK Tools窗口中，选择Show Package Details，然后在Android SDK Build Tools中勾选Android SDK Build-Tools 23.0.1（必须是这个版本）。然后还要勾选最底部的Android Support Repository.
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-android-sdk-build-tools.png)

#### ANDROID_HOME环境变量

确保ANDROID_HOME环境变量正确地指向了你安装的Android SDK的路径。具体的做法是把下面的命令加入到~/.bash_profile文件中：(译注：~表示用户目录，即/Users/你的用户名/，而小数点开头的文件在Finder中是隐藏的，并且这个文件有可能并不存在。请在终端下使用vi ~/.bash_profile命令创建或编辑。如不熟悉vi操作，请点击这里学习）。如果你的命令行不是bash，而是例如zsh等其他，请使用对应的配置文件。
> 如果你不是通过Android Studio安装的sdk，则其路径可能不同，请自行确定清楚。

>`export ANDROID_HOME=~/Library/Android/sdk`

然后使用下列命令使其立即生效（否则重启后才生效）：

> `source ~/.bash_profile`

> 可以使用echo $ANDROID_HOME检查此变量是否已正确设置。

### 安装 Watchman
[Watchman](https://facebook.github.io/watchman/docs/install.html)是由Facebook提供的监视文件系统变更的工具。安装此工具可以提高开发时的性能（packager可以快速捕捉文件的变化从而实现实时刷新）。

`brew install watchman`

### 安装 Genymotion
比起Android Studio自带的原装模拟器，Genymotion是一个性能更好的选择，但它只对个人用户免费。

1.下载和安装[Genymotion](https://www.genymotion.com/download/)（genymotion需要依赖[VirtualBox](https://www.virtualbox.org/wiki/Downloads)虚拟机，下载选项中提供了包含VirtualBox和不包含的选项，请按需选择）。

2.打开Genymotion。如果你还没有安装VirtualBox，则此时会提示你安装。

3.创建一个新模拟器并启动。

4.启动React Native应用后，可以按下⌘+M来打开开发者菜单。

### 安装 react-native-cli 命令行工具
`sudo npm install -g react-native-cli`

### 创建 HealloWorld 项目
注意：init命令默认会创建最新的版本，而目前最新的0.45及以上版本需要下载boost库编译。此库体积庞大，在国内即便翻墙也很难下载成功，导致很多人无法正常运行iOS项目，中文网在论坛中提供了这些库的国内下载链接。如果你嫌麻烦，又没有对新版本的需求，那么可以暂时创建0.44.3的版本。

>提示：你可以使用--version参数（注意是两个杠）创建指定版本的项目。例如react-native init MyApp --version 0.44.3，注意版本号必须精确到两个小数点。

或者也可以手动安装第三方编译库

>RN iOS 0.45以上版本开始需要依赖一些第三方编译库，这些库在国内下载都非常困难（一般的翻墙工具都很难下载）
未来RN不同版本可能依赖不同版本的第三方编译库，具体所需库和版本请查看ios-install-third-party.sh文件，注意先把左上角的branch切换到对应的版本

![](http://bbs.reactnative.cn/uploads/files/1501422470851-branch.png)

然后在底部查看所需的依赖库名字和版本

![](http://bbs.reactnative.cn/uploads/files/1501422596982-version.png)

然后去网盘里下载↓

第三方依赖库百度盘链接： https://pan.baidu.com/s/1i43FTTr

下下来后请放置到 ~/.rncache 目录

比如你可以打开终端，输入
```
cd ~   
mkdir .rncache
cp ~/Downloads/boost_1_63_0.tar.gz ~/.rncache/ 
```
全部复制完成后，就可以开始init新的RN项目了

	react-native init HelloWorld
	cd HelloWorld
	react-native run-ios // 或者 react-native run-android

>如果提示 command not found: react-native ，就执行下面命令
>`export PATH="$HOME/.node/bin:$PATH"`

>init 项目后，会生成yarn.lock文件，用来管理版本依赖，所以之后用`yarn` 代替 `npm install`
>Enable Hot Reloading ios模拟器:cmd+d,android 模拟器:cmd+m or f1 or f2

### 如果到这里你还没成功，请不要放弃，因为从入门到放弃的你还没入门，所以我即将告诉大家一个1分钟搞定上面所有步骤的方法，不要打我

#### 安装 create-react-native-app

`$ npm install -g create-react-native-app`

#### 用 create-react-native-app 一键生成RN应用二维码，并安装[Expo](https://expo.io/)扫描查看

    $ create-react-native-app BeautyWrold
    $ cd BeautyWrold/
    $ npm start

# 环境搭建(Windows)
## 安装JDK
从[官网](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html)下载jdk并安装，注意选择操作系统版本。

完成安装后，在系统环境变量中新增JAVA_HOME变量。

![](http://120.79.26.168:8088/ysMobilePlatform/testOne/raw/master/image/JAVA_HOME.png)

> 开发环境需要安装Java Development Kit [JDK] 1.8。

> 将jdk的bin目录路径`%JAVA_HOME%\bin`和`%JAVA_HOME%\jre\bin`加入到系统环境变量Path中。

> 可以在命令行输入`java -version`来检查jdk安装版本。

## 安装Python
从[官网](https://www.python.org/downloads/release/python-2711/)下载并安装python 2.7.x（3.x版本不行）。

完成安装后，在用户环境变量中新增PYTHON_HOME变量。

![](http://120.79.26.168:8088/ysMobilePlatform/testOne/raw/master/image/PYTHON_HOME.png)

> 系统环境变量Path中添加：`%PYTHON_HOME%`和`%PYTHON_HOME%\Scripts`。

> 安装和配置完成后需要重启电脑。

## 安装Git
下载[Git](https://git-scm.com/downloads)客户端并安装，在安装过程中记得勾选安装Git Bash和Git GUI两项，并注意要选择`Use Git from Git Bash only`选项。

## 安装Android SDK
下载[Android Studio](http://www.android-studio.org/index.php/download)注意操作系统版本。
React Native目前需要Android Studio2.0或更高版本。

> Android Studio需要Java Development Kit [JDK] 1.8。你可以在命令行中输入 javac -version来查看你当前安装的JDK版本。如果版本不合要求，则可以到[官网](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)上下载。

Android Studio包含了运行和测试React Native应用所需的Android SDK和模拟器。

> 除非特别注明，请不要改动安装过程中的选项。比如Android Studio默认安装了 Android Support Repository，而这也是React Native必须的（否则在react-native run-android时会报appcompat-v7包找不到的错误）。

安装完成后第一次运行会报`unable to access android sdk-on list`，选择`cancel`，后续配置项如下选择：

- 选择Custom选项：
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-custom-install.png)

- 勾选Performance和Android Virtual Device
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-additional-installs.png)

- 然后会继续开始下载安装Android SDK（时间较长）,安装完成后，在Android Studio的启动欢迎界面中选择Configure | SDK Manager。
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-configure-sdk.png)

- 在SDK Platforms窗口中，选择Show Package Details，然后在Android 6.0 (Marshmallow)中勾选Google APIs、Android SDK Platform 23、Intel x86 Atom System Image、Intel x86 Atom_64 System Image以及Google APIs Intel x86 Atom_64 System Image。
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-android-sdk-platforms.png)

- 在SDK Tools窗口中，选择Show Package Details，然后在Android SDK Build Tools中勾选Android SDK Build-Tools 23.0.1（必须是这个版本）。然后还要勾选最底部的Android Support Repository.
![](http://reactnative.cn/static/docs/0.50/img/react-native-android-studio-android-sdk-build-tools.png)

点击apply，继续下载。完成后在用户环境变量中配置ANDROID_HOME。

![](http://120.79.26.168:8088/ysMobilePlatform/testOne/raw/master/image/ANDROID_HOME.png)

> 系统环境变量Path中添加：`%ANDROID_HOME%\tools`和`%ANDROID_HOME%\platform-tools`。

## 安装node.js
从[官网](http://nodejs.cn/download/)下载对应系统的安装文件,直接安装即可。

> 检查系统环境变量path中是否已添加nodeJs目录。

![](http://120.79.26.168:8088/ysMobilePlatform/testOne/raw/master/image/path.png)

> 在命令行工具中输入`node --version`检查Node.js版本。

由于新版的nodejs已经集成了npm，所以npm也一并安装好了。在命令行工具中输入`npm -v`来测试是否安装成功。

设置npm镜像以加速后面的过程

    npm config set registry https://registry.npm.taobao.org
    npm config set disturl https://npm.taobao.org/dist

配置后可通过输入`npm config get registry`来验证是否成功。

在命令行输入`npm config set python python2.7`配置python版本。

## 安装React Native
选择自己需要安装的目录，鼠标右键`Git Bash Here`。

输入命令`git clone https://github.com/facebook/react-native.git`。

## 安装react-native命令行工具

在命令行工具输入`npm install -g react-native-cli`。

## 安装Genymotion
比起Android Studio自带的原装模拟器，Genymotion是一个性能更好的选择，但它只对个人用户免费。

1.下载和安装[Genymotion](https://www.genymotion.com/download/)（genymotion需要依赖[VirtualBox](https://www.virtualbox.org/wiki/Downloads)虚拟机，下载选项中提供了包含VirtualBox和不包含的选项，请按需选择）。

2.打开Genymotion。如果你还没有安装VirtualBox，则此时会提示你安装。

3.创建一个新模拟器并启动。

4.启动React Native应用后，可以按下⌘+M来打开开发者菜单。

> 模拟器占用空间较大，请谨慎选择安装路径以及模拟器文件下载路径。

## 创建HelloWord项目
创建自己的项目目录，例如`D:\work\rnWorkspace`。
在开始菜单里面找到nodeJS执行程序`node.js command prompt`以管理员身份运行。在命令行中跳转到上述路径下，然后输入命令`react-native init HelloWorld`来创建项目。这里`HelloWorld`为项目名。

> 安装过程要耐心等待数（或数十）分钟。，这个过程会下载一些包。

创建项目完成后，命令行切换目录到`D:\work\rnWorkspace\HelloWorld`路径下，输入`react-native start`。

> 可以用浏览器访问[脚本](http://localhost:8081/index.bundle?platform=android)看看是否打包成功。第一次访问通常需要十几秒，并且在packager的命令行可以看到形如[====]的进度条。

保持packager开启，另外打开一个命令行窗口，在工程目录下运行`react-native run-android`。
# IPA打包
在App Store上发布应用首先需要编译一个“发布版本”(release)的应用。具体的做法是在Xcode中选择Product -> Scheme -> Edit Scheme (cmd + <)，然后选择Run选项卡，将Build Configuration设置为release。 Release版本的应用会自动禁用开发者菜单，同时也会将js文件和静态图片打包压缩后内置到包中，这样应用可以在本地读取而无需访问开发服务器（同时这样一来你也无法再调试，需要调试请将Buiid Configuration再改为debug）。
由于发布版本已经内置了js文件，因而也无法再通过开发服务器来实时更新。面向用户的热更新，使用专门的热更新服务。
编译完成后，你就可以打包提交到TestFlight进行内测，或是提交到App Store进行发布。

# APK打包
#### 生成一个签名密钥
用keytool命令生成一个私有密钥

```
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
```

> 这条命令会要求你输入密钥库（keystore）和对应密钥的密码，然后设置一些发行相关的信息。最后它会生成一个叫做my-release-key.keystore的密钥库文件。

> 在运行上面这条语句之后，密钥库里应该已经生成了一个单独的密钥，有效期为10000天。--alias参数后面的别名是你将来为应用签名时所需要用到的，所以记得记录这个别名。

> 注意：请记得妥善地保管好你的密钥库文件，不要上传到版本库或者其它的地方。

#### 设置gradle变量
1.把my-release-key.keystore文件放到你工程中的android/app文件夹下。
2.编辑~/.gradle/gradle.properties（没有这个文件你就创建一个），添加如下的代码（注意把其中的****替换为相应密码）

> 注意：~表示用户目录，比如windows上可能是C:\Users\用户名，而mac上可能是/Users/用户名。

```
MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
MYAPP_RELEASE_KEY_ALIAS=my-key-alias
MYAPP_RELEASE_STORE_PASSWORD=*****
MYAPP_RELEASE_KEY_PASSWORD=*****
```

上面的这些会作为全局的gradle变量，我们在后面的步骤中可以用来给应用签名。

> 关于密钥库的注意事项:

> 一旦你在Play Store发布了你的应用，如果想修改签名，就必须用一个不同的包名来重新发布你的应用（这样也会丢失所有的下载数和评分）。所以请务必备份好你的密钥库和密码。

> 提示：如果你不想以明文方式保存密码，同时你使用的是macOS系统，那么你也可以把密码保存到钥匙串（Keychain）中。这样一来你就可以省略掉上面配置中的后两行（即MYAPP_RELEASE_STORE_PASSWORD和MYAPP_RELEASE_KEY_PASSWORD）。

#### 添加签名到项目的gradle配置文件
编辑你项目目录下的android/app/build.gradle，添加如下的签名配置：

```
...
android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            storeFile file(MYAPP_RELEASE_STORE_FILE)
            storePassword MYAPP_RELEASE_STORE_PASSWORD
            keyAlias MYAPP_RELEASE_KEY_ALIAS
            keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}
...
```

#### 生成发行APK包
只需在终端中运行以下命令：

```
$ cd android && ./gradlew assembleRelease
```

> cd android表示进入android目录（如果你已经在android目录中了那就不用输入了）。./gradlew assembleRelease在macOS、Linux或是windows的PowerShell环境中表示执行当前目录下的名为gradlew的脚本文件，且其运行参数为assembleRelease，注意这个./不可省略；而在windows的传统CMD命令行下则需要去掉./。

> Gradle的assembleRelease参数会把所有用到的JavaScript代码都打包到一起，然后内置到APK包中。如果你想调整下这个行为（比如js代码以及静态资源打包的默认文件名或是目录结构等），可以看看android/app/build.gradle文件，然后琢磨下应该怎么修改以满足你的需求。

> 生成的APK文件位于android/app/build/outputs/apk/app-release.apk，它已经可以用来发布了。

如果遇到报错：SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable.

```
# cd /my_current_project/

//created a file called local.properties and put inside
# vi local.properties // put inside 'sdk.dir=/my_current_path_to/sdk'
set ANDROID_HOME=/my_current_path_to/sdk
```

#### 测试应用的发行版本
在把发行版本提交到Play Store之前，你应该做一次最终测试。输入以下命令可以在设备上安装发行版本：

```
$ cd android && ./gradlew installRelease
```

> 注意installRelease参数只能在你完成了上面的签名配置之后才可以使用。 你现在可以关掉运行中的packager了，因为你所有的代码和框架依赖已经都被打包到apk包中，可以离线运行了。

> 在debug和release版本间来回切换安装时可能会报错签名不匹配，此时需要先卸载前一个版本再尝试安装。