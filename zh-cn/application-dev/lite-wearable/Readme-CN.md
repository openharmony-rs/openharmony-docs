# Lite Wearable应用开发基础

<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @huipeizi-->
<!--Designer: @huipeizi--->
<!--Tester: @huipeizi--->
<!--Adviser: @huipeizi-->


- 应用模型开发概述
- FA模型应用程序包结构
- FA模型应用配置文件<!--application-configuration-file-fa-->
    - FA模型应用配置文件概述
    - app对象内部结构
    - deviceConfig内部结构
    - module对象内部结构
- FA模型应用组件<!--fa-model-application-components-->
    - 应用/组件级配置
    - PageAbility组件开发指导<!--pageability-->
        - PageAbility组件概述
        - PageAbility组件配置
        - PageAbility的生命周期
        - PageAbility的启动模式
        - 创建PageAbility
        - 启动本地PageAbility
        - 停止PageAbility
    <!--Del-->
        - 启动远程PageAbility（仅对系统应用开放）
        <!--DelEnd-->
        - 启动指定页面
        - 窗口属性
        - 申请授权
        - 跳转规则
    - ServiceAbility组件开发指导<!--serviceability-->
        - ServiceAbility组件概述
        - ServiceAbility组件配置
        - ServiceAbility的生命周期
        - 创建ServiceAbility
        - 启动ServiceAbility
        - 连接ServiceAbility
    - DataAbility组件开发指导<!--dataability-->
        - DataAbility组件概述
        - DataAbility组件配置
        - DataAbility的生命周期
        - 创建DataAbility
        - 启动DataAbility
        - 访问DataAbility
        - DataAbility权限控制
    - FA模型的Context
    - 信息传递载体Want
    - 组件启动规则（FA模型）
- FA模型的进程模型
- FA模型的线程模型
<!--Del-->
- FA模型的任务管理（仅对系统应用开放）
<!--DelEnd-->
- FA模型的应用窗口管理
<!--Del-->
- FA模型与Stage模型应用组件互通指导<!--fa-stage-interaction-->
  - FA模型与Stage模型应用组件互通综述
  - FA模型启动Stage模型UIAbility
  - FA模型绑定Stage模型ServiceExtensionAbility
  - FA模型访问Stage模型DataShareExtensionAbility
  - Stage模型启动FA模型PageAbility
  - Stage模型绑定FA模型ServiceAbility
  - FA模型切换Stage模型指导<!--fa-to-stage-switch-->
  - 模型切换概述
  - 配置文件切换<!--configuration-file-switch-->
      - 配置文件的差异
      - app和deviceConfig的切换
      - module的切换
  - 组件切换<!--component-switch-->
      - PageAbility切换
      - ServiceAbility切换
      - DataAbility切换
  - 卡片切换
  - API切换<!--api-switch-->
      - API切换概述
      - Context接口切换
      - featureAbility接口切换
      - particleAbility接口切换
      - LifecycleForm接口切换
      - LifecycleApp接口切换
      - LifecycleService接口切换
      - LifecycleData接口切换
      - DataAbilityHelper接口切换
      - request接口切换
      - resourceManager接口切换
      - window接口切换
      - Storage接口切换
<!--DelEnd-->