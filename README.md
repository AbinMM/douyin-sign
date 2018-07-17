[视频演示](http://yxshare.oss-cn-hangzhou.aliyuncs.com/flyoffline/%E6%8A%96%E9%9F%B3%E8%A7%86%E9%A2%91%E6%BC%94%E7%A4%BA.mp4)

>温馨提醒：

*抖音7月12日发布了v2.0.0的版本，加了一个策略：如果你登录过一个较大的版本号(比如1.9.8)，那么再登录回较低的版本号（1.7.2），会提示“为确保账户安全，请升级最新版本进行操作”。*

> 看不懂算法也想撸起来的朋友看这个：[https://github.com/sweet8-asia/douyin-demo](https://github.com/sweet8-asia/douyin-demo)

> 这里有一个演示的网页Demo:[http://toolher.com/douyin_video](http://toolher.com/douyin_video)，用于批量获取某个抖音号的所有无水印视频。

>需要源码中的Key的朋友私聊或加我QQ：2811481636，这里有[视频演示效果](http://yxshare.oss-cn-hangzhou.aliyuncs.com/flyoffline/%E6%8A%96%E9%9F%B3%E8%A7%86%E9%A2%91%E6%BC%94%E7%A4%BA.mp4)。请确保你看得懂这些go的代码再问我要Key，我这边不写其他语言的demo，也不写那些刷的软件。

>大家可以围观作者的另一款产品：[马上下——在线磁力链下载服务](https://wapp.flyoffline.com/)。*世界杯期间免费送卡，每天进几球送几张卡*。


>首先[这里有一篇关于Android逆向工程的文章](http://www.520monkey.com/archives/1081)，反编译了抖音的libuserinfo.so文件的种种加密入口限制，使得自己的Android程序可以调用该so文件直接加密校验。这样的效果就是无需真正意义破解加密算法。

>我这里直接讲抖音的加密算法本身。火山小视频也一样。

### 抖音核心的步骤是：

+ 在查询串插入一个固定的键rstr
+ 对查询串进行按键排序并取值，对空格和+进行转义为a
+ 然后取MD5；如果时间轴&1为1，那么取多一次MD5
+ 将MD5结果分别和5******6、1******4进行2次错位排序算法
+ 将4的结果再进行一次错位排序，得到36位字符
+ 将字符分别取18位给到as和cp字段，追加到查询串最后

>在最新的SDK版本有了新的mas字段辅助校验，这个完全可以忽略，只要把查询串的version_code设置到169之前就可以跳过这个字段了。
另外aid为必填字段，其他和接口本身无关的字段都可去掉。


![截图1](http://yxshare.oss-cn-hangzhou.aliyuncs.com/Screen%20Shot%202018-05-21%20at%2022.04.56.png)
![截图1](http://yxshare.oss-cn-hangzhou.aliyuncs.com/Screen%20Shot%202018-05-21%20at%2022.05.07.png)

>由于这里涉及到抖音公司的核心利益，就不放具体代码和关键Key值了。有需要深入研究的朋友可以私信我。
>需要源码中的Key的朋友私聊或加我QQ：2811481636


