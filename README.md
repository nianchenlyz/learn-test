2015.6.3 
Android 性能测试实践
内存
http://testerhome.com/topics/2572

实时监控
http://testerhome.com/topics/2574

CPU
http://testerhome.com/topics/2583

流量
http://testerhome.com/topics/2643

耗电测试
http://testerhome.com/topics/2673

GPU
http://testerhome.com/topics/502



Android 性能测试初探
合集 
https://testerhome.com/topics/506

客户端上的性能测试
https://testerhome.com/topics/470

客户端上的性能测试细节
https://testerhome.com/topics/479

CPU 及内存性能测试
https://testerhome.com/topics/484

GPU 性能测试
http://testerhome.com/topics/486

功耗测试
https://testerhome.com/topics/502

流量测试
https://testerhome.com/topics/503

android性能监控工具
https://testerhome.com/topics/568

功耗测试-软件篇
http://testerhome.com/topics/1957


Android 应用性能内存
http://blogs.360.cn/blog/%E6%B5%85%E8%B0%88android%E5%BA%94%E7%94%A8%E6%80%A7%E8%83%BD%E4%B9%8B%E5%86%85%E5%AD%98/



性能测试工具 -> Emmagee
http://www.oschina.net/news/59652/emmagee-2-2



Android 安全测试
https://testerhome.com/topics/1574
https://testerhome.com/topics/1575
http://testerhome.com/topics/1576

Android App Monkey 稳定性测试
https://testerhome.com/topics/599
https://testerhome.com/topics/597
drozer 是一款非常强悍的工具，适合深入挖掘应用底层方面的安全威胁，可以查杀漏洞及木马，以及暗码（有了暗码，很多事情就很好办了~~），drozer搭建好环境后，通过命令行的方式进行运行，命令方面的讲解大家可以移步官方的doc文档。

fuzz测试，可能大家在pc端并不陌生，但是移动端的fuzz测试并不是传统意义的fuzz，而是通过频繁调用空intent来遍历调用apk的各个activity来验证是否会产生崩溃，死机等方面的问题，甚至安全方面的隐患。

2015.11.20
iOS专项测试杂谈

一、压力测试
iOS压力测试推荐github上的ui-auto-monkey。使用简介如下：
1. 安装：xcode打开你的ios项目 — Product — Profile — UI Automation，然后导入UIAutoMonkey.js这个脚本。
2.  修改配置信息：
config: {
numberOfEvents: 1000,
delayBetweenEvents: 0.05,    // In seconds
// Events are triggered based on the relative weights here.
// The event with this highest number gets triggered the most.
eventWeights: {
tap: 30,
drag: 1,
flick: 1,
orientation: 1,
clickVolumeUp: 1,
clickVolumeDown: 1,
lock: 1,
pinchClose: 10,
pinchOpen: 10,
shake: 1
},

// Probability that touch events will have these different properties
touchProbability: {
multipleTaps: 0.05,
multipleTouches: 0.05,
longPress: 0.05
}
}

3. 执行该脚本即可；
4. 它还具有一些额外功能包括：UI holes、application not responding等。

二、CPU、内存、流量、耗电量测试
方法1：采用第三方framework，比如GT.framework，嵌入到应用中。
该方法的优点是：数据可以导出分析、可以图表化展示、而且功能强大，CPU、内存、流量、耗电量、平滑度等等都能分析；缺点是需要源码、并且重新打包app。因此该方法不能用来做竞品分析。

方法2：instruments
Xcode自带的instruments功能强大，可以检查内存、内存泄漏、time profile、耗电量、流量、CPU等等；另外，开发者模式可以用来模拟弱网络、录制耗电量和流量数据。
该方法的缺点就是很多数据不能导出分析，采样得到的数据只能通过instruments自身进行分析；耗电量数据只是energy usage level，精确度数据不直观。也很不方便用来做竞品分析。

方法3：摄像+分析
iOS竞品测试，主要是通过摄像然后进行时间分析的方法来进行。

方法4：通过tcpdump进行流量分析，可以用于竞品分析。
移动端专项测试博文
http://www.dzwanli.com.cn/?cat=3

https://github.com/jonathanpenn/ui-auto-monkey

iOS Monkey 测试方案
https://testerhome.com/topics/2523

iOS 
$instruments -s devices 进行设备id的查看
