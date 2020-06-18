# SpringBoot整合RabbitMQ
> 本项目博客地址 ：[SpringBoot整合RabbitMQ之 典型应用场景实战一](https://blog.csdn.net/u013871100/article/details/82982235)

### 二、Docker安装RabbitMQ

```shell
#  拉取镜像
1. docker pull rabbitmq:management
#  运行镜像，使用当前目录做为挂载目录
2. docker run -d --name rabbitmq3.7.7 -p 5672:5672 -p 15672:15672 -v `pwd`/data:/var/lib/rabbitmq --hostname myRabbit -e RABBITMQ_DEFAULT_VHOST=my_vhost  -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=admin rabbitmq:management
#  查看正在运行镜像
3. docker ps 
#  查看镜像运行日志
4. docker logs -f container
#  进入到镜像内部
5. docker exec -it container /bin/bash
#  设置RabbitMQ用户的权限
6. rabbitmqctl set_permissions -p "my_vhost" admin ".*" ".*" ".*
```

### 三、参考资料
- [SpringBoot整合RabbitMQ之 典型应用场景实战一](https://blog.csdn.net/u013871100/article/details/82982235)
- [Spring Boot整合RabbitMQ详细教程](https://blog.csdn.net/qq_38455201/article/details/80308771)
- [RabbitMQ与多线程](https://blog.csdn.net/qq_37653556/article/list/1)
- [Springboot 整合RabbitMq ，用心看完这一篇就够了](https://blog.csdn.net/qq_35387940/article/details/100514134)


### 四、异常记录
> RabbitMQ3.3.1之后出于安全考虑,禁止使用guest来登录。新建用户后要设置权限：
> 
> `rabbitmqctl set_permissions -p "my_vhost" admin ".*" ".*" ".*"`

> 因为连接RabbitMQ用户没有权限导致：设置权限 rabbitmqctl set_permissions -p "<your_vhost>" <username> ".*" ".*" ".*"
[RabbitMQ连接异常:com.rabbitmq.client.ShutdownSignalException: connection error; protocol method](https://blog.csdn.net/heni6560/article/details/83784192)

> javax.mail.AuthenticationFailedException: 535 Login Fail. Please enter your authorization code to login.
>
> 邮件认证失败：需要重新设置邮件发送密码
[邮箱报错](https://blog.csdn.net/qq_41879385/article/details/104259852)  

