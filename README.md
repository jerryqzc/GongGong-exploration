# Gonggong-exploration
## Hello Gonggong！🌚🌚🌚     
                            
## 2018-12-02 13:52                                
### Introduction:上周末拿到了拱拱iOS端的源码，想想还有点小激动，伴随而来的还有些许担忧，希望之后能有更多的小伙伴陪我一起走下去吧，不过如果真的就是我一个人的话，那我也没有怨言。今天早上起床，看班群里我们班上的同学在问课表，突然一个人说“去拱拱上看呀”，接着他又说“哦，忘了拱拱没有iOS版的，下个超级课程表吧，或者到微信小程序里看看。”感到有点尴尬，但这又激励我继续前进，去了解小居居是如何吃苹果的。                
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/awk.png)                
## Note:一拿到拱拱的源码，我就迫不及待的想再Xcode的simulator里面先跑一下，可好像没我想的那么简单。。。Build Failed                
出现了没有配置Snapkit的错误                
我就在网上找了如下资料                                
http://www.hangge.com/blog/cache/detail_746.html                
http://www.hangge.com/blog/cache/detail_1097.html                
了解了什么是Snapkit和Auto Layout，Snapkit有什么作用，并将Snapkit添加到原来的项目中                
然后我就开心的点了一下左上角运行按钮。。。Build Failed                
出现了'/tmp/injectionforxcode/BundleInjection.h'file not found的错误                
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/owm.png)                
经过一番搜寻，我找到了injectionforxcode插件，然后运行。。。Build Failed                
出现了                
*error: open //bin/unhide: No such file or directory                
*error: open //bin/unhide.sh: No such file or directory                
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/spec.png)                
在YouTube 上找了视频看关于injection如何使用                
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/ytuhep.png)                

## 2018-12-08 23:30                
### Note：经过几天带一晚我和唐贤君的瞎折腾，请允许我高兴一下下，所有红色的❕issues都没了！终于可以看到那只粉居居在iOS模拟器里流畅运行啦！或许在dalao们看来这并不算什么，可能看到自己添了一点东西在里面，issues就消失了，出现Build Succeeded的时候是多么让人兴奋。                
先说一下我们改的过程吧，两个issues我和jgg各自解决了一个，上周还在纠结环境，语言，版本的问题，这周有了Mac mini的帮助，环境立刻好了，我的电脑也认识粉居居了。ps：虽然你们说Mac mini好慢，可我在实际操作的时候发现体验并不差，除了开机速度有点揪心，其他渲染什么的感觉差距不太大，接在同学的超大的显示器上也是超级舒服的。                
一个issue就是Swift Compiler Error Expected identifier in function declaration，也就是编译器错误，函数声明中的预期标识符,我在函数声明那里加了个名称，完美，解决了一个issue                
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/is1.png)                
另一个就是在Localizable.strings中莫名多了一个点，我是真的没发现，也不敢乱动，结果唐贤君说试试删了那个句号，然后就Build Succeeded！！！多么激动！                
展示一下磨人的小妖精                
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-12-08%20%E4%B8%8B%E5%8D%8811.17.58.png)
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/prv.png)
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/login.png)
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/logged.png)
*![Image text](https://github.com/jerryqzc/Gonggong-exploration/blob/master/git-img/task.png)
运行了拱拱(一个单视图应用程序（Single View Application）)，另外还有主-从视图应用程序(Master-Detail Application)，Page Based 应用程序，Tabbed 应用程序等，这些都是Xcode中提供的模版。

## 2018-12-14 23:53                
### Note：初探结构                
打开workspace，有GongGong和Pods两个子项目                
*![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/1list.png)                
                        
将两个子项目展开：
*![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/2list.png)                
                        
Gongong project 展开：
*![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/3listG.png)                
                            
Pods project 展开：
*![Image text](https://github.com/jerryqzc/GongGong-exploration/blob/master/git-img/3listP.png)                
这里的Pods看起来好熟悉，先前也在翻代码的过程中看到了Cocoa Touch框架，而Cocoa Touch框架也在学长给我的开发指南中有介绍，我也找了一下CocoaPods的简介：CocoaPods是专门为iOS project提供第三方依赖库的管理工具，通过CocoaPods，可以更方便地管理每个第三方库的版本，而且不需要做太多的配置，就可以直观、集中和自动化地管理我们项目的第三方库。                
CocoaPods将所有依赖的库都放在一个名为Pods的项目下，然后让主项目依赖Pods项目。然后，我们编码工作都从主项目转移到Pods项目。Pods项目最终会编译为一个libPod-项目名.a静态库，主项目依赖于这个静态库。                
对于资源文件，CocoaPods 提供了一个名为 Pods-resources.sh 的 bash 脚本，该脚本在每次项目编译的时候都会执行，将第三方库的各种资源文件复制到目标目录中。                
CocoaPods 通过一个名为 Pods.xcconfig 的文件来在编译时设置所有的依赖和参数。                
CocoaPods是用 Ruby 写的，并由若干个 Ruby 包 (gems) 构成的。在解析整合过程中，最重要的几个 gems 分别是： CocoaPods/CocoaPods, CocoaPods/Core, 和 CocoaPods/Xcodeproj。               

## 2018-12-20 18:20                
### CocoaPod的核心组件                
#### CocoaPods/CocoaPod                
这是是一个面向用户的组件，每当执行一个 pod 命令时，这个组件都将被激活。该组件包括了所有使用 CocoaPods 涉及到的功能，并且还能通过调用所有其它的 gems 来执行任务。                
#### CocoaPods/Core                
Core 组件提供支持与 CocoaPods 相关文件的处理，文件主要是 Podfile 和 podspecs。                
#### Podfile                
Podfile 是一个文件，用于定义项目所需要使用的第三方库。该文件支持高度定制，你可以根据个人喜好对其做出定制。更多相关信息，请查阅 Podfile 指南。                
#### Podspec                
.podspec 也是一个文件，该文件描述了一个库是怎样被添加到工程中的。它支持的功能有：列出源文件、framework、编译选项和某个库所需要的依赖等。                
#### CocoaPods/Xcodeproj                
这个 gem 组件负责所有工程文件的整合。它能够对创建并修改 .xcodeproj 和 .xcworkspace 文件。它也可以作为单独的一个 gem 包使用。如果还想要写一个脚本来方便的修改工程文件，那么可以使用这个 gem。                

## 2019-1-12  23:39                 
9号考完试，10号去长沙玩了一天，11号下午回来，马不停蹄的开始了因考试而搁置的iOS Development，我也有了正儿八经的教师来教我如何耍Xcode了，不过学习之前我还是再了解一下iOS architecture，发现它的底层是Unix。
今天冬令营也开始了，在明天到来之前我给自己做了一个学习+工作的规划                
               
## 2019-1-23  21:15                 
冬令营终于结束了，我也在22号平安抵达了禄口机场，整顿了一天之后，今天也开始了正式（假的）寒假生活，虽然一直到26号期间都有很多事要办，还有本人的20大寿，但学习还是要学习的，笔记还是要做的，要不光年哥是不会放过我的，我自己也会不好意思的。                
近期我在YouTube上看Stanford某教授的公开课。通过公开课的学习，我将了解更多有关高版本Xcode的使用方法以及它与老版本Xcode存在的语言方面的差异。      
                     
## 2019-1-29  13:54                 
### Note：System Learning                
### 面向对象编程 Object-Oriented Programming           
### iOS app 适用语言 Oobjective-C 和 Swift（现已更新到5.0）                   
### 编程思想MVC Model-View-Controller  
可在https://www.tutorialspoint.com/mvc_framework/mvc_framework_introduction.htm        
查看简介
### iOS 结构：          
#### Cocoa Touch        
#### Media             
#### Core Service           
#### Core OS                   
不太明确分的四层结构          
顺便提一句，基于BSD版本的Unix 底层大部分是用C语言构建的（又到了令我恐惧的C语言）              
### Xcode         
Single view app单视图程序            
左侧 navigator导航栏             
右侧 utilities pane工具栏            
下方 debugger 和 console 控制台            
assets 包括应用图标等图片            
main storyboard即构建UI之处                   
在view controller中编辑UI             
借助interface builder 旁边还有 document outline 就是interface builder的文本大纲形式             
下方有设备选择器                    
后期还要制作自适应app，以适应在不同型号设备上的显示           
像个home键一样的图标 那是object library对象库                 
可以添加诸如buttons、sliders、labels、switches、web views、table views、text views、ARKit等控件（对象）          
只需要drag and drop就可以很简单的添加控件        

## 2019-1-30  17:21                      
### Assistant editor             
让代码和UI同时出现在屏幕上，便于编辑          
          
### 将UI和代码建立关联             
按住control从视图里拖到代码区域，就与方法建立了联系          
button关联有action和outlet两种类型，这里我们选择action。因为需要的是用户给出click的操作，然后button给出相应的响应             
       
### main.storyboard构成      
      
import UIKit       
       
class ViewController: UIViewController {
所有的方法和实例变量全都放在括号里，这就是声明类的方法，为了点击button时有所反应，所以我们要在这里创建一个方法       

@IBAction func touchCard(_ sender: UIButton) {        
   
}    
@IBAction是Xcode里修饰方法的特殊指令，因此左边显示了一个小圆圈，当鼠标悬浮在其上时，会有响应       
}      
这里定义了一个类，用关键字class      
viewController是类的名字，虽然它在这里指代范围很广泛，但若想要改变它的名字，不宜在这里单独改变，还要注意在用户界面也要改，这里不做赘述      
后面的UIViewController是它的父类（super class），继承自UIKit，因为UIViewController在UIKit中定义      
               
## 2019-1-31  11:42     
### 先说点不正经的，今天学了点Markdown的基本语法，又改进了一下自己的笔记的格式，看看是不是清爽了很多？嘻嘻，也让我自己坚定了要学下去的信心。     
不恰当的说，方法equals to定义在类里的函数（也就是对不对象的区别，特别是在Objective-C里，就不细说了），我们也可以在基本的swift语法中看出来。       
#### @IBAction func touchCard(_ sender: UIButton) {     
#### }     
举个简单的例子，这里的func，众所周知，即是一个函数，那它后面的touchCard就是一个方法了。这个方法就是对用户给出的点击的action给出相应的响应。     
#### (_ sender: UIButton)    
就是一个参数(argument)列表。这个方法有一个参数，参数类型在最后面，用英文':'隔开，这里的类型就是UIButton        
_ sender是参数parameter的名称        
这里插播一个point，swift语言有两个和其他语言不通的地方：          
其一：每个参数有一个实参标签在前面，在实际调用方法的时候就用这个标签        
其二：每个参数有两个名字，其中一个就是之前提到的实参标签（external name），这是给调用方法的人（程序员）用的；另一个就是行参名称（internal name），即在实现方法的时候使用的形式参数的名称          
如果有返回值，就加上-> Int 
### Example:           
#### @IBAction func touchCard(_ sender: UIButton)  -> Int  {          
#### }         
这样就会返回指定类型的数，例如这里就会返回一个Int类型的整数            
这里我们可以添加print（）这个全局函数，在控制台里测试这个方法是否可用（这也是debug的一种方法）        
#### 如何写一个swift函数？
It's  a piece of cake !
func开头（方法也是函数的一种嘻嘻嘻，这也是为什么我之前作出“不恰当的”equal）         
之后就是函数的名称，就叫flipCard吧，毕竟它是个翻牌程序呀        
如之前所言，接下来就到了参数arguments了，这里的函数有两个参数，一个是我们在牌上添加的内容，就是那个emoji(给它命名为withEmoji，类型为String)，另一个，显而易见就是button(命名为on button，具体命名规则参照swift.org,API设计准则)按钮了，另外我也发现这里正是swift特性表现出来的一个好例子，实参标签和行参名称同时出现           
也是考虑到不让程序员太过痛苦，所以有一条就是"read like English"不得不说应该点个赞        
接下来就是华丽丽的调用函数了，在touchCard里调用         
@IBAction func touchCard(_ sender: UIButton) {        
flipCard(withEmoji: "👻", on: sender)         
}            
这样调用的时候，读起来就像真正的英语一样吧          
再接着之前(142行)所说的，其实也不必有两个名字，但只有极少数情况下我们才会使用一个名字，当我们只使用一个名字时，缺省的参数用'_'表示      

## 2019-2-1  22:21

# 好久也没有更新了哈，不过这并不代表我没在学习啊。
# 毕竟昨天凌晨我也是全程看完了WWDC19直播的人嘞
---
这次主要阐述三个思路吧。
+第一个，也是最重要的，就是昨天在WWDC19上推出的SwiftUI和Xcode 11 Beta版，我回以最快速度完成SwiftUI的学习并将它运用到拱拱中，并重构部分冗余界面。
+第二个就是语言方面的更新，暑假一定会将Swift更新到4.2，如果有可能，也会直接跟进到5.0。
+第三个就是暑假的安排吧：学习Swift,完善拱拱。
