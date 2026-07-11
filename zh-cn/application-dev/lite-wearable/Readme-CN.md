# Lite Wearable应用开发基础

<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @huipeizi-->
<!--Designer: @huipeizi--->
<!--Tester: @huipeizi--->
<!--Adviser: @huipeizi-->


- [应用模型开发概述](../application-models/fa-model-development-overview.md)
- [FA模型应用程序包结构](../quick-start/application-package-structure-fa.md)
- FA模型应用配置文件<!--application-configuration-file-fa-->
    - [FA模型应用配置文件概述](../quick-start/application-configuration-file-overview-fa.md)
    - [app对象内部结构](../quick-start/app-structure.md)
    - [deviceConfig内部结构](../quick-start/deviceconfig-structure.md)
    - [module对象内部结构](../quick-start/module-structure.md)
- FA模型应用组件<!--fa-model-application-components-->
    - [应用/组件级配置](../application-models/application-component-configuration-fa.md)
    - PageAbility组件开发指导<!--pageability-->
        - [PageAbility组件概述](../application-models/pageability-overview.md)
        - [PageAbility组件配置](../application-models/pageability-configuration.md)
        - [PageAbility的生命周期](../application-models/pageability-lifecycle.md)
        - [PageAbility的启动模式](../application-models/pageability-launch-type.md)
        - [创建PageAbility](../application-models/create-pageability.md)
        - [启动本地PageAbility](../application-models/start-local-pageability.md)
        - [停止PageAbility](../application-models/stop-pageability.md)
    <!--Del-->
        - [启动远程PageAbility（仅对系统应用开放）](../application-models/start-remote-pageability-sys.md)
        <!--DelEnd-->
        - [启动指定页面](../application-models/start-page.md)
        - [窗口属性](../application-models/window-properties.md)
        - [申请授权](../application-models/request-permissions.md)
        - [跳转规则](../application-models/redirection-rules.md)
    - ServiceAbility组件开发指导<!--serviceability-->
        - [ServiceAbility组件概述](../application-models/serviceability-overview.md)
        - [ServiceAbility组件配置](../application-models/serviceability-configuration.md)
        - [ServiceAbility的生命周期](../application-models/serviceability-lifecycle.md)
        - [创建ServiceAbility](../application-models/create-serviceability.md)
        - [启动ServiceAbility](../application-models/start-serviceability.md)
        - [连接ServiceAbility](../application-models/connect-serviceability.md)
    - DataAbility组件开发指导<!--dataability-->
        - [DataAbility组件概述](../application-models/dataability-overview.md)
        - [DataAbility组件配置](../application-models/dataability-configuration.md)
        - [DataAbility的生命周期](../application-models/dataability-lifecycle.md)
        - [创建DataAbility](../application-models/create-dataability.md)
        - [启动DataAbility](../application-models/start-dataability.md)
        - [访问DataAbility](../application-models/access-dataability.md)
        - [DataAbility权限控制](../application-models/dataability-permission-control.md)
    - [FA模型的Context](../application-models/application-context-fa.md)
    - [信息传递载体Want](../application-models/want-fa.md)
    - [组件启动规则（FA模型）](../application-models/component-startup-rules-fa.md)
- [FA模型的进程模型](../application-models/process-model-fa.md)
- [FA模型的线程模型](../application-models/thread-model-fa.md)
<!--Del-->
- [FA模型的任务管理（仅对系统应用开放）](../application-models/mission-management-fa-sys.md)
<!--DelEnd-->
- [FA模型的应用窗口管理](../windowmanager/application-window-fa.md)
<!--Del-->
- FA模型与Stage模型应用组件互通指导<!--fa-stage-interaction-->
  - [FA模型与Stage模型应用组件互通综述](../application-models/fa-stage-interaction-overview.md)
  - [FA模型启动Stage模型UIAbility](../application-models/start-uiability-from-fa.md)
  - [FA模型绑定Stage模型ServiceExtensionAbility](../application-models/bind-serviceextensionability-from-fa.md)
  - [FA模型访问Stage模型DataShareExtensionAbility](../application-models/access-datashareextensionability-from-fa.md)
  - [Stage模型启动FA模型PageAbility](../application-models/start-pageability-from-stage.md)
  - [Stage模型绑定FA模型ServiceAbility](../application-models/bind-serviceability-from-stage.md)
  - FA模型切换Stage模型指导<!--fa-to-stage-switch-->
  - [模型切换概述](../application-models/model-switch-overview.md)
  - 配置文件切换<!--configuration-file-switch-->
      - [配置文件的差异](../application-models/configuration-file-diff.md)
      - [app和deviceConfig的切换](../application-models/app-deviceconfig-switch.md)
      - [module的切换](../application-models/module-switch.md)
  - 组件切换<!--component-switch-->
      - [PageAbility切换](../application-models/pageability-switch.md)
      - [ServiceAbility切换](../application-models/serviceability-switch.md)
      - [DataAbility切换](../application-models/dataability-switch.md)
  - [卡片切换](../application-models/widget-switch.md)
  - API切换<!--api-switch-->
      - [API切换概述](../application-models/api-switch-overview.md)
      - [Context接口切换](../application-models/context-switch.md)
      - [featureAbility接口切换](../application-models/featureability-switch.md)
      - [particleAbility接口切换](../application-models/particleability-switch.md)
      - [LifecycleForm接口切换](../application-models/lifecycleform-switch.md)
      - [LifecycleApp接口切换](../application-models/lifecycleapp-switch.md)
      - [LifecycleService接口切换](../application-models/lifecycleservice-switch.md)
      - [LifecycleData接口切换](../application-models/lifecycledata-switch.md)
      - [DataAbilityHelper接口切换](../application-models/dataabilityhelper-switch.md)
      - [request接口切换](../application-models/request-switch.md)
      - [resourceManager接口切换](../application-models/resourcemanager-switch.md)
      - [window接口切换](../application-models/window-switch.md)
      - [Storage接口切换](../application-models/storage-switch.md)
<!--DelEnd-->