### 一、SonarQube代码质量检查工具简介

Sonar（SonarQube）是一个用于管理源代码质量的开源平台，支持Java，C#，C/C++，PL/SQL，Cobol，JavaScrip，Groovy等二十几种编程语言的代码质量管理与检测。

Sonar从7个维度检测代码质量，开发人员至少需要处理前5种代码质量问题。这7个维度分别为：

##### a）不遵循代码标准

Sonar可以通过PMD，CheckStyle，Findbugs等代码规则检测工具规范代码编写。

##### b）潜在的缺陷

Sonar可以通过PMD，CheckStyle，Findbugs等代码规则检测工具检测出潜在的缺陷。

##### c）糟糕的复杂度分布

文件、类、方法等如果复杂度过高，修改起来将会非常麻烦，同时开发人员将难以理解它们。

##### d）重复度

程序中如果包含大量复制粘贴的代码，其质量会很差。Sonar可以展示源码中严重重复的地方。

##### e）注释不足或者过多

没有注释将使代码可读性变差，特别是当不可避免地出现人员变动时，程序的可读性将大幅下降；而过多的注释又会使得开发人员将精力过多地花费在阅读注释上，亦有违初衷。

##### f）缺乏单元测试

Sonar可以很方便地统计并展示单元测试覆盖率。

##### g）糟糕的设计

Sonar可以找出循环、展示包与包、类与类之间的相互依赖关系，可以检测自定义的架构规则。Sonar还可以管理第三方的jar包，利用LCOM4检测单个任务规则的应用情况，并检测藕合。

### 二、 安装：

#### 1. 安装SonarQube web server

a）根据jdk选择自己需要的版本，至少需要jdk 8+，SonarQube 8.0以上的版本需要jdk 11+；

b）点击链接 https://www.sonarqube.org/downloads/ ，下载SonarQube社区版。

点击下方的` Show all versions `按钮，可以查看并下载所有的历史版本，如图1-1所示：

![1-1](https://images.gitee.com/uploads/images/2021/0901/111847_cd545ebc_8721401.png "1-1.png")
##### 图1-1 查看所有历史版本

c）解压后的目录如图1-2所示：

![1-2](https://images.gitee.com/uploads/images/2021/0901/112235_ab501705_8721401.png "1-2.png")
##### 图1-2 解压后的目录

#### 2. 配置数据库

修改` /conf/sonar.properties` 配置文件，添加Mysql相关配置。在本地数据库新建一个 sonarqube 库：


```
sonar.jdbc.url=jdbc:mysql://localhost:3306/sonarqube?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true&useConfigs=maxPerformance&useSSL=false
sonar.jdbc.username=用户名  // 刚刚创建的sonarQube用户
sonar.jdbc.password=密码   // 创建用户对应的密码
sonar.sorceEncoding=UTF-8 // 设置编码格式为UTF-8
sonar.login=admin             // 登录账号
sonar.password=admin     // 登录密码
```

需要注意的是，一些关键配置的修改，如主机地址、context、端口号等，通常情况下使用默认的配置即可。

此外，在conf目录下的sonar.properties文件下有这样一行配置 : 


```
#----- MySQL >=5.6 && < 8.0
```

所以，如果mysql版本过高的话，需要降级。

#### 3. 启动

a）到解压目录的bin\windows-x86-64（编者注：作者电脑是64位）目录下，双击` StartSonar.bat `文件启动SonarQube。

第一次启动会自动初始化数据库，需要花费一定的时间。

b）到浏览器界面，输入` http://localhost:9000 `，能够进入界面证明安装成功。

启动成功的窗口如图1-3所示：

![1-3](https://images.gitee.com/uploads/images/2021/0901/114307_8000168e_8721401.png "启动成功.png")
##### 图1-3 启动成功

如果启动失败或者窗口自动关闭 ,我们可以在sonarqube-7.4\logs日志目录查看报错信息。一般情况下，启动错误基本上都是“数据库不存在”或者“端口冲突”的原因：

> 错误类型1：无法初始化数据库
> 
> 报错信息：
> 
> `logs/web.log Cannot execute statement: impossible to write to binary log since BINLOG_FORMAT = STATEMENT and at least one table uses a storage` 
> `engine limited to row-based logging. InnoDB is limited to row-logging when transaction isolation level is READ COMMITTED or READ UNCOMMITTED.`
> 
> 解决办法：
> 
> `$ vim /etc/my.cnf binlog-format=MIXED #指定binlog格式为mixed `
> 
> 参考：https://www.devside.net/wamp-server/mysql-error-impossible-to-write-to-binary-log-since-binlog_format-statement
> 
> 错误类型2：历史脏数据冲突
> 
> 报错信息：
> 
> ` Web server startup failed: Current version is too old. Please upgrade to Long Term Support version firstly.` 
> 
> 解决办法：
> 
> 清理历史数据（因首次安装，直接drop掉sonar表，然后重建），重启sonar即可。

### 三、使用

#### 1. 安装必要的插件（如汉化包）

a）点击导航栏的` config `，选择应用市场；

b）搜索` Chinese pack `，点击` install `进行安装；

c）安装成功后, 重启SonarQube。

中文界面的安装和展示分别如图2-1及图2-2所示：

![2-1](https://images.gitee.com/uploads/images/2021/0901/141113_3bbc534c_8721401.png "2-1.png")
##### 图2-1 搜索汉化包

![2-2](https://images.gitee.com/uploads/images/2021/0901/141149_da3af12e_8721401.png "2-2.png")
##### 图2-2 中文界面自动安装成功

如果上图自动安装方式失败，也可以选择下载[中文插件jar包](https://github.com/SonarQubeCommunity/sonar-l10n-zh/tags)，手动安装中文插件。

Sonar版本对应的中文插件包版本如下：

> SonarQube版本    7.00   6.70   6.60   6.50   6.40   6.30   6.20   6.10   6.00   5.60   5.50   5.40
> 
> sonar-|10n-zh    1.20   1.19   1.18   1.17   1.16   1.15   1.14   1.13   1.12   1.11   1.10   1.09

一般中文插件版本尽量选较低一点，如果太高的话，重启SonarQube的时候容易报错。

如图2-3所示，下载对应SonarQube版本的中文jar包，把它复制到sonarqube-7.4\extensions\plugins目录下，然后重新启动Sonarqube即可。

![2-3](https://images.gitee.com/uploads/images/2021/0901/144930_890cd194_8721401.png "2-3.png")
##### 图2-3 把中文jar包复制到指定目录

### 四、代码检测 

#### 1. 配置文件

如图3-1所示，在我们需要检查的项目目录下，新建` sonar-project.properties `配置文件：

![3-1](https://images.gitee.com/uploads/images/2021/0901/143541_64a3b155_8721401.png "3-1.png")
##### 图3-1 配置文件

配置文件内容如下：
```
sonar.projectKey=wzgy
sonar.projectName=wzgy
sonar.projectVersion=5.0
# Path to the parent source code directory.
# Path is relative to the sonar-project.properties file. Replace "\" by "/" on Windows.
# Since SonarQube 4.2, this property is optional if sonar.modules is set.
# If not set, SonarQube starts looking for source code from the directory containing
# the sonar-project.properties file.
# 项目目录
sonar.sources=F:\\EOS\\wzgy\\com.tenglong.qualitycheck\\src

# Encoding of the source code
sonar.sourceEncoding=UTF-8

# Additional parameters
sonar.my.property=value

# 项目目录
sonar.java.binaries=F:\\EOS\\wzgy\\com.tenglong.qualitycheck\\src

sonar.language=java
sonar.exclusions=**/*.js
```

具体配置说明如下：
```
sonar.projectKey=gpcore       #sonar平台中相对应项目的key
sonar.projectName=gpcore      #sonar平台中相对应项目的名字
sonar.sources=.               #sonar检测的源文件目录，‘.’表示当前根目录下的所有文件目录；包含主要源文件的目录的逗号分隔路径
sonar.exclusions=**/*_test.go,**/vendor/**      #检测中排除的源文件（排除的源文件不参与检测，一般排除单元测试文件、配置文件等）
sonar.tests=.                 #sonar检测的测试文件目录，‘.’表示当前根目录下的所有文件目录；包含测试源文件的目录的逗号分隔路径。从构建系统中读取Maven，Gradle，MSBuild项目。否则默认为空。
sonar.test.inclusions=**/**_test.go             #检测中的测试源文件（指定单元测试文件）
sonar.test.exclusions=**/vendor/**              #检测中排除的测试源文件（排除的源文件不参与检测）
```

#### 2. 创建测试项目

a）如图3-2和图3-3所示，在浏览器进入SonarQube主页，选择` 创建新项目 `：

![3-2](https://images.gitee.com/uploads/images/2021/0901/143917_f8cee95a_8721401.png "3-2.png")
##### 图3-2 创建新项目

![3-3](https://images.gitee.com/uploads/images/2021/0901/143952_f50370e3_8721401.png "3-3.png")
##### 图3-3 创建新令牌

b）如图3-4所示，选择所需检测的语言：

![3-4](https://images.gitee.com/uploads/images/2021/0901/144146_c91ae3af_8721401.png "3-4.png")
##### 图3-4 选择语言（注意，原文不是Java项目，所以选择的是其他，操作系统是window，点击完成）

c）如图3-5所示，点击` 下载 `选项，下载Windows扫描器：

![3-5](https://images.gitee.com/uploads/images/2021/0901/144438_7f17305b_8721401.png "3-5.png")
##### 图3-5 下载扫描器

d）如图3-6所示，将bin目录加入path变量中，双击启动` sonar-scanner-debug.bat `文件即可：

![3-6](https://images.gitee.com/uploads/images/2021/0901/144657_40969421_8721401.png "3-6.png")
##### 图3-6 启动bat文件

#### 3. 创建令牌

a）如图3-7所示，点击最上面的创建令牌创建一个令牌：

![3-7](https://images.gitee.com/uploads/images/2021/0901/145258_56de8e85_8721401.png "3-7.png")
##### 图3-7 创建令牌

b）如图3-8所示，我们可以看到如下信息表明令牌创建成功：

![3-8](https://images.gitee.com/uploads/images/2021/0901/145344_b5ab2ac0_8721401.png "3-8.png")
##### 图3-8 令牌创建成功

c）按照图3-8中所说，cmd进入需要测试的项目目录，把命令在项目目录下执行即可。检测完成如图3-9所示：

![3-9](https://images.gitee.com/uploads/images/2021/0901/150021_8b6744c2_8721401.png "3-10.png")
##### 图3-9 检测完成

注意，如果出现` sonar-scanner 不是命令` 这样的提示，则需要把sonar-scanner的bin目录加入到path中（见上述2d））。

d）在浏览器上访问SonarQube，观察被测项目，得到检测结果如图3-10所示：

![3-10](https://images.gitee.com/uploads/images/2021/0901/150034_8a91bcc2_8721401.png "3-11.png")
##### 图3-10 检测结果

e）点击项目进入图3-11所示页面：

![3-11](https://images.gitee.com/uploads/images/2021/0901/150152_4f8eb79e_8721401.png "3-12.png")
##### 图3-11 检测结果

f）查看各类bugs，如图3-12和图3-13所示：

![3-12](https://images.gitee.com/uploads/images/2021/0901/150310_7729f554_8721401.png "3-13.png")
##### 图3-12 bug列表

![3-13](https://images.gitee.com/uploads/images/2021/0901/150332_d09eef6a_8721401.png "3-14.png")
##### 图3-13 具体的错误

#### 注意，如果项目过大，容易出现内存溢出，这时候把需要检测的模块单独复制出来检测即可。

### 五、版权声明

本文基于CSDN博主「不想做咸鱼的王富贵」的原创文章进行修改，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。

原文链接：1）https://blog.csdn.net/weixin_43564627/article/details/107310201 ；

2）https://blog.csdn.net/weixin_43564627/article/details/107319453
