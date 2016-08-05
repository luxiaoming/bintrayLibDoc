# bintrayLibDoc
AndroidStuio快速发布开源项目到Jcenter/Bintray


![](http://upload-images.jianshu.io/upload_images/1603789-ecc54e41efb335a4?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

AndroidStuio快速发布开源项目到Jcenter/Bintray

如何将自己开发的库，分享出去，让更多的人开发使用。就像你自己使用别人的库一样。比如

![](http://upload-images.jianshu.io/upload_images/1603789-fef5543165e2dfde?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

去引用这个gson库。
这一讲我们就来解决这个事情。

1 在自己的项目根节点的build.gradle

在 dependencies 里面加入

![](http://upload-images.jianshu.io/upload_images/1603789-34cc7be1184ca494?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个就是生成文档需要的插件

2 在根节点复制一个文件bintray.gradle

这里面完成生成需要的task任务。主要我们要修改的是dependencies里面的依赖，这里就是添加我们这个库依赖的其他库资源。

比如我们依赖的gson
![](http://upload-images.jianshu.io/upload_images/1603789-fef5543165e2dfde?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这里转为

![](http://upload-images.jianshu.io/upload_images/1603789-542853095aa59f4c?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其他依赖的一样添加即可。这个文件其他地方不用管了。

3 在根节点的gradle.properties

![](http://upload-images.jianshu.io/upload_images/1603789-cf7b680635e660ca?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

主要完成2步骤里面的变量初始化。
这里我们看到一些值
项目组
PROJ_GROUP=com.xm.core
项目版本号
PROJ_VERSION=0.0.1
项目名字
PROJ_NAME=core
项目地址
PROJ_WEBSITEURL=https://github.com/luxiaoming/xmCore
项目提交问题地址
PROJ_ISSUETRACKERURL=https://github.com/luxiaoming/xmCore/issues
项目git地址
PROJ_VCSURL=https://github.com/luxiaoming/xmCore.git
项目描述
PROJ_DESCRIPTION=android app Development Kit
项目artifactId
PROJ_ARTIFACTID=core
作者id
DEVELOPER_ID=code_gg
作者名字
DEVELOPER_NAME=luxiaoming
作者联系方式
DEVELOPER_EMAIL=332324956@qq.com
如果成功后，我们使用的时候使用的是：
PROJ_GROUP:PROJ_ARTIFACTID:PROJ_VERSION
这里就会是：
compile ‘com.xm.core:core:0.0.1’

4 在根节点的local.properties 添加

BINTRAY_USER 和 BINTRAY_KEY

这两个值从这里拿到：
https://bintray.com/profile/edit ，user就是上面的那个值：这里为luxiaoming
key就是下面的api key值

![](http://upload-images.jianshu.io/upload_images/1603789-4df66712251f2b9f?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5 注册bintray账号

1登录 https://bintray.com/ ，点击右上角的Sign in，使用github登录，或者自己去注册一个即可。

2 进入之后，点击屏幕中间有个New Repository，创建一个新的仓库。

![](http://upload-images.jianshu.io/upload_images/1603789-7f1bc5adf1cfc926?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3 输入 名字（和项目配置的PROJ_NAME一样，这里就是core） 类型选择 Maven 协议使用Apache-2.0 描述下功能后，点击创建即可。

![](http://upload-images.jianshu.io/upload_images/1603789-5cd1bc9dddf36ca8?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6 生成javadoc javadocjar sourcejar

在Android studio主界面，点击右侧的Gradle，展开自己的项目的所有命令。在other里面找到 javadoc javadocjar sourcejar 三个，点击下运行，看到成功后即可。
然后选择publishing 里面的generatePomFileForMavenjavaPubLication 和bintrayUpload ，依次运行下，成功后即可。此时已经上传成功了。

![](http://upload-images.jianshu.io/upload_images/1603789-61b61e38f256e1b5?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

7验证

在你的网页上面，刷新下即可看到。 此时离直接使用只有一步了，就是加入到JCenter，这个也很简单。直接点击界面的add to JCenter ，里面不需要填什么，直接点击Send等待即可。

![](http://upload-images.jianshu.io/upload_images/1603789-fcd9fefa202c2a6d?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

8使用

如果发布成功了，直接在http://jcenter.bintray.com/ 后面跟你的包名就能看到。直接项目

compile ‘com.xm.core:core:0.0.1’  即可。

如果没发布出去的时候，我么可以再加一个仓库的方式解决。（我们知道我们在https://bintray.com 已经添加成功了，它也是一个仓库，我们把它加入进来，然后使用compile ‘com.xm.core:core:0.0.1’即可。）如何添加呢？ 在项目的根节点的build.gradle里面的

![](http://upload-images.jianshu.io/upload_images/1603789-1751a17d97247dee?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

9 相关文件下载

https://github.com/luxiaoming/bintrayLibDoc

![](http://upload-images.jianshu.io/upload_images/1603789-9b956c129df9565f?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
