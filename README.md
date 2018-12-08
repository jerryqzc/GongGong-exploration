# Gonggong-exploration
introduction:上周末拿到了拱拱iOS端的源码，想想还有点小激动，伴随而来的还有些许担忧，希望之后能有更多的小伙伴陪我一起走下去吧，不过如果真的就是我一个人的话，那我也愿意的。今天早上起床，看班群里我们班上的同学在问课表，突然一个人说“去拱拱上看呀”，接着他又说“哦，忘了拱拱没有iOS版的，下个超级课程表吧，或者到微信小程序里看看。”image
感到有点尴尬，但这又激励我继续前进，了解小居居是如何吃苹果的。
body:一拿到拱拱的源码，我就迫不及待的想再Xcode的simulator里面先跑一下，可好像没我想的那么简单。。。Build Failed
出现了没有配置Snapkit的错误
我就在网上找了如下资料
http://www.hangge.com/blog/cache/detail_746.html
http://www.hangge.com/blog/cache/detail_1097.html
了解了什么是Snapkit和Auto Layout，Snapkit有什么作用，并将Snapkit添加到原来的项目中
然后我就开心的点了一下左上角运行按钮。。。Build Failed
出现了'/tmp/injectionforxcode/BundleInjection.h'file not found的错误
image
经过一番搜寻，我找到了injectionforxcode插件，然后运行。。。Build Failed
出现了error: open //bin/unhide: No such file or directory
error: open //bin/unhide.sh: No such file or directory
image
在YouTube 上找了视频看关于injection如何使用
2018-12-02 4 13 52
