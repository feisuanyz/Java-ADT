## Soflu社区版快速入门教程

### 1. 下载本地客户端

在注册登录使用全自动开发平台社区版之前，您需要先[下载](https://main.feisuanyz.com:8080/flow-community/feisuanyz-local-engine.zip)并启动本地客户端。

说明：本地客户端用于实现用户将平台上开发的项目部署到自己的本地主机上，主要可以解决网络、安全、效率等问题。

本地客户端下载和启动的Java运行环境必须是JDK1.8.1及以上版本。
 
### 2. 启动本地客户端

用户在启动本地客户端时，可能会存在两种操作环境：Windows系统和Linux系统，以下将对这两种操作环境下启动本地客户端的情况进行分别介绍。

#### 2.1 操作步骤
##### 2.1.1 Windows系统启动方式

a）解压下载的本地客户端引擎包

b）双击` startup.bat `运行启动本地客户端，如图1-1所示：

![image](https://user-images.githubusercontent.com/79617492/174986315-fb4534c0-24b0-47b5-8421-f01cba052b25.png)

##### 图1-1 启动本地客户端服务器
 
c）启动后，系统会自动生成` log_info.log `日志文件，出现如图1-2所示日志信息，说明本地客户端启动成功。

![image](https://user-images.githubusercontent.com/79617492/174986372-42bdb6c8-1045-4679-bf68-9653f4d4b89c.png)

##### 图1-2 查看日志信息
 
说明：本地客户端默认不需要配置任何内容，启动端口默认为` 8080 `，日志文件默认存储到当前安装包目录下面的` logs `文件夹中（若安装包为` feisuanyz-local-engine-1.0.3 `，则日志生成路径是` feisuanyz-local-engine-1.0.3/logs `）。

d）若需修改端口、日志存放路径配置，您需要创建一个` application.yml `文件，该文件需要与` feisuanyz-local-engine.jar `文件存放到同一目录中，` application.yml `文件创建模板如下：
```
server:
 # 服务端口
port: 8080
 
# 系统日志配置
logging:
    file:
        path: /logs


# 系统日志存储到kafka
logging:
    config: classpath:logback-kafka.xml

# kafka相关配置，日志默认是保存到本地文件中，我们也支持将日志存储到kafka，需要按照下面模板进行配置
fs:
    kafka:
        producer-enabled: true
        producers:
            logback:
            # kafka集群地址
                bootstrapservers: bootstrap.servers=127.0.0.1:9092,127.0.0.2:9093,127.0.0.3:9092
                # topic
        topic: flow-system-logs

```

注意：` application.yml `文件中日志的存储方式只能选择一种。

##### 2.1.2 Linux系统启动方式

a）上传本地客户端引擎包至目标服务器并解压、添加执行脚本执行权限，执行` startup.sh `启动本地客户端，如图1-3所示：

![image](https://user-images.githubusercontent.com/79617492/174986421-5c40c7f4-216c-463f-bcc4-863482f72a54.png)

##### 图1-3 启动客户端服务器
 
b）系统日志输出如图1-4所示，说明本地客户端启动成功：

![image](https://user-images.githubusercontent.com/79617492/174986430-24b3928c-0495-4718-a60e-16dde79d1600.png)

##### 图1-4 查看日志信息
 
### 3. 社区版注册与登录

下载并启动好本地客户端之后，便可以进行社区版的注册。

#### 3.1 操作步骤

a）如图2-1所示，打开浏览器，在地址栏中输入“ http://服务器地址:服务端口 ”（例如输入 http://10.10.10.11:8080 ），并按“Enter”键，进入社区版登录页面。注意“服务器地址”为当前部署Local客户端的服务器IP地址；“端口”默认为` 8080 `，若为自定义端口，请填写自定义端口。

![image](https://user-images.githubusercontent.com/79617492/174987374-f410880f-662f-472b-88d3-74f2431e9767.png)

##### 图2-1 社区版登录页面
 
b）单击“免费注册”，系统显示会员注册页面，如图2-2所示：

![image](https://user-images.githubusercontent.com/79617492/174987668-b88f46be-e0c5-421a-a3f0-4fde89913bf4.png)

##### 图2-2 会员注册页面
 
c）请根据实际情况填写注册的基本信息。

d）滑动滚动条验证通过后，选中“阅读并同意”按钮。

e）单击“同意条款并注册”，如图2-3所示：

![image](https://user-images.githubusercontent.com/79617492/174987696-22e7088e-8f7f-4292-a384-38bbb378225f.png)

##### 图2-3 输入注册用户信息
 
f）输入注册手机号的验证码，单击“确认”，如图2-4所示：

![image](https://user-images.githubusercontent.com/79617492/174987727-9942ffbf-f718-46bc-8363-648c93e6f02a.png)

##### 图2-4 输入验证码页面
 
g）输入注册用户名和密码，单击“登录”，如图2-5所示：

![image](https://user-images.githubusercontent.com/79617492/174987793-2b399094-d655-4858-8fc7-478c92ef39fe.png)

##### 图2-5 登录社区版页面
 
### 4. 基本操作指引

#### 4.1 如何创建项目

a）选择“项目管理”，系统默认显示“项目管理”页面，如图3-1所示：

![image](https://user-images.githubusercontent.com/79617492/175227344-cd5d4be2-a518-420c-b73e-2a6bf26ed04b.png)

##### 图3-1 默认项目管理页面
 
b）单击“创建项目”，系统显示“新增项目”页面，如图3-2所示：

![image](https://user-images.githubusercontent.com/79617492/175227356-3aa2ba15-fc12-4edc-847b-589a267e6551.png)

##### 图3-2 新增项目页面
 
c）在“新增项目”页面，请根据实际需求输入项目的基本信息，如图3-3所示：

![image](https://user-images.githubusercontent.com/79617492/175227383-4e8aa8b8-1dab-4e2f-933e-159555d165c2.png)

##### 图3-3 配置项目信息页面
 
d）单击“确定”，系统显示“项目加载项”页面，如图3-4所示：

![image](https://user-images.githubusercontent.com/79617492/175227414-9eefab8a-c1b0-4324-95c9-e39034d592d3.png)

##### 图3-4 项目加载项页面
 
e）在加载项页面中平台集成了开发微服务项目使用到的组件、函数、插件、资源以及JAR扩展包，请根据实际选择开发需求所涉及到的组件或者资源，单击“加载应用”，完成新增微服务项目。

f）默认创建的项目为启动状态，如果创建的项目显示已经停止。请单击项目卡片上的“已停用”，在系统弹出提示框中选择“启用”，如图3-5所示：

![image](https://user-images.githubusercontent.com/79617492/175227434-2e2d42f9-6198-41b7-940b-30adc73c5865.png)

##### 图3-5 启用微服务项目页面
 
#### 4.2 如何创建接口

a）在项目管理页面中，选择“接口管理”，系统显示接口管理页面，如图3-6所示：

![image](https://user-images.githubusercontent.com/79617492/175227469-4f0657ba-3d9e-4fba-a5e5-f0b3512af118.png)

##### 图3-6 选择接口管理

b）单击“新增接口模块”，系统显示“新增接口模块”，输入接口模块的信息，如图3-7所示：

![image](https://user-images.githubusercontent.com/79617492/175227490-ec24526e-9fea-4ee1-a5dc-45fa2821a044.png)

##### 图3-7 新增接口模块

c）单击“确定”。

系统提示“新增成功”。

e）单击已新增模块后的“+”，选择“新增接口”，如图3-8所示：

![image](https://user-images.githubusercontent.com/79617492/175227505-b752177a-ad67-4653-ba88-28ec8154629f.png)

##### 图3-8 新增接口

f）在“新增接口信息 > 基本信息”页面，配置接口的基本信息，如图3-9所示：

![image](https://user-images.githubusercontent.com/79617492/175227631-b20d919d-71c1-4d6e-83c8-340f4234feeb.png)

##### 图3-9 配置新增接口的基本信息

g）单击“下一步”。

h）在“新增接口信息 > 入参列表”页面，配置接口的入口参数，如图3-10所示：

![image](https://user-images.githubusercontent.com/79617492/175227657-3e36fba1-dd72-457c-a2c6-d610f9d09de7.png)

##### 图3-10 配置新增接口的入口参数

i）单击“输出结果类型配置 > 输出结果项”，配置接口输出结果的信息，如图3-11所示：

![image](https://user-images.githubusercontent.com/79617492/175227676-f4fce659-4eeb-4641-b242-c185887be98a.png)

##### 图3-11 配置新增接口的输出结果项

说明：在接口输出结果类型配置中至少要包括“响应码”、“返回信息”和“返回数据”这三种配置项，则需要按照以下要求进行配置，假设使用：

a'）` code `代表“响应码”、` msg `代表“返回信息”、` data `代表“返回数据”；

b'）` code `、` msg `类型选择` String `，` data `类型选择` Object `；

c'）` data `返回业务数据的“动态获取值”选择为是。

j）单击“输出结果类型配置 > 输出结果内容”，配置接口输出结果的信息，如图3-12所示：

![image](https://user-images.githubusercontent.com/79617492/175227706-eb89e143-a35f-4bbd-b2f3-99742931824d.png)

##### 图3-12 配置新增接口的输出结果内容

说明：

a'）当响应码` code `输入` 000000 `，返回信息` msg `代表成功；

b'）当响应码` code `输入` 999999 `，返回信息` msg `代表失败。

k）单击“新增入口参数”，配置接口的入口参数信息，如图3-13所示：

![image](https://user-images.githubusercontent.com/79617492/175227728-a9d7687c-2d55-4510-97df-54b3744974ab.png)

##### 图3-13 配置新增接口的入口参数信息

l）在“输出结果 > 选择数据”页面，选择输出结果的“成功”项，如图3-14所示。

![image](https://user-images.githubusercontent.com/79617492/175227746-61f2e9c3-84c3-4c53-b9ed-1818dbb0febc.png)

##### 图3-14 选择输出结果的成功项

m）完成新增接口的入口参数的信息配置，如图3-15所示：

![image](https://user-images.githubusercontent.com/79617492/175227769-3e3049ff-977d-440a-8109-d7f86661f11c.png)

##### 图3-15 配置新增接口的入口参数

n）单击“提交，进入“模型”页面”，如图3-16所示：

![image](https://user-images.githubusercontent.com/79617492/175227785-6f5a4c4f-95b8-4023-85de-74bf3a7f579f.png)

##### 图3-16 新增接口信息的模型页面

o）单击“进入模型编辑”，系统显示“窗体视图”页面，选择“组件列表 > 工具 > 输出结果”，拖拽“输出结果”组件至视图区域，如图3-17所示：

![image](https://user-images.githubusercontent.com/79617492/175227804-549eb515-0852-47d9-8cfe-d541a5ee7246.png)

##### 图3-17 窗体视图

p）连接组件的流程图，如图3-18所示：

![image](https://user-images.githubusercontent.com/79617492/175227824-62f0c9c5-91fc-445d-97b6-a2c218e93798.png)

##### 图3-18 连接组件流程图

q）选中流程图中的输出结果组件，在右侧输出结果中配置“响应结果”，如图3-19所示：

![image](https://user-images.githubusercontent.com/79617492/175227905-fe7c352e-aa6a-4da3-ad2b-37adc634f56d.png)

##### 图3-19 配置输出结果的响应结果

r）单击“确认”，完成配置响应结果。

s）选中流程图中的输出结果组件，在右侧输出结果中配置“输出项值”，如图3-20、图3-21、图3-22、图3-23所示：

![image](https://user-images.githubusercontent.com/79617492/175227931-175f92f4-92df-4790-928d-c93a8683f1d2.png)

##### 图3-20 配置输出结果的输出项值

![image](https://user-images.githubusercontent.com/79617492/175227975-853746b2-995e-47ec-98f9-61c72cae095d.png)

##### 图3-21 选择值类型

![image](https://user-images.githubusercontent.com/79617492/175227994-c4b346e3-ee6d-44b2-88ca-8d3eb3fa8c3a.png)

##### 图3-22 选择流程变量

![image](https://user-images.githubusercontent.com/79617492/175228011-de14e46e-bfa4-4a07-b539-fc1068c4306d.png)

##### 图3-23 选择接口根参数

t）单击“确定”，完成配置输出项值，如图3-24所示：

![image](https://user-images.githubusercontent.com/79617492/175228060-445fdabe-0cf4-416e-abd7-285ea9515640.png)

##### 图3-24 配置输出项值

u）单击“确定”，完成组件配置，如图3-25所示，单击“保存并退出”：

![image](https://user-images.githubusercontent.com/79617492/175228089-b2c0b9ff-4165-41bb-901f-9a0d609d443f.png)

##### 图3-25 保存组件配置

v）单击“提交”，完成接口配置，如图3-26所示：

![image](https://user-images.githubusercontent.com/79617492/175228107-7b669dbd-81c1-4060-a5e5-b4d62bd9cc0f.png)

##### 图3-26 提交接口配置

w）单击“提交”后的“...”，选择“发布接口”，如图3-27所示：

![image](https://user-images.githubusercontent.com/79617492/175228127-d51d5f1c-f706-484a-ac55-a978f5292dbe.png)

##### 图3-27 发布接口

x）单击“提交”后的“...”，选择“测试用例”，如图3-28所示：

![image](https://user-images.githubusercontent.com/79617492/175228435-76545ae5-bcc7-453c-9180-6cdb1f8d7963.png)

##### 图3-28 测试接口用例

y）单击“编辑”，配置` Body `参数信息，如图3-29所示：

![image](https://user-images.githubusercontent.com/79617492/175228447-dfb26969-ce0b-4b10-8dc7-7757495094c9.png)

##### 图3-29 配置测试用例参数

z）单击“保存”保存配置，单击“执行”执行测试用例并查看执行输出结果，如图3-30所示：

![image](https://user-images.githubusercontent.com/79617492/175228850-aa14d0e9-bcf3-4458-83b0-ab3fdcdf8afb.png)

##### 图3-30 执行测试用例并查看输出结果

#### 4.3 如何新增资源实例

a）在项目管理页面中，选择“资源实例”，如图3-31所示：

![image](https://user-images.githubusercontent.com/79617492/175228874-44fd44ee-023b-4245-98b1-de34459692a6.png)

##### 图3-31 选择资源实例

b）单击“分布式中间件”后的“+”，选择“新增资源实例”，如图3-32所示：

![image](https://user-images.githubusercontent.com/79617492/175228889-32bf65bd-ac6d-43a9-a857-9ec47459e946.png)

##### 图3-32 新增资源实例

c）在“资源实例管理”页面，选择系统默认的环境，配置新增资源实例的配置项信息，如图3-33所示：

![image](https://user-images.githubusercontent.com/79617492/175228914-9e365e88-5ed4-4e78-a042-a8c011edd6a7.png)

##### 图3-33 配置资源实例的配置项

说明：

本节是以配置分布式中间件为样例做说明，其他资源配置的配置项，请根据实际进行配置。

目前分布式中间件的配置项包括：ZK地址、DAL组、超时时间、重试次数。

d）单击“提交”。

系统提示“新增成功”。

e）在“资源实例管理”页面，成功新增一个分布式中间件DAL，如图3-34所示：

![image](https://user-images.githubusercontent.com/79617492/175228962-9596ebbc-a8a7-4864-9aeb-a4614863c13c.png)

##### 图3-34 新增分布式中间件DAL

#### 4.4 如何新增实体模型

a）在项目管理页面中，选择“实体模型”，系统显示实体模型页面，如图3-35所示：

![image](https://user-images.githubusercontent.com/79617492/175229013-3658ec8e-536f-4122-b7a1-6e57e04353a2.png)

##### 图3-35 选择实体模型模块

b）单击“新增实体模型模块”，系统显示“新增实体模型模块”，输入名称和描述信息，如图3-36所示：

![image](https://user-images.githubusercontent.com/79617492/175229090-6f250387-f1e9-4c57-87af-221f45b6a822.png)

##### 图3-36 新增实体模型模块

c）单击“确定”。

d）选择实体模型模块，单击“+”，选择“新增实体模型”，系统显示新增实体模型，如图3-37所示：

![image](https://user-images.githubusercontent.com/79617492/175229292-6fea8a7f-ae2f-4d06-9a73-cf65b8b59011.png)

##### 图3-37 新增实体模型

e）输入实体模型的名称和描述，单击“新增”，系统自动新增实体模型字段，请根据事实添加实体模型字段，如图3-38所示：

![image](https://user-images.githubusercontent.com/79617492/175229409-01cc1f02-030f-4828-bd15-45f23ac6073f.png)

##### 图3-38 添加实体模型字段

f）单击“提交”。

#### 4.5 如何连接数据库

前提条件：目前全自动开发平台只能支持连接公网的数据库。

a）在项目管理页面中，选择“数据库设计”，如图3-39所示：

![image](https://user-images.githubusercontent.com/79617492/175229434-1f0c7443-87b8-4c2e-967e-0fcb772c2047.png)

##### 图3-39 选择数据库设计

b）单击“新增数据库”，系统显示“新增项目数据库”页面，输入数据库名称，如图3-40所示：

![image](https://user-images.githubusercontent.com/79617492/175229452-b8333786-ef57-4f76-9958-3cda8351be7e.png)

##### 图3-40 新增数据库

c）单击“确定”。

d）单击已经创建数据库后的树形省略号，选择“数据库连接”，如图3-41所示：

![image](https://user-images.githubusercontent.com/79617492/175229481-856d2a7d-2f31-47bc-b295-0738d1f94654.png)

##### 图3-41 选择数据库连接

e）在“数据库连接管理”页面，单击“新增”，如图3-42所示：

![image](https://user-images.githubusercontent.com/79617492/175229495-5429f858-3c41-4c02-9b53-9ff4862a4943.png)

##### 图3-42 新增数据库配置

f）在“新增数据库连接”页面，配置项目数据库的相关信息，如图3-43所示：

![image](https://user-images.githubusercontent.com/79617492/175229508-36565c8c-24e1-467e-bc07-75fc4cf40acf.png)

##### 图3-43 新增数据库配置信息

说明：

其中数据库的“连接名”可自行定义。

若想自定义` URL` ，请打开“是否自定` URL `”的开关，然后在“地址”栏输入定义的` URL `。

g）在“新增数据库连接”页面，单击“测试”，测试连接的数据库是否正确。如图3-44所示：

![image](https://user-images.githubusercontent.com/79617492/175229525-e1fd63bb-b35f-47f9-a39d-b98292797454.png)

##### 图3-44 测试连接数据信息

若提示“连接成功”信息，说明连接数据库正确。

若提示失败信息，请检查连接数据库的相关配置信息，请修改为正确再重新测试。

h）单击“提交”，统提示“新增成功”信息，如图3-45所示：

![image](https://user-images.githubusercontent.com/79617492/175229544-766df7d8-52a3-4562-bd8a-7193d3277ebc.png)

##### 图3-45 新增数据库

说明：

您可以单击“删除”列的删除按钮，删除连接的数据库。

您可以单击“删除”列的修改按钮，修改连接的数据库的配置信息。

#### 4.6 如何新增SQL信息

a）选择“` SQL `管理”，系统显示“` SQL `管理”页面，如图3-46所示：

![image](https://user-images.githubusercontent.com/79617492/175229574-00008780-8f97-404f-83f5-289caceb840b.png)

##### 图3-46 SQL管理页面

b）单击“新增` SQL `组”，系统显示“新增` SQL `组”页面，输入` SQL `组的相关信息，如图3-47所示：

![image](https://user-images.githubusercontent.com/79617492/175229597-6bdbc209-35c6-4683-aae0-7d2dcddb3117.png)

##### 图3-47 新增SQL组

说明：

如果填写数据库名称，在该组里面创建的` SQL `语句，在执行` SQL `语句时，则指向数据库里面的表，例如表查询操作，则只能查询该数据库的表。

中间件：请单击下拉框选择中间件，如何添加中间件，具体请参见“如何新增资源实例”。

c）单击“提交”。

系统提示“新增成功”，完成新增` SQL `组，如图3-48所示：

![image](https://user-images.githubusercontent.com/79617492/175229622-ff6c4ab3-8e84-40bc-821f-c491bf0cf5fa.png)

##### 图3-48 新增SQL组

d）单击“添加模块”，系统显示“新增` SQL `模块”对话框，输入` SQL `模块名称及描述，如图3-49所示：

![image](https://user-images.githubusercontent.com/79617492/175229635-61b25276-1c90-4c45-8e15-b964747039a1.png)

##### 图3-49 添加SQL模块

e）单击“确定”。

系统提示“新增成功”。

f）选择需要添加` SQL `信息的` SQL `模块，如图3-50所示：

![image](https://user-images.githubusercontent.com/79617492/175229773-12f1811a-83d8-4767-ba19-89da419cd750.png)

##### 图3-50 选择SQL模块

g）单击“新增` SQL `信息”，系统显示“新增` SQL `信息”对话框。填写` SQL `名称、选择` SQL `类型、填写超时时间和描述，在“` SQL `内容”输入` SQL `信息，如图3-51所示：

![image](https://user-images.githubusercontent.com/79617492/175231844-663caac4-6340-4f37-b282-31b97313be97.png)

##### 图3-51 配置SQL信息

h）单击“字段映射配置”，单击“新增”，新增对应的` SQL `字段映射关系，如图3-52所示：

![image](https://user-images.githubusercontent.com/79617492/175232135-454ecb95-e800-4288-9066-b6923d4b83af.png)

##### 图3-52 配置字段映射

说明：

目前只有查询的` SQL `信息才需要配置字段映射关系。

您可以单击“删除”，删除新增的映射字段。

i）单击“确定”。

j）单击“` SQL `在线调试”，系统显示“` SQL `在线调试”页面；单击“开始校验”，校验结果如图3-53所示：

![image](https://user-images.githubusercontent.com/79617492/175232434-1105752f-4824-4eba-a747-eba3b44719ff.png)

##### 图3-53 SQL在线调式

说明：

若查询的表没有数据，则校验的结果为无数据。

若查询的表有数据，则会展示表的字段及相关的数据信息。

若出现报错信息，则说明创建的` SQL `信息有错误，请修改为正确后再执行校验。

k）单击“保存”，完成新增` SQL `信息，如图3-54所示：

![image](https://user-images.githubusercontent.com/79617492/175232822-45d5d9dd-b16b-488f-ae09-f611a6e04e55.png)

##### 图3-54 完成新增SQL信息

系统提示“新增成功”。

#### 4.7 如何对项目发版

a）选择已经创建项目的卡片，单击“齿轮”图标，选择“发版”，如图3-55所示：

![image](https://user-images.githubusercontent.com/79617492/175233070-02228583-23b3-4db0-aadb-309d077fa250.png)   

##### 图3-55 发版

b）在“项目发版”页面中，输入项目发版的标签和描述，如图3-56所示：

![image](https://user-images.githubusercontent.com/79617492/175233112-4ef0904a-07e4-42d5-985d-71c060c9e0af.png)

##### 图3-56 项目发版页面

c）单击“确定”。
   
系统提示“正在生成项目数据包,请于2分钟后查看最新发版记录！”。

d）单击“齿轮”图标，选择“发版记录”，如图3-57所示：

![image](https://user-images.githubusercontent.com/79617492/175233145-4986394a-cbe7-4aa4-a979-9c8452def115.png)

##### 图3-57 发版记录

e）在项目“发版记录”页面，进行查看项目发版记录的信息，如图3-58所示：

![image](https://user-images.githubusercontent.com/79617492/175233176-e5164df8-bb7e-4eae-836a-7ab31335e45b.png)

##### 图3-58 项目发版记录页面

#### 4.8 如何部署项目

前提条件：您已经完成了项目发版的操作，详见快速入门4.7如何对项目发版。

项目部署主要分为以下几步：1）下载执行引擎包；2）下载项目部署包；3）其他配置操作。

#### 4.8.1 下载执行引擎包

a） 进入平台项目管理页面，单击页面右上方的下载按钮，如图3-59所示：

![image](https://user-images.githubusercontent.com/79617492/175233228-20bd924b-c692-4df5-9db2-2e636ca6489f.png)

##### 图3-59 项目管理页面

b）进入开发辅助工具页面，单击“执行引擎”图标下载执行引擎包保存至本地PC，如图3-60所示：

![image](https://user-images.githubusercontent.com/79617492/175233278-32794f9c-707e-481f-a0cc-7b141884b635.png)

##### 图3-60 开发辅助工具页面

#### 4.8.2 下载项目部署包

a）选择需进行项目部署的项目卡片，单击“齿轮”图标，选择“发版记录”，如图3-61所示：

![image](https://user-images.githubusercontent.com/79617492/175233303-c59c0adc-e300-415c-9ab7-55f22a9d2f83.png)

##### 图3-61 选择发版记录

b）在“发版记录”页面中，单击“操作”列中如图3-62所示按钮，下载项目部署包：

![image](https://user-images.githubusercontent.com/79617492/175233347-ba9e428b-ff32-4819-b823-f740467da607.png)

##### 图3-62 下载项目部署包

c）在系统弹出“选择环境”对话框中选择开发项目的默认环境，如图3-63所示：

![image](https://user-images.githubusercontent.com/79617492/175233390-c553403a-5f96-477b-b831-6ffa9cd5f8ba.png)

##### 图3-63 选择环境

说明：

一般选择默认环境即可，例如：默认开发环境为“测试环境”，部署包则选择测试环境。

d）单击“确定”即开始下载，并保存至本地PC。

#### 4.8.3 其他配置操作

a）解压下载的执行引擎包` feisuanyz-engine.zip `，如图3-64所示：

![image](https://user-images.githubusercontent.com/79617492/175233431-fb1c7c17-62b6-4023-9d86-d18b1c8f0c5e.png)

##### 图3-64 解压执行引擎包

b）将下载的项目部署包（假设为` newproject_606ff50b57da6c00088985b0_v5-deploy.zip `），移到执行引擎包的` apps `目录下。

说明：

如果解压后的执行引擎包没有` apps `目录，请手工创建` apps `目录。

项目部署默认不需要配置任何内容，启动端口默认为` 8080 `，日志文件默认存放在当前执行引擎包目录下面的` logs `目录中（该目录在项目服务启动后自动生成）。

例如：若解压后的执行引擎包为` feisuanyz-engine-3.0.12 `，则日志生成路径是` feisuanyz-engine-3.0.12/logs `。如果需要修改配置，您需要创建一个` application.yml `文件，该文件需要与` feisuanyz-engine.jar `存放到同一目录中。

` application.yml `文件创建模板如下：
```
server:
    # 服务端口
    port: 8080

# 系统日志配置（日志二选一）
logging:
    file:
        path: /logs


# 系统日志存储到kafka（日志二选一）
logging:
    config: classpath:logback-kafka.xml

# kafka相关配置，日志默认是保存到本地文件中，我们也支持将日志存储到kafka，需要按照下面模板进行配置
fs:
    kafka:
        producer-enabled: true
        producers:
            logback:
            # kafka集群地址
                bootstrapservers: bootstrap.servers=127.0.0.1:9092,127.0.0.2:9093,127.0.0.3:9092
                # topic
        topic: flow-system-logs
```

注意：` application.yml `的日志的存储方式只能选择一种。

#### 可选 c）如果在Windows操作系统部署项目，则执行以下操作：

按下“Windows+R”键，输入cmd，调出命令行窗口；

进入执行引擎包的路径；

输入` startup.bat `按回车启动项目服务，如图3-65所示：

![image](https://user-images.githubusercontent.com/79617492/175233813-04b988e9-3295-470c-8cb7-1dd27f380229.png)

##### 图3-65 在Windows部署项目

注意：默认服务端口是` 8080 `，日志存放路径是当前部署项目根目录，例如：` \feisuanyz-engine-3.0.12\logs `。

#### 可选 d）如果在Linux操作系统部署项目，则执行以下操作：

使用工具或者通过二进制方式上传项目部署包至安装的服务器；

进入当前项目的安装路径下；

执行以下命令给安装脚本添加执行权限：

```
chmod a+x startup.sh
chmod a+x shutdown.sh
```

执行` ./startup.sh `启动项目服务，如图3-66所示：

![image](https://user-images.githubusercontent.com/79617492/175234446-bee0b9c9-3add-47cc-ace8-771e5af777c4.png)

##### 图3-66 启动项目服务

注意：

` startup.sh `为启动服务脚本。

` shutdown.sh `为停止服务脚本。

默认服务端口是` 8080 `，日志存放路径是当前部署项目根目录，例如：` /feisuanyz-engine-3.0.12/logs `。

#### 4.9 如何加载资源

本节主要介绍向已创建微服务项目中加载资源的具体操作方法。

#### 4.9.1 操作步骤

a）选择已创建项目的项目卡片，单击“设置”选项，选择“加载项”，如图3-67所示：

![image](https://user-images.githubusercontent.com/79617492/175234507-4f300923-58a3-4423-9647-837c9784292e.png)

##### 图3-67 选择项目卡片

b）在系统显示的“项目加载项”页面中，单击“资源”页签，如图3-68所示：

![image](https://user-images.githubusercontent.com/79617492/175234534-d124c450-65ad-4d60-ae91-29ffc42433c5.png)

##### 图3-68 项目加载项页面

c）选择“资源”页签中需要添加的资源，单击“添加”按钮，如图3-69所示：

![image](https://user-images.githubusercontent.com/79617492/175234558-61c1a1b5-61db-45a4-89c8-7a0b8a6fae6c.png)

##### 图3-69 添加资源

d）单击“加载应用”，完成项目资源的添加。

#### 4.10 如何自动生成SQL信息

本节主要介绍如何通过全自动开发平台自动生成SQL信息。

#### 4.10.1 前提条件

您已经成功连接数据库。

您已经成功连接中间件资源。

#### 4.10.2 操作步骤

a）在平台功能模块界面中，选择“接口生成器”功能模块，系统显示“接口生成器”页面，如图3-70所示：

![image](https://user-images.githubusercontent.com/79617492/175234600-2ba49ff6-584c-4816-8cd0-c746b8f02ae9.png)

##### 图3-70 选择接口生成器

b）选中数据库，如图3-71所示，单击“下一步”：

![image](https://user-images.githubusercontent.com/79617492/175234623-e04036a2-1853-43ca-94f1-64c7b8040f1b.png)

##### 图3-71 选择数据库

c）勾选需要生成的SQL信息的表，如图3-72所示，单击“下一步”：

![image](https://user-images.githubusercontent.com/79617492/175234649-623ce742-2c96-4946-900b-30c59d919daf.png)

##### 图3-72 选择数据库表

d）勾选生成的SQL信息类型，选择SQL组和SQL模块，如图3-73所示：

![image](https://user-images.githubusercontent.com/79617492/175234675-dc54823e-4293-4ba5-8c50-6aeb4fcf0803.png)

##### 图3-73 选择SQL类型

e）单击“生成接口”，系统提示操作成功。

f）选择“SQL管理”功能模块，进入对应的SQL组和SQL模块查看SQL信息，如图3-74所示：

![image](https://user-images.githubusercontent.com/79617492/175234700-0f293337-72e2-41a8-9914-3e57002ec1f0.png)

##### 图3-74 SQL信息自动生成
