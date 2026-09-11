# Ability Kit（程序框架服务）<!--ability-kit-->

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jayleehw-->
<!--Designer: @jayleehw-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->


- Ability Kit简介
- 应用模型<!--application-models-->
  - 应用模型概述
  - 应用组件<!--stage-model-application-components-->
    - 应用/组件级配置
    - UIAbility组件<!--uiability-->
      - UIAbility组件概述
      - UIAbility组件生命周期
      - UIAbility组件启动模式
      - UIAbility组件基本用法
      - UIAbility组件与UI的数据同步
      - 启动应用内的UIAbility组件
      - 通过Call调用实现多端协同
      - UIAbility备份恢复
    - ExtensionAbility组件
      <!--Del-->
      - 使用AgentExtensionAbility组件提供的智能体服务（仅对系统应用开放）
      - ServiceExtensionAbility（仅对系统应用开放）
      - UIServiceExtension（仅对系统应用开放）
      - UIExtensionAbility（仅对系统应用开放）
      - 使用AutoFillExtensionAbility实现自动填充功能（仅对系统应用开放）
      - 使用通过UIServiceExtensionAbility实现的系统悬浮窗
      <!--DelEnd-->
      - EmbeddedUIExtensionAbility
      - 使用AppServiceExtensionAbility组件实现后台服务
    - AbilityStage组件管理器
    - 应用上下文Context
    - 信息传递载体Want<!--want-->
      - Want概述
      - 显式Want与隐式Want匹配规则
      - 使用显式Want启动应用组件
      - 常见action与entities（不推荐使用）
    - 组件启动规则<!--component-startup-rules-->
      - 设备内组件启动规则
      <!--Del-->
      - 设备内组件启动规则（仅对系统应用开放）
      <!--DelEnd-->
      - 跨设备组件启动规则
      <!--Del-->
      - 跨设备组件启动规则（仅对系统应用开放）
      <!--DelEnd-->
    - 获取/设置环境变量
    <!--Del-->
    - 应用组件跨设备交互（流转）<!--hop-->
      - 流转概述
      - 跨端迁移
      - 多端协同
    <!--DelEnd-->  
  - 进程模型<!--process-model-stage-->
    - 进程模型概述
    - 扩展进程开发指导<!--extended-process-development-->
      - 子进程开发指导（ArkTS）
      - 子进程开发指导（C/C++）
    - 独立进程开发指导
  - 线程模型
  <!--Del-->
  - 任务（Mission）管理（仅对系统应用开放）<!--mission-management-->
    - 任务（Mission）管理场景介绍（仅对系统应用开放）
    - 任务（Mission）与启动模式（仅对系统应用开放）
    - 页面栈及任务链（仅对系统应用开放）
    - 设置任务快照的图标和名称（仅对系统应用开放）
  <!--DelEnd-->
  - 应用配置文件
- 应用生命周期<!--app-lifecycle-->
  - 应用生命周期概述
  - 应用启动<!--app-start-->
    - 应用启动流程
    - 应用启动设置
    - 应用启动框架AppStartup
    - 应用预加载
    - 应用快启
  - 应用退出<!--RP2--><!--RP2End-->
  - 应用重启
  - 获取应用异常退出原因
- 应用间跳转<!--inter-app-redirection-->
  - 应用间跳转概述
  - 拉起指定应用<!--directional-redirection-->
    - 拉起指定应用概述
    - （可选）使用canOpenLink判断应用是否可访问
    - 获取目标应用的URL信息
    - 使用Deep Linking实现应用间跳转
    - 使用App Linking实现应用间跳转
    - 显式Want跳转切换应用链接跳转适配指导
    - 应用链接说明
  - 拉起指定类型的应用<!--specified-type-app-redirection-->
    - 拉起指定类型的应用概述
    - 拉起导航类应用（startAbilityByType）
    - 拉起邮件类应用（startAbilityByType）
    - 拉起邮件类应用（mailto方式）
    - 拉起金融类应用（startAbilityByType）
    - 拉起航班类应用（startAbilityByType）
    - 拉起快递类应用（startAbilityByType）
    - 拉起图片编辑类应用（startAbilityByType）
    - 拉起文件处理类应用（startAbility）
  - 拉起系统应用<!--RP1--><!--RP1End-->
- 方舟智能开发框架开发指导<!--ark-agentic-framework-->
  - 方舟智能开发框架概述
  - 意图框架开发指导<!--insight-intent-->
    - 意图框架概述
    - 开发意图<!--insight-intent-development-->
      - 意图开发概述
      - 使用配置文件开发意图
      - 使用装饰器开发意图
      - 附录：标准意图接入规范
    - 调试意图
  - 基于ArkTS脚本的应用Skill开发指导
  - 端侧A2A框架开发指导<!--agent-guideline-->
    - 端侧A2A框架概述
    - 开发端侧智能体<!--agent-development-->
      - 使用AgentExtensionAbility组件实现智能体服务
      - AgentExtensionAbility配置文件说明
      <!--Del-->
      - 使用AgentExtensionAbility组件提供的智能体服务（仅对系统应用开放）
      <!--DelEnd-->
- 基于ModularObjectExtensionAbility的模块化对象开发指导 (C/C++)<!--modular-object-extension-ability-->
  - 模块化对象模型概述 (C/C++)
  - 使用ModularObjectExtensionAbility实现模块化对象 (C/C++)
  - 使用Taihe实现ModularObjectExtensionAbility的IPC通信 (C/C++)
  - 使用ModularObjectDispatcher实现动态接口调用 (C/C++)
- Ability Kit术语