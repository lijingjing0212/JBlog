# 软构件与中间件 JavaEE 实验题目
## 题目1 （必做）设计实现基于 JavaEE 架构的个人博客管理系统。
### [实验目的]
使学生们熟练掌握使用 JavaEE 架构进行系统开发的全过程。
### [实验内容及要求]
#### 内容：
1. 按照教课书上步骤，使用 JDK7 + Eclipse + JBoss 7 + mysql 完成 JavaEE
   架构开发环境和运行环境的配置和搭建。
2. 个人博客管理系统的主要功能就是让用户能够在网上写日志、上传照片等功能，
   具体功能如下：  
   1) 用户注册与登录：用户注册后可以登录，如忘记密码可以找回密码，
      登陆后可以修改除用户名以外的注册资料；注册时用户名不能重复。
      密码必须是8位以上的字母和数字组合，并且在数据库中进行加密存储。
      找回密码时使用注册资料进行验证。  
   2) 整个系统分为两类用户，管理员和访客。管理员可以进行文章管理、相册管理、
      网站管理、系统信息维护等多项操作，而访客可以浏览博文信息、发表博文评论等；  
   3) 访客登录后，可以看到主页上的博客日历、最新博文、系统相关介绍、
      信息关键字搜索和友情链接等。而且还可以分类查看博文和相册里的图片，
      在查看博文的同时还可对文章进行评论。  
   4) 系统管理员的功能可分为分类管理，文章管理，相册管理、评论管理，链接管理，留言管理。
      分类管理包括文章、相册类型的添加，修改，删除。
      文章管理包括文章的修改，删除。
      相册管理、评论管理、链接管理和留言管理的功能自己定义。  

#### 技术要求：
1. 使用JSF与验证器实现用户登录与注册验证功能；
2. 使用无状态会话Bean实现用户、文章、照片等的增删改查功能的调用；
3. 使用有状态会话Bean实现对喜欢文章或者图片的收藏功能；
4. 访客可以订阅或者取消订阅管理员发送的通知，请使用消息驱动Bean通知访客订阅的消息；
5. 使用JPA技术实现对用户、文章、相册等信息存取。

## 大坑
- > ConfigurationException: The tag named xxx from namespace
    http://xmlns.jcp.org/jsf/core has a null handler-class defined

`javax.faces-2.2.1.jar` 与 `jstl-1.2.jar` 应该是 `provided` 范围的库
 
- > IJ010075: The resource adapter metadata must contain either
    an outbound or inbound configuration
    
EJB 部署的 Artifacts *必须*是 `Archive` 类型且以 `.rar` 后缀结尾，
不能是 `Exploded` 类型

- > `persistence.xml` 中使用 Hibernate 的 properties 连接数据库时，
    调用 EntityManager 的 persist 方法持久化实体成功，但不会同步到数据库中

改用 Widfly 配置的 JBoss 数据源才可正常工作。

## 进度
- 2016-08-31 看题
- 2016-09-01 搭建环境开始踩坑
- 2016-09-02 终于搭好了框架，写完实体类
- 2016-09-03 写完前台页面，写后台页面，完善实体类。
- 2016-09-04 跳整页面结构，完成登录注册，添加过滤器。分类管理。
- 2016-09-07 乱码解决，发表文章
- 2016-09-08 文章列表，编辑、删除文章，注销
- 2016-09-09 评论、文章导航、权限检查