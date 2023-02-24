# simple-douyin
## Introduction

**基于Kitex + Hertz 框架的简易版douyin/TikTok服务端，具有视频推送、视频上传、点赞、评论、关注等基础功能。**

| 编程语言     | Golang         | 1.18.1    |
| ------------ | -------------- | --------- |
| 微服务框架   | Kitex          | 0.4.4     |
| HTTP框架     | Hertz          | 0.5.2     |
| 数据库       | MySQL          | 5.7.41    |
| ORM框架      | Gorm           | 1.20.0    |
| 其他组件     | ffmpeg         | 4.2.4     |
| 对象储存系统 | MinIO          | 2023.2.10 |
| 部署工具     | Docker         | 23.0.0    |
|              | Docker Compose | 2.4.1     |
|              | Kubernetes     | 1.22.3    |
| 测试工具     | Apifox         | 2.2.24    |

1. 视频储存采用分布式对象储存系统MinIO，使用Docker-Compose进行容器集群部署，提升服务性能
2. 使用Kubernetes对运行微服务的Docker镜像进行部署，保障服务高可用
3. 使用Gorm事务操作，保障服务高可靠性      

**代码目录结构**

| **目录**      | **子目录** | **说明**                   |
| ------------- | ---------- | -------------------------- |
| **cmd**       | api        | 初始化Hertz框架            |
|               | user       | 作为客户端调用相应服务     |
|               | feed       |                            |
|               | favorite   |                            |
|               | publish    |                            |
|               | relation   |                            |
| **conf**      |            | 配置文件                   |
| **idl**       |            | thrift接口定义文件         |
| **dal**       | mysql      | 数据库初始化操作，业务逻辑 |
| **kitex_gen** |            | Kitex 自动生成的代码       |
| **pkg**       | jwt        | 登录鉴权组件               |
|               | md5        | 数据加密组件               |

## Unit Strcture

和javaee中的三层架构相似<BR>

|  javaee  |     go     |
|:--------:|:----------:|
|   WEB层   |  handler   |
| service层 | service文件夹 |
|   dal层   |   dal文件夹   |
