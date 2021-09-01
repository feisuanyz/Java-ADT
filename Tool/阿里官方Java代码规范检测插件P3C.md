P3C插件是由阿里巴巴开发爱好者自发组织的p3c项目组根据《阿里巴巴Java开发规范》开发出的自动化代码规范检查插件。该插件在扫描代码之后，将不符合《规范》的代码按 Blocker / Critical / Major 三个等级告知，并能基于Inspection机制为用户提供实时检测功能。

P3C插件的github地址参见 https://github.com/alibaba/p3c 。

### 一、安装教程

#### 1. IDEA插件安装

操作步骤：File - Setting - Plugins - 输入alibaba找到插件进行安装。

如果不能安装可以去[JetBrains Plugins Repository](http://plugins.jetbrains.com)搜索 alibaba 进行安装，安装后如图1-1所示：

![1-1](https://images.gitee.com/uploads/images/2021/0831/174429_56dc57b5_8721401.png "1-1.png")
##### 图1-1 IDEA安装成功

#### 2. STS插件安装

操作步骤：选择Install New SoftWare - 填写https://p3c.alibaba.com/plugin/eclipse/update - 勾选并安装。

![1-2](https://images.gitee.com/uploads/images/2021/0831/174700_94f52850_8721401.png "1-2.png")
##### 图1-2 STS插件安装

如果出现插件安装不了的问题，比如` repository not found problem... `是工具版本过低，建议升级开发工具的版本。

当插件安装完成之后，重启工具就可以使用了，直接右键工程项目或者右键需要检查的类，然后运行显示进行检查。

![1-3](https://images.gitee.com/uploads/images/2021/0831/174916_8d184086_8721401.png "1-3.png")
##### 图1-3 右键即可运行插件

### 二、Bug的等级程度及修复优先级

某种意义上来说，Priority的定义要依赖于Severity，在大多数情况下，Severity越严重，那这个Bug的Priority就越高。

Priority（优先级）和Severity（严重程度）是Bug的两个重要属性。通常Bug管理系统里Severity分为四个等级Blocker, Critical, Major, Minor/Trivial（也可以自定义）；Priority则分为五个等级：Immediate, Urgent, High, Normal, Low。具体含义如下：

#### 1. Severity：

#### a）Blocker（阻塞限制）: 即系统无法执行、崩溃或严重资源不足、应用模块无法启动或异常退出、无法测试、造成系统不稳定。

比如：内存泄漏、用户数据丢失或破坏、服务器500错误等。

#### b）Critical（临界危急的）：即影响系统功能或操作，主要功能存在严重缺陷，但不会影响到系统稳定性。

比如：系统刷新错误、安全性问题等。

#### c）Major（主要的）：即界面、性能缺陷和兼容性问题。

比如：提示信息错误、兼容性问题等。

#### d）Minor/Trivial（不重要的）:即易用性及建议性问题。

比如：界面格式等不规范、操作未给用户提示等。

#### 2. Priority：

#### a）Immediate 即“马上解决”，表示问题必须马上解决，否则系统根本无法达到预定的需求。

#### b）Urgent 即“急需解决”，表示问题的修复很紧要，很急迫，关系到系统的主要功能模块能否正常。

#### c）High 即“高度重视”，表示有时间就要马上解决，否则系统偏离需求较大或预定功能不能正常实现。

#### d）Normal 即“正常处理”，进入个人计划解决，表示问题不影响需求的实现，但是影响其他使用方面，比如页面调用出错，调用了错误的等。

#### e）Low 即”低优先级”，即问题在系统发布以前必须确认解决或确认可以不予解决。

### 版权声明

本文基于CSDN博主「Wong_Wang」的原创文章修改，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。

原文链接：https://blog.csdn.net/qq_39560484/article/details/81087010
