# Gonggong-exploration
Hello Gonggong</br>
2018-12-02 13 52 </br>
引入:上周末拿到了拱拱iOS端的源码，想想还有点小激动，伴随而来的还有些许担忧，希望之后能有更多的小伙伴陪我一起走下去吧，不过如果真的就是我一个人的话，那我也愿意的。今天早上起床，看班群里我们班上的同学在问课表，突然一个人说“去拱拱上看呀”，接着他又说“哦，忘了拱拱没有iOS版的，下个超级课程表吧，或者到微信小程序里看看。”感到有点尴尬，但这又激励我继续前进，了解小居居是如何吃苹果的。
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/awk.png)</br>
Note:一拿到拱拱的源码，我就迫不及待的想再Xcode的simulator里面先跑一下，可好像没我想的那么简单。。。Build Failed
出现了没有配置Snapkit的错误
我就在网上找了如下资料
http://www.hangge.com/blog/cache/detail_746.html
http://www.hangge.com/blog/cache/detail_1097.html
了解了什么是Snapkit和Auto Layout，Snapkit有什么作用，并将Snapkit添加到原来的项目中
然后我就开心的点了一下左上角运行按钮。。。Build Failed
出现了'/tmp/injectionforxcode/BundleInjection.h'file not found的错误
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/owm.png)
经过一番搜寻，我找到了injectionforxcode插件，然后运行。。。Build Failed
出现了error: open //bin/unhide: No such file or directory
error: open //bin/unhide.sh: No such file or directory
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/spec.png)
在YouTube 上找了视频看关于injection如何使用
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/ytuhep.png)

2018-12-08 23 59</br>
Note：经过几天带一晚我和君gg的瞎折腾，请允许我高兴一下下，所有红色的❕issues都没了！终于可以看到那只粉居居在iOS模拟器里流畅运行啦！或许在dalao们看来这并不算什么，可能看到自己添了一点东西在里面，issues就消失了，出现Build Succeeded的时候是多么让人兴奋。</br>
先说一下我们改的过程吧，两个issues我和jgg各自解决了一个，上周还在纠结环境，语言，版本的问题，这周有了Mac mini的帮助，环境立刻好了，我的电脑也认识粉居居了。ps：虽然你们说Mac mini好慢，可我在实际操作的时候发现体验并不差，除了开机速度有点揪心，其他渲染什么的感觉差距不太大，接在同学的超大的显示器上也是超级舒服的。
一个issue就是Swift Compiler Error Expected identifier in function declaration，也就是编译器错误，函数声明中的预期标识符,我在函数声明那里加了个名称，完美，解决了一个issue
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/is1.png)
另一个就是在Localizable.strings中莫名多了一个点，我是真的没发现，也不敢乱动，结果唐贤君说试试删了那个句号，然后就Build Succeeded！！！多么激动！</br>
展示一下磨人的小妖精
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-12-08%20%E4%B8%8B%E5%8D%8811.17.58.png)
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/prv.png)
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/login.png)
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/logged.png)
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/task.png)
运行了拱拱，这是一个单视图应用程序（Single View Application），另外还有主-从视图应用程序(Master-Detail Application)，Page Based 应用程序，Tabbed 应用程序等，这些都在Xcode中提供了模版。

2018-12-08 23 59</br>
Note：了解结构
打开workspace，有GongGong和Pods两个子项目
![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/1list.png)</br>
</br>
将两个子项目展开：
![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/2list.png)</br>
</br>
Gongong project 展开：
![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/3listG.png)</br>
</br>
Pods project 展开：
![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/3listP.png)</br>
这里的Pods看起来好熟悉，先前也在翻代码的过程中看到了Cocoa Touch框架，而Cocoa Touch框架也在学长给我的开发指南中有介绍，我也找了一下CocoaPods的简介：CocoaPods是专门为iOS project提供第三方依赖库的管理工具，通过CocoaPods，可以更方便地管理每个第三方库的版本，而且不需要做太多的配置，就可以直观、集中和自动化地管理我们项目的第三方库。</br>
CocoaPods将所有依赖的库都放在一个名为Pods的项目下，然后让主项目依赖Pods项目。然后，我们编码工作都从主项目转移到Pods项目。Pods项目最终会编译为一个libPod-项目名.a静态库，主项目依赖于这个静态库。</br>
对于资源文件，CocoaPods 提供了一个名为 Pods-resources.sh 的 bash 脚本，该脚本在每次项目编译的时候都会执行，将第三方库的各种资源文件复制到目标目录中。
CocoaPods 通过一个名为 Pods.xcconfig 的文件来在编译时设置所有的依赖和参数。</br>
CocoaPods是用 Ruby 写的，并由若干个 Ruby 包 (gems) 构成的。在解析整合过程中，最重要的几个 gems 分别是： CocoaPods/CocoaPods, CocoaPods/Core, 和 CocoaPods/Xcodeproj。</br>
</br>
CocoaPod的核心组件</br>
CocoaPods/CocoaPod</br>
这是是一个面向用户的组件，每当执行一个 pod 命令时，这个组件都将被激活。该组件包括了所有使用 CocoaPods 涉及到的功能，并且还能通过调用所有其它的 gems 来执行任务。</br>
CocoaPods/Core</br>
Core 组件提供支持与 CocoaPods 相关文件的处理，文件主要是 Podfile 和 podspecs。</br>
Podfile</br>
Podfile 是一个文件，用于定义项目所需要使用的第三方库。该文件支持高度定制，你可以根据个人喜好对其做出定制。更多相关信息，请查阅 Podfile 指南。</br>
Podspec</br>
.podspec 也是一个文件，该文件描述了一个库是怎样被添加到工程中的。它支持的功能有：列出源文件、framework、编译选项和某个库所需要的依赖等。</br>
CocoaPods/Xcodeproj</br>
这个 gem 组件负责所有工程文件的整合。它能够对创建并修改 .xcodeproj 和 .xcworkspace 文件。它也可以作为单独的一个 gem 包使用。如果还想要写一个脚本来方便的修改工程文件，那么可以使用这个 gem。</br>
2018-12-13 18 20
