# 架构设计、详细设计（BCE方法）到应用程序框架映射指南

### 1.逻辑架构
逻辑架构由三层模型（表示层、业务层、持久化层）构成

#### 1.1.表示层
本项目主要使用Vue开发的前端应用作为表示层，在h5移动端(PWA)和PC的Web端提供给用户一个用户账号管理系统、问卷管理中心以及任务管理中心

#### 1.2.业务层
业务层方面，服务端充当了业务层的角色，通过服务端为表示层的各个子系统提供相应的服务模块

#### 1.3.持久化层
持久化层则是使用MySQL 提供了数据的持久化服务

### 2. 框架目录设计

##### 前端src目录设计

```
src
├── App.vue
├── assets
│   └── ...
├── components
│   ├── BottomBar.vue
│   ├── GroupCard.vue
│   ├── NavBar.vue
│   ├── OptionBar.vue
│   ├── QuestionnaireCard.vue
│   ├── TaskCard.vue
│   └── loading
│       └──...
├── entry-client.js
├── entry-server.js
├── main.js
├── mixins
│   └── disabledDate.js
├── pages
│   ├── Settings
│   ├── createTask
│   ├── finish
│   ├── home
│   ├── login
│   ├── publishedQuestionnaire
│   ├── publishedTask
│   ├── questionaire
│   ├── register
│   ├── task
│   └── user
├── router
│   └── index.js
├── services
│   ├── api.js
│   ├── authService.js
│   ├── questionnaireService.js
│   └── taskService.js
├── store
|   └──...
├── sw
│   └── serviceWorker.js
└── utils
    ├── antdIcon.js
    ├── eventBus.js
    └── utils.js
```

##### 后端src目录设计

```
src
├── app.js
├── config # 服务器端口以及mysql环境的配置
│   └── config.js
├── controllers # 处理 http 请求
│   ├── authController.js
│   ├── questionnaireController.js
│   └── taskController.js
├── models # 定义模型，与数据库交互
│   ├── Participation.js
│   ├── Questionnaire.js
│   ├── Task.js
│   ├── User.js
│   └── index.js
├── policies # 检查输入的中间件
│   └── authControllerPolicy.js
├── routes.js
└── utils
    ├── timeUtils.js
    └── uploader.js
```


### 3.与 ECB 关系
* ECB中：
    * Entity：代表系统数据，如：问卷、任务等
    * Boundary：与用户的接口，如：界面、网关、代理等
    * Controller：在 Boundary 和 Entity 中衔接的媒介，编排来自 Boundary 的命令的执行
* 在本系统中，Boundary有三个部分：
    * 客户端 Vue编写的前端页面
    * 服务端 Nginx 反向代理服务器

* Controller 包含：
    * 在我们项目服务器框架目录设计中，controller 目录下，我们定义了所有的相关内容，它们通过接收来自上述 Boundary 的命令，并编排相关的操作
* Entity 包含：
    * 服务器框架目录设计中，model 目录下定义了所有服务器与 MySQL 相关的实体，承载系统数据

