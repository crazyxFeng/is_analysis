
# 接口：changeUserInfo  [返回](../README.md)
用例： [修改用户信息](../用例/修改用户信息.md)

- 功能：
    修改用户的GitHub用户名。
    修改用户的的密码。

    
- 权限：
    学生/老师：修改自己的密码和github用户名，必须先登录。    
    
- API请求地址： 
    接口基本地址/v1/api/setUserInfo

- 请求方式 ：
    POST

- 请求实例：

        {
            "id":"21048329823",
            "github_username":"ABCDE",            
            "password":"asdas6581155",            
            "re_password":"asdas6581155",            
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |user_id|用户的ID号。对应表USERS.USER_ID的值|
  |github_username|用户GitHub用户名。| 
  |password|用户修改的密码，不是原文，是加密后的字符串| 
  |re_password|用户重复输入的密码。不是原文，是加密后的字符串| 
  
- 返回实例：

        {         
            "status": true,
            "info": null
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|


