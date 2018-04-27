# 实验四：图书管理系统顺序图绘制
|学号|班级|姓名|
|:-------:|:-------------: | :----------:|
|201510414124|软件(本)15-1|熊峰|
## 1.超级管理员
### 1.1 plantUML源码如下
```
@startuml
box "__超级管理员__用例"
hide footbox

actor __超级管理员__ as superManager
actor __普通管理员__ as manager
participant __普通管理员信息__ as info

activate superManager
superManager -> manager : 管理
activate manager
manager -> info :提供个人信息
deactivate manager

activate info

info --> superManager :存储信息并进行管理
end box
@enduml
```
### 1.2 图片如下
![](./超级管理员.png '超级管理员')



## 2.普通管理员
### 2.1 plantUML源码如下
```
@startuml
hide footbox
autonumber
actor __管理员__ as manager
actor __读者__ as reader
participant __读者信息__ as readerInfo

activate manager
manager -> reader : 管理
activate reader
reader -> readerInfo :提供个人信息
deactivate reader

activate readerInfo

readerInfo --> manager :存储信息并进行管理

manager -> readerInfo:获取借阅情况
manager <- readerInfo:借书、还书信息
note right:返回消息
@enduml
```
### 2.2 图片如下
![](./管理员.png '普通管理员')


## 3.借书
### 3.1 plantUML源码如下
```
@startuml
hide footbox
title __借阅图书__
autonumber
actor __读者__ as reader
participant 借书方式 as chioce
participant 网上借阅 as inter
participant 图书馆借阅 as lib
participant 借书记录 as bookrecord
activate reader
reader ->chioce :选择借书方式

activate chioce
chioce -> inter:网上借阅？
activate inter
inter -> bookrecord :添加借阅记录
deactivate inter
activate bookrecord

chioce -> lib:图书馆借阅？
deactivate chioce
activate lib
lib -> bookrecord :添加借阅记录
deactivate lib


bookrecord -> reader :到管理员处登记信息

@enduml
```
### 3.2 图片如下
![](./借阅图书.png '借阅图书')


## 4.还书
### 4.1 plantUML源码如下
```
@startuml


hide footbox
autonumber
title __归还图书__ 用例
actor 普通管理员 as manager
boundary 账号判断 as account
control 业务判断  as business
database 数据库 as db




activate account
	manager -> account :  输入读者账号信息
	activate business
		account -> business : 获取账号信息
deactivate account
		activate db
			business -> db : 比对账号密码合法性
			db --> business : 账号合法


			manager -> business : 输入归还图书信息
			business -> db : 删除借阅信息
			business -> db : 修改图书库存
			db -> business : 返回操作结果
		deactivate db
	business -> manager : 返回归还结果
	deactivate db
	



@enduml
```
### 4.2 图片如下
![](./归还图书用例.png '归还图书')


## 5.预定
### 5.1 plantUML源码如下
```
@startuml

hide footbox
title __预定图书__ 用例
actor 读者 
boundary 权限判断
control 业务控制
database 数据库


autonumber
group 账号合法性验证
activate 权限判断
	读者 -> 权限判断 :  输入账号信息
	activate 业务控制
		权限判断 -> 业务控制 : 获取账号信息
deactivate 权限判断
		activate 数据库
			业务控制 -> 数据库 : 比对账号密码合法性
			数据库 --> 业务控制 : 账号合法
end
group 预定图书
			读者 -> 业务控制 : 输入预定图书信息
			业务控制 -> 数据库 : 增加预定信息
			数据库 -> 业务控制 : 返回操作结果
		deactivate 数据库
	业务控制 -> 读者 : 返回预定图书结果
	deactivate 业务控制
	

end

@enduml
```
### 5.2 图片如下
![](./预定图书用例.png '预定图书')

## 6.取消预定
### 6.1 plantUML源码如下
```
@startuml

hide footbox
title __取消预定__ 用例
actor 读者 
boundary 权限判断
control 业务控制
database 数据库



group 账号合法性验证
activate 权限判断
	读者 -> 权限判断 :  输入账号信息
	activate 业务控制
		权限判断 -> 业务控制 : 获取账号信息
deactivate 权限判断
		activate 数据库
			业务控制 -> 数据库 : 比对账号密码合法性
			数据库 --> 业务控制 : 账号合法
end
group 取消预定
			读者 -> 业务控制 : 输入取消预定的图书信息
			业务控制 -> 数据库 : 删除预定信息
			数据库 -> 业务控制 : 返回操作结果
		deactivate 数据库
	业务控制 -> 读者 : 返回取消预定结果
	deactivate 业务控制
	

end

@enduml
```
### 6.2 图片如下
![](./取消预定用例.png '取消预定')


