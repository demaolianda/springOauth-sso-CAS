# spring-Oauth-sso
#### 1.SSO介绍

#####   	什么是SSO

​	SSO英文全称Single Sign On，单点登录。SSO是在多个应用系统中，用户只需要登录一次就可以访问所有相互信任的应用系统。它包括可以将这次主要的登录映射到其他应用中用于同一个用户的登录的机制。它是目前比较流行的企业业务整合的解决方案之一。

​	简单来说，SSO出现的目的在于解决同一产品体系中，多应用共享用户session的需求。SSO通过将用户登录信息映射到浏览器cookie中，解决其它应用免登获取用户session的问题。

##### 	为什么需要SSO

​	开放平台业务本身不需要SSO，但是如果平台的普通用户也可以在申请后成为一个应用开发者，那么就需要将平台加入到公司的整体账号体系中去，另外，对于企业级场景来说，一般都会有SSO系统，充当统一的账号校验入口。

##### 	CAS协议中概念介绍

​	SSO单点登录只是一个方案，而目前市面上最流行的单端登录系统是由耶鲁大学开发的CAS系统，而由其实现的CAS协议，也成为目前SSO协议中的既定协议，下文中的单点登录协议及结构，均为CAS中的体现结构
CAS协议中有以下几个概念：
1.CAS Client：需要集成单点登录的应用，称为单点登录客户端
2.CAS Server：单点登录服务器，用户登录鉴权、凭证下发及校验等操作
3.TGT：ticker granting ticket，用户凭证票据，用以标记用户凭证，用户在单点登录系统中登录一次后，再其有效期内，TGT即代表用户凭证，用户在其它client中无需再进行二次登录操作，即可共享单点登录系统中的已登录用户信息
4.ST：service ticket，服务票据，服务可以理解为客户端应用的一个业务模块，体现为客户端回调url，CAS用以进行服务权限校验，即CAS可以对接入的客户端进行管控
5.TGC：ticket granting cookie，存储用户票据的cookie，即用户登录凭证最终映射的cookies

![](https://img2018.cnblogs.com/blog/1373932/201905/1373932-20190504102528208-1014155182.gif)



#### 2.接口测试

```java
首先启动server项目,在先后启动client1和client2不然会报找不到认证服务器异常:
访问URL:
http://127.0.0.1:8060/client2/index.html
此时会进行认证服务器的登录校验,用户名随便填写,密码我这里固定设置为123456
跳转后点击访问client2即可访问client2的相关内容,至此完成Sso不同应用间单点登录的功能
```

#### 3.代码相关

​	这里有很多人会报JWT找不到的错误,这个问题我之前也遇到过,具体可以查看相关的依赖配置,注意pom包的引入应该都是SpringBoot的,而不是SpringCloud的包,这个之前是因为包的问题引入错误导致的,至于其他原因的产生可以试着运行下本人的代码并进行对照查看,有什么问题可以留言给我,**欢迎点星支持和交流!**

#### 4.项目git地址

<font color=#68228B  size=3>(喜欢记得点星支持哦,谢谢!)</font> 

<font color=#EEB422   size=4>https://github.com/fengcharly/springOauth-sso-CAS</font>



