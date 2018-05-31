
# 接口：getStudentInfo  [返回](../README.md)
用例： [查看用户信息](../用例/查看用户信息.md),[修改用户信息](../用例/修改用户信息.md)

- 功能：
    查看学生的所有信息。
    
- 权限：
    学生：查看自己的信息，必须先登录，无法查看别人的信息。    
    
- API请求地址： 
    接口基本地址/v1/api/getUserInfo/<user_id>

- 请求方式 ：
    GET
      
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |student_id|用户的ID号。对应表STUDENTS.STUDENT_ID的值|
  
- 返回实例：

        {         
            "status": true,
            "info": null,
            "ID":"201510421",    
            "name":"小明",
            "class_dept":"软件工程1班"
            "github_username":"crazyJack",
            "type":"学生"            
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |ID|学号|
  |name|用户的真实姓名|  
  |class_dept|班级名称|
  |github_username|gitHub用户名|
  |type|学生|

