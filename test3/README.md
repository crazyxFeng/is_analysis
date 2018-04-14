# 实验三：图书管理系统领域对象建模
|学号|班级|姓名|
|:-------:|:-------------: | :----------:|
|201510414124|软件(本)15-1|熊峰|
## 一、图书管理系统类图
####  plantUMl源码如下：
```
@startuml
class 管理员信息{
    -mangerId:Interger
    -mangerName:String
    -mangerNumber:String
    -mangerAddress:String
    -mangerPhone:String
}
class 读者信息{
    -readerId:Interger 
    -readerName:String 
    -bookISBN:String 
    -lendBookTime:String 
    -returnBookTime:String
}
class 图书信息{
    -bookId:Interger
    - bookISBN:String
    -bookName:String 
    -total:Interger 
    -stock:Interger 
    -publisher:String 
    -author:String 
    -summary:String
}
class 读者{
    --个人基本信息--
    名字
    年龄
    电话
    地址
    等等....
}
class 注册用户{
    名字
    身份证号
    电话号码
    微信
    QQ
    等等...
}
class 会员{
    名字
    延长的借阅时间
    会员剩余时间
    等等....
}
class 预定的记录{
    预定的时间
}
class 借书记录{
    借书时间
    还书时间
}
class 逾期记录{
    逾期天数
    可以逾期的天数
    还书时间
}
class 超级管理员{
    普通管理员的相关信息
}
note "省略了getter和setter的方法，可在其他代码中看到" as N
读者信息 "多" --* "1" 预定的记录  :借阅
读者信息 --> 借书记录:添加
借书记录 --> 管理员信息:增加借阅信息
借书记录 --> 逾期记录
逾期记录 --> 管理员信息:处理
预定的记录 --> 管理员信息 :增加预定记录
管理员信息 "1" --* "多" 图书信息 :mange
管理员信息 "1" --* "多" 读者信息  :mange
超级管理员 "1" -- "多"管理员信息:contains
读者信息    <|--    读者
读者信息    <|--    注册用户
读者信息    <|--    会员


N .. 管理员信息
N .. 读者信息
N .. 图书信息

@enduml
```
#### 图片
![](./类图.png '类图')

## 二、图书管理系统对象图
####  plantUMl源码如下：
```
@startuml
object 超级管理员信息{
    姓名：熊峰
    年龄：23
    专业：信息科学与工程
    学校：成都大学
}
object 普通管理员{
    姓名：张三
    地址：成都市龙泉驿区成都大学十陵上街一号
    年龄：26
    电话：1520-280-2236
    其他管理员：不一一列举
}
object 读者{
    姓名：李四
    年龄：22
    电话：028-3452245
    借书的ISBN：654655162165
    借书时间：18-05-01
    还书时间：18-5-12
}
object 注册用户{
    姓名：小红
    注册时间：18-5-2
    是否会员：否
    电话：028-5689423
}
object 会员用户{
    姓名：小李
    注册时间：18-5-2
    是否会员：是
    电话：028-5689423
    能否延长借书时间：能
    可逾期时间：10天
}
object 借书记录{
    时间：18-2-5
}
object 还书记录{
    时间：18-3-5
}
object 逾期记录{
    天数：3天
    还书时间：18-3-8
}
object 图书信息{
    书名：《简爱》
    ISBN：159-456-763-5612
    作者：奥斯特洛夫斯基
    出版社：成都大学出版社
    ......
}
超级管理员信息 -->普通管理员:管理
普通管理员 --> 图书信息
普通管理员 --> 借书记录
普通管理员 --> 还书记录
普通管理员 --> 逾期记录
普通管理员 --> 读者

读者<-- 注册用户
读者<-- 会员用户
@enduml
```
#### 图片
![](./对象图.png '对象图')

## 三、图书管理员类图
#### plantUML源码如下：
```
@startuml
class MangeInfo{
    -mangerId:Interger
    -mangerName:String
    -mangerNumber:String
    -mangerAddress:String
    -mangerPhone:String
    ..getter..
    +getMangerId()
    +getMangerName()
    +getMangerNumber()
    +getMangerAddress()
    +getMangerPhone()
    ..setter..
    +setMangerId()
    +setMangerName()
    +setMangerNumber()
    +setMangerAddress()
    +setMangerPhone()
}
@enduml
```
#### 图片
![](./管理员信息.png '类图')

## 四、图书信息类图
#### plantUML源码如下：
```
@startuml
class Book{
    -bookId:Interger
    - bookISBN:String
    -bookName:String 
    -total:Interger 
    -stock:Interger 
    -publisher:String 
    -author:String 
    -summary:String
    ..getter..
    +getBookId()
    +getBookISBN()
    +getBookName()
    +getTotal()
    +getStock()
    +getPublisher()
    +getAuthor()
    +getSummary()
    ..setter..
    +setBookId()
    +setBookISBN()
    +setBookName()
    +setTotal()
    +setStock()
    +setPublisher()
    +setAuthor()
    +setSummary() 
}

@enduml
```
#### 图片
![](./图书信息.png '类图')
## 五、读者信息类图
#### plantUML源码如下：
```
@startuml
class ReaderInfo{
    -readerId:Interger 
    -readerName:String 
    -bookISBN:String 
    -lendBookTime:String 
    -returnBookTime:String
    ..getter..
    +getReaderId()
    +getReaderName()
    +getBookISBN()
    +getLendBookTime()
    +getReturnBookTime()
    ..setter..
    +setReaderId()
    +setReaderName()
    +setBookISBN()
    +setLendBookTime()
    +setReturnBookTime() 
}
@enduml
```
#### 图片
![](./读者信息.png '类图')


