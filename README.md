# Gonggong-exploration

Hello Gonggong
2018-12-02 13 52
introduction:上周末拿到了拱拱iOS端的源码，想想还有点小激动，伴随而来的还有些许担忧，希望之后能有更多的小伙伴陪我一起走下去吧，不过如果真的就是我一个人的话，那我也愿意的。今天早上起床，看班群里我们班上的同学在问课表，突然一个人说“去拱拱上看呀”，接着他又说“哦，忘了拱拱没有iOS版的，下个超级课程表吧，或者到微信小程序里看看。”感到有点尴尬，但这又激励我继续前进，了解小居居是如何吃苹果的。
![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/awk.png)
body:一拿到拱拱的源码，我就迫不及待的想再Xcode的simulator里面先跑一下，可好像没我想的那么简单。。。Build Failed
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

2018-12-08 23 59
经过几天带一晚我和君gg的瞎折腾，请允许我高兴一下下，所有红色的❕issues都没了！终于可以看到那只粉居居在iOS模拟器里流畅运行啦！或许在dalao们看来这并不算什么，可能看到自己添了一点东西在里面，issues就消失了，出现Build Succeeded的时候是多么让人兴奋。
先说一下我们改的过程吧，两个issues我和jgg各自解决了一个，上周还在纠结环境，语言，版本的问题，这周有了Mac mini的帮助，环境立刻好了，我的电脑也认识粉居居了。ps：虽然你们说Mac mini好慢，可我在实际操作的时候发现体验并不差，除了开机速度有点揪心，其他渲染什么的感觉差距不太大，接在同学那个超大的显示器上也是超级舒服的。
一个issue就是Swift Compiler Error Expected identifier in function declaration也就是编译器错误，函数声明中的预期标识符,我在函数声明那里加了个名称，完美，解决了一个issue
另一个就是在Localizable.strings中莫名多了一个符号，我是真的没发现，也不敢乱动，结果jgg说要不删了那个试试，然后就Build Succeeded！！！多么激动！
