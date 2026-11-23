# Ability Kit管理类概览

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @ccllee1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

Ability Kit（程序框架服务）提供了多个以“Manager”等命名的管理类模块，分别面向应用组件运行、应用包管理、启动加速、任务管理、跨端迁移、进程管理、权限隐私、智能体等不同功能领域。本文按功能层级对这些管理类接口进行归类，帮助开发者快速定位所需能力并跳转至对应的API参考。

## 应用组件与运行时管理

本类接口用于查询和管理应用组件的运行状态和进程信息。

| 模块 | 功能说明 |
| -------- | -------- |
| [abilityManager](../reference/apis-ability-kit/js-apis-app-ability-abilityManager.md) | 提供Ability信息管理功能，包括获取Ability运行状态、重启原子化服务、判断设备能力支持等。 |
| [appManager](../reference/apis-ability-kit/js-apis-app-ability-appManager.md) | 提供应用管理能力，包括查询是否为RAM受限设备、获取可用最大内存、获取运行进程信息等。 |
| [errorManager](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md) | 提供应用运行时各类异常的全局观测能力，支持监听应用崩溃（JS_CRASH）、应用冻屏（APP_FREEZE）、未捕获的Promise异常、资源使用量超过预设基线等异常场景。 |

## 应用包管理
 
本类接口用于查询应用包信息，以及管理默认应用、桌面应用（Launcher）、插件、快捷方式等。
 
| 模块 | 功能说明 |
| -------- | -------- |
| [bundleManager](../reference/apis-ability-kit/js-apis-bundleManager.md) | 提供应用信息的查询能力，支持BundleInfo、ApplicationInfo、AbilityInfo、ExtensionAbilityInfo等信息查询。 |
| [defaultAppManager](../reference/apis-ability-kit/js-apis-defaultAppManager.md) | 提供查询默认应用的能力，支持查询当前应用是否为默认应用。 |
| [launcherBundleManager](../reference/apis-ability-kit/js-apis-launcherBundleManager.md) | 提供launcher应用（桌面有图标的应用）所需的查询能力。 |
| [pluginBundleManager](../reference/apis-ability-kit/js-apis-pluginBundleManager.md) | 提供应用对自分发插件的管理能力，包括安装、卸载本地插件。 |
| [shortcutManager](../reference/apis-ability-kit/js-apis-shortcutManager.md) | 提供应用快捷方式管理能力，包括设置快捷方式是否显示等。 |
|<!--DelRow-->[bundleMonitor](../reference/apis-ability-kit/js-apis-bundleMonitor-sys.md)（系统接口） | 提供监听应用安装、卸载、更新的能力。 |
|<!--DelRow-->[bundleResourceManager](../reference/apis-ability-kit/js-apis-bundleResourceManager-sys.md)（系统接口） | 提供应用资源数据查询能力，支持BundleResourceInfo、LauncherAbilityResourceInfo等信息查询。 |
|<!--DelRow-->[distributedBundleManager](../reference/apis-ability-kit/js-apis-distributedBundleManager-sys.md)（系统接口） | 提供分布式应用的管理能力。 |

## 应用启动管理

本类接口用于管理应用的启动流程，包括启动框架任务调度、应用快启和开机自启。

| 模块 | 功能说明 |
| -------- | -------- |
| [startupManager](../reference/apis-ability-kit/js-apis-app-appstartup-startupManager.md) | 提供应用启动框架管理能力，支持启动任务依赖调度、并行执行、so预加载及任务结果管理。 |
| [hyperSnapManager](../reference/apis-ability-kit/js-apis-app-ability-hyperSnapManager.md) | 提供应用快启管理能力，包括启用或禁用快启功能、请求重新初始化快启等。 |
| [autoStartupManager](../reference/apis-ability-kit/js-apis-app-ability-autoStartupManager.md) | 提供获取自身应用开机自启状态以及检查设备是否支持开机自启动的能力。 |

## 进程与上下文管理

本类接口用于管理子进程的创建与启动，以及ArkTS并发实例间的上下文传递。

| 模块 | 功能说明 |
| -------- | -------- |
| [childProcessManager](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md) | 提供子进程管理能力，支持子进程创建和启动操作。创建的子进程会随父进程退出。 |
| [sendableContextManager](../reference/apis-ability-kit/js-apis-app-ability-sendableContextManager.md) | 提供Context与SendableContext相互转换的能力，用于ArkTS并发实例间（主线程、TaskPool工作线程、Worker工作线程）的数据传递。 |

## 方舟智能开发框架

本类接口用于端侧智能体（Agent）管理、Function（函数）调用、CLI工具交互、技能（Skill）查询和ArkTS脚本管理，支撑方舟智能开发框架。

| 模块 | 功能说明 |
| -------- | -------- |
|<!--DelRow-->[agentManager](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md)（系统接口） | 提供Agent管理能力，支持连接与断开AgentExtensionAbility、管理生命周期及获取AgentCard信息。 |
|<!--DelRow-->[functionManager](../reference/apis-ability-kit/js-apis-app-function-functionManager-sys.md)（系统接口） | 提供Function的管理和调用能力，可查询可用Function信息、调用指定Function执行业务逻辑。 |
|<!--DelRow-->[taskManager](../reference/apis-ability-kit/js-apis-app-agent-taskManager-sys.md)（系统接口） | 提供任务（Task）生命周期管理能力。任务是用户意图执行的归因单元，任务存续期间系统按任务优先级管控归因到该任务的进程。 |
| [skillManager](../reference/apis-ability-kit/js-apis-skillManager.md) | 提供技能（Skill）信息查询能力，支持查询应用自身、指定应用或所有应用的技能信息，用于AI代理任务调度。 |
| [cliManager](../reference/apis-ability-kit/js-apis-app-cli-cliManager.md) | 提供与系统命令行工具（CLI）的交互能力，可查询工具信息、执行CLI命令及管理会话。 |
| [scriptManager](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md) | 提供ArkTS脚本信息的管理与组织能力，支持应用ArkTS脚本执行结果上报。 |

<!--Del-->
## 任务管理

本类接口为系统接口，仅系统应用可调用，用于管理设备内和跨设备的任务（Mission）。

| 模块 | 功能说明 |
| -------- | -------- |
| [missionManager](../reference/apis-ability-kit/js-apis-app-ability-missionManager-sys.md)（系统接口） | 提供系统任务管理能力，包括对任务执行锁定、解锁、清理、切换到前台等操作。 |
| [distributedMissionManager](../reference/apis-ability-kit/js-apis-distributedMissionManager-sys.md)（系统接口） | 提供跨设备任务管理能力，包括注册与取消任务状态监听、同步远端任务列表、通过任务ID和包名迁移任务等。 |
<!--DelEnd-->

## 跨端迁移与流转

本类接口用于应用接续（跨端迁移）与流转/协同管理。

| 模块 | 功能说明 |
| -------- | -------- |
| [continueManager](../reference/apis-ability-kit/js-apis-app-ability-continueManager.md) | 提供应用跨端迁移的管理能力，例如，获取应用接续过程中快速拉起目标应用的结果。 |

## 权限与隐私管理

本类接口用于管理敏感权限的使用记录、URI权限授权和锁屏下的敏感数据保护。

| 模块 | 功能说明 |
| -------- | -------- |
| [screenLockFileManager](../reference/apis-ability-kit/js-apis-screenLockFileManager.md) | 提供锁屏下应用敏感数据保护能力，支持申请与释放锁屏下敏感数据访问权限以及查询敏感数据密钥状态。 |
|<!--DelRow-->[privacyManager](../reference/apis-ability-kit/js-apis-privacyManager-sys.md)（系统接口） | 提供权限使用记录等隐私管理接口，支持记录、查询、监听和控制敏感权限的使用情况。 |
|<!--DelRow-->[uriPermissionManager](../reference/apis-ability-kit/js-apis-uripermissionmanager-sys.md)（系统接口） | 提供URI权限管理能力，用于应用间授权/撤销URI权限，支持安全地共享文件访问权限。 |

## 其他能力

本类接口提供自动填充、Kiosk模式、快速修复、垂域面板和业务路由等能力。

| 模块 | 功能说明 |
| -------- | -------- |
| [autoFillManager](../reference/apis-ability-kit/js-apis-app-ability-autoFillManager.md) | 提供账号、密码、地址、电话号码等用户信息的自动填充能力。 |
| [kioskManager](../reference/apis-ability-kit/js-apis-app-ability-kioskManager.md) | 提供Kiosk模式管理能力，包括进入或退出Kiosk模式的操作。 |
|<!--DelRow-->[quickFixManager](../reference/apis-ability-kit/js-apis-app-ability-quickFixManager-sys.md)（系统接口） | 提供快速修复能力，支持通过快速下发补丁进行缺陷修复。 |
|<!--DelRow-->[verticalPanelManager](../reference/apis-ability-kit/js-apis-app-ability-verticalpanelmanager-sys.md)（系统接口） | 提供垂域面板管理能力，当前支持启动垂域应用面板选择器。 |
|<!--DelRow-->[businessAbilityRouter](../reference/apis-ability-kit/js-apis-businessAbilityRouter-sys.md)（系统接口） | 提供业务路由能力，用于查询设备上安装应用的路由Ability信息，支持标准化业务注册和跳转管控。 |
