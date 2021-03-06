
# 接口：check_experiment[返回](../README.md)
用例： [查看实验要求](../用例/查看实验要求.md)

- 功能：
    学生查看实验要求并完成实验
    
- 权限：
    学生：学生必须先登录之后才能查看相关实验    
    


- 请求方式 ：
    GET
      
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |experiment_id|实验的ID号。对应表EXPERIMENT.EXPERIMENT_ID的值|
  
- 返回实例：

        {         
            "status": true,
            "info": null,
            "experiment_id":"1",    
            "title":"信息分析与系统设计第一次实验(15%)",
            "start_time":"2018年5月30日"
            "end_time":"2018年6月7日",
            "content":"    1.本实验的目的是了解PlantUML标准，搭建系统分析文档编写平台，并能绘制出一些简单的业务流程。
    2.重新绘制Page107图6.1: 考试及成绩管理流程
    3.重新绘制Page108图6.2: 客户维修服务流程
    4.重新绘制的两个流程图要汇总到REMADE.md文本文件中进行说明，说明文件用Markdown格式编写。"            
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |experiment_id|实验的ID号|
  |title|实验标题|  
  |start_time|实验发布时间|
  |end_time|实验结束时间|
  |content|要完成的实验内容|

