# Linux基础课

## 6. thrift教

各版本信息：

### 1.init lessone\_folder:
将文件夹git init，并上传到git仓库
此版本仅有文件夹：thrift
包含了两个thrift文件 match.thrift//定义匹配接口，
                     save.thrift//定义服务器保存用户信息接口
上述两个文件由thrift官方文档,[thrift definition file](https://gitbox.apache.org/repos/asf?p=thrift.git;a=blob;hb=HEAD;f=tutorial/tutorial.thrift)

### 2.add match server:
新增match-server文件夹，并使用thrift官方文档的tutorial [C++ tutorial](https://thrift.apache.org/tutorial/cpp.html)
命令：thrift -r --gen cpp match.thrift//带路径
加入我们需要的功能代码

### 3.add client:

新增game文件夹，使用[thrift tutorial](https://thrift.apache.org/tutorial/py.html)
创建client.py文件，依据tutorial中的[样例代码](https://gitbox.apache.org/repos/asf?p=thrift.git;a=blob;hb=HEAD;f=tutorial/py/PythonClient.py)进行修改使用
注意，py文件中，from import路径中不要带有“-”，所以文件夹注意要将-换成\_


### 4.add input function of client:

修改client.py，实现使用输入实现add 和 remove的操作
例如：
add 1 xiaoming 90
add 2 xiaojiang 91
rm 1 xiaoming 90

### 5.match-server version:2.0:
与python类似，cpp文件中最好也不要在include路径中加入"-",使用"\_"替代
在main.cpp中加入了线程池，互斥锁，实现了互斥访问与多线程处理

### 6 modify readme.md:

修改readme文档，记录每一个版本的改动

### 7 add cloud\_server data storage:

使用thrift文件夹下面的save.thrift 在 match\_system下generate一个thrift cpp tutorial，另外由于我们这次添加的是客户端，不需要服务端cpp文件，所以将.skeleton.cpp后缀文件删除！

再在main.cpp内加入实例客户端代码，在Pool类save\_result函数下 注意修改自定义

连接上云服务器后，在对应的文件夹下生成文件，写入当前匹配成功的两个用户的信息


### 8  upgrade matching method:

本版本主要将匹配机制升级，将原有的先到先匹配机制改为，分数相差在50分以内进行匹配

### 9 TSimpleServer upgrade ThreadServer:

将单线程处理升级为多线程服务

### 10 upgrade matching method with time:

根据分段和匹配等待时间进行综合考虑匹配
