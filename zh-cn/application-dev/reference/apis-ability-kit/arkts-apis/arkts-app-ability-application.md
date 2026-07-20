# @ohos.app.ability.application

开发者可以通过该模块创建[Context](docroot://application-models/application-context-stage.md)。

**起始版本：** 12

<!--Device-unnamed-declare namespace application--><!--Device-unnamed-declare namespace application-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { application } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createModuleContext](arkts-ability-application-createmodulecontext-f.md#createmodulecontext) | 创建指定模块的上下文。创建出的模块上下文中[resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md)资源继承自入参上下文，便于开发者获取[跨HAP/HSP包应用资源](docroot://quick-start/resource-categories-and-access.md#跨haphsp包应用资源)。使用Promise异步回调。 |
| [createModuleContextSync](arkts-ability-application-createmodulecontextsync-f.md#createmodulecontextsync) | 创建指定模块的上下文。创建出的模块上下文中[resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md)资源继承自入参上下文，便于开发者获取[跨HAP/HSP包应用资源](docroot://quick-start/resource-categories-and-access.md#跨haphsp包应用资源)。 |
| [createPluginModuleContext](arkts-ability-application-createpluginmodulecontext-f.md#createpluginmodulecontext) | 根据入参Context、指定的插件包名和插件模块名，创建本应用下插件的Context，用于获取插件的基本信息。使用Promise异步回调。 |
| [demoteCurrentFromCandidateMasterProcess](arkts-ability-application-demotecurrentfromcandidatemasterprocess-f.md#demotecurrentfromcandidatemasterprocess) | 撤销当前进程的备选主控进程资格。使用Promise异步回调。该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中返回801错误码。 |
| [exitMasterProcessRole](arkts-ability-application-exitmasterprocessrole-f.md#exitmasterprocessrole) | 放弃当前进程的[主控进程](docroot://application-models/ability-terminology.md#masterprocess主控进程)身份。使用Promise异步回调。该接口仅在2in1、Tablet设备中可正常调用，在其他设备中返回801错误码。 |
| [getAppPreloadType](arkts-ability-application-getapppreloadtype-f.md#getapppreloadtype) | 获取应用当前进程的预加载类型。 |
| [getApplicationContext](arkts-ability-application-getapplicationcontext-f.md#getapplicationcontext) | 获取应用上下文。开发者使用该接口时，无需依赖Context基类。重复调用该接口，将生成新的ApplicationContext对象。 |
| [getApplicationContextInstance](arkts-ability-application-getapplicationcontextinstance-f.md#getapplicationcontextinstance) | 获取应用上下文。开发者使用该接口时，无需依赖Context基类。重复调用该接口，将获取同一个ApplicationContext实例。 |
| [promoteCurrentToCandidateMasterProcess](arkts-ability-application-promotecurrenttocandidatemasterprocess-f.md#promotecurrenttocandidatemasterprocess) | 开发者可以调用该接口将当前进程放入[备选主控进程](docroot://application-models/ability-terminology.md#candidatemasterprocess备选主控进程)链表。使用Promise异步回调。当[主控进程](docroot://application-models/ability-terminology.md#masterprocess主控进程)销毁后，再次启动配置了isolationProcess为true的UIAbility/UIExtensionAbility组件时，系统会根据是否存在备选主控进程执行相应操作。  - 如果存在备选主控进程，系统会将备选主控进程链表首节点的进程设置为主控进程，触发[onNewProcessRequest](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onnewprocessrequest-1)回调。  - 如果不存在备选主控进程，系统会根据组件类型执行相应的操作。  - 对于UIAbility组件，系统将创建新的空进程作为主控进程。  - 对于UIExtensionAbility组件，系统会优先复用已有的UIExtensionAbility进程作为新的主控进程，无可用进程时则创建新的空进程作为主控进程。该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中返回801错误码。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createBundleContext](arkts-ability-application-createbundlecontext-f-sys.md#createbundlecontext) | 根据入参Context创建相应应用的Context。使用Promise异步回调。 |
| [createModuleContext](arkts-ability-application-createmodulecontext-f-sys.md#createmodulecontext-1) | 根据入参Context创建相应模块的Context。使用Promise异步回调。 |
| [createPluginModuleContextForHostBundle](arkts-ability-application-createpluginmodulecontextforhostbundle-f-sys.md#createpluginmodulecontextforhostbundle) | 根据入参Context、插件包名和插件模块名和应用包名，创建对应插件的Context，用于获取插件的基本信息。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AppPreloadType](arkts-ability-application-apppreloadtype-e.md) | 表示应用当前进程的预加载类型枚举。 |

