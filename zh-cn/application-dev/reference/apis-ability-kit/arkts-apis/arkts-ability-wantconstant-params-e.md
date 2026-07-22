# Params

want的Params操作的常量。

**起始版本：** 9

<!--Device-wantConstant-export enum Params--><!--Device-wantConstant-export enum Params-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## ABILITY_BACK_TO_OTHER_MISSION_STACK

```TypeScript
ABILITY_BACK_TO_OTHER_MISSION_STACK = 'ability.params.backToOtherMissionStack'
```

表示是否支持跨任务链返回。

该参数用于控制跨应用的UIAbility返回逻辑，其核心作用是改变用户执行返回键时的应用跳转行为。例如现有UIAbility A和UIAbility B，当前前台显示的是UIAbility A，随后系统服务又拉起UIAbility B（同时在Want的Params字段配置该参数为true），那么，当UIAbility B退出时，会返回到UIAbility A（即返回到最近一次的访问任务）。如果未配置该参数，则默认直接返回桌面。需要注意的是，该字段仅支持系统设置，三方应用传入该字段不生效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Params-ABILITY_BACK_TO_OTHER_MISSION_STACK = 'ability.params.backToOtherMissionStack'--><!--Device-Params-ABILITY_BACK_TO_OTHER_MISSION_STACK = 'ability.params.backToOtherMissionStack'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## ABILITY_RECOVERY_RESTART

```TypeScript
ABILITY_RECOVERY_RESTART = 'ohos.ability.params.abilityRecoveryRestart'
```

表示当前Ability是否发生了故障恢复重启。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Params-ABILITY_RECOVERY_RESTART = 'ohos.ability.params.abilityRecoveryRestart'--><!--Device-Params-ABILITY_RECOVERY_RESTART = 'ohos.ability.params.abilityRecoveryRestart'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## CONTENT_TITLE_KEY

```TypeScript
CONTENT_TITLE_KEY = 'ohos.extra.param.key.contentTitle'
```

表示原子化服务分享的标题。

在跨端分享的[onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare)回调中，开发者可通过该字段设置分享的标题。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Params-CONTENT_TITLE_KEY = 'ohos.extra.param.key.contentTitle'--><!--Device-Params-CONTENT_TITLE_KEY = 'ohos.extra.param.key.contentTitle'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## SHARE_ABSTRACT_KEY

```TypeScript
SHARE_ABSTRACT_KEY = 'ohos.extra.param.key.shareAbstract'
```

表示原子化服务分享的内容摘要。

在跨端分享的[onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare)回调中，开发者可通过该字段设置分享的摘要。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Params-SHARE_ABSTRACT_KEY = 'ohos.extra.param.key.shareAbstract'--><!--Device-Params-SHARE_ABSTRACT_KEY = 'ohos.extra.param.key.shareAbstract'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## SHARE_URL_KEY

```TypeScript
SHARE_URL_KEY = 'ohos.extra.param.key.shareUrl'
```

表示原子化服务分享的URL链接。

在跨端分享的[onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare)回调中，开发者可通过该字段设置分享的URL链接。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Params-SHARE_URL_KEY = 'ohos.extra.param.key.shareUrl'--><!--Device-Params-SHARE_URL_KEY = 'ohos.extra.param.key.shareUrl'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## SUPPORT_CONTINUE_PAGE_STACK_KEY

```TypeScript
SUPPORT_CONTINUE_PAGE_STACK_KEY = 'ohos.extra.param.key.supportContinuePageStack'
```

表示在跨端迁移过程中是否迁移页面栈信息。默认值为true，表示在跨端迁移过程中自动迁移页面栈信息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Params-SUPPORT_CONTINUE_PAGE_STACK_KEY = 'ohos.extra.param.key.supportContinuePageStack'--><!--Device-Params-SUPPORT_CONTINUE_PAGE_STACK_KEY = 'ohos.extra.param.key.supportContinuePageStack'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## SUPPORT_CONTINUE_SOURCE_EXIT_KEY

```TypeScript
SUPPORT_CONTINUE_SOURCE_EXIT_KEY = 'ohos.extra.param.key.supportContinueSourceExit'
```

表示跨端迁移源端应用是否退出。默认值为true，表示在跨端迁移过程中源端应用自动退出。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Params-SUPPORT_CONTINUE_SOURCE_EXIT_KEY = 'ohos.extra.param.key.supportContinueSourceExit'--><!--Device-Params-SUPPORT_CONTINUE_SOURCE_EXIT_KEY = 'ohos.extra.param.key.supportContinueSourceExit'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## SHOW_MODE_KEY

```TypeScript
SHOW_MODE_KEY = 'ohos.extra.param.key.showMode'
```

表示[EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md)的显示模式，值为枚举类型[ShowMode](arkts-ability-wantconstant-showmode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-SHOW_MODE_KEY = 'ohos.extra.param.key.showMode'--><!--Device-Params-SHOW_MODE_KEY = 'ohos.extra.param.key.showMode'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## PARAMS_STREAM

```TypeScript
PARAMS_STREAM = 'ability.params.stream'
```

表示授权给目标方的文件URI列表。对应的value必须是string类型的文件URI数组。文件URI的获取参考[fileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#geturifrompath)。该字段需要与文件URI读写[Flags](arkts-ability-wantconstant-flags-e.md)配合使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-PARAMS_STREAM = 'ability.params.stream'--><!--Device-Params-PARAMS_STREAM = 'ability.params.stream'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## APP_CLONE_INDEX_KEY

```TypeScript
APP_CLONE_INDEX_KEY = 'ohos.extra.param.key.appCloneIndex'
```

表示分身应用索引。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-APP_CLONE_INDEX_KEY = 'ohos.extra.param.key.appCloneIndex'--><!--Device-Params-APP_CLONE_INDEX_KEY = 'ohos.extra.param.key.appCloneIndex'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## CALLER_REQUEST_CODE

```TypeScript
CALLER_REQUEST_CODE = 'ohos.extra.param.key.callerRequestCode'
```

表示应用拉起的请求码。

当调用[startAbilityForResult](arkts-ability-uiabilitycontext-c.md#startabilityforresult)或[openLink](arkts-ability-uiabilitycontext-c.md#openlink)拉起目标方Ability时，需要目标方返回结果。为了确保目标方能够将结果准确返回到调用方，系统会自动生成唯一的requestCode，以标识本次调用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-CALLER_REQUEST_CODE = 'ohos.extra.param.key.callerRequestCode'--><!--Device-Params-CALLER_REQUEST_CODE = 'ohos.extra.param.key.callerRequestCode'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## PAGE_PATH

```TypeScript
PAGE_PATH = 'ohos.param.atomicservice.pagePath'
```

表示原子化服务的页面路径。

如果原子化服务的页面跳转是通过[router](../../../ui/arkts-routing.md)实现的，可以使用该参数指定跳转的页面，例如"library/ets/pages/menu"。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-PAGE_PATH = 'ohos.param.atomicservice.pagePath'--><!--Device-Params-PAGE_PATH = 'ohos.param.atomicservice.pagePath'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## ROUTER_NAME

```TypeScript
ROUTER_NAME = 'ohos.param.atomicservice.routerName'
```

表示原子化服务的页面路由名称，即进行页面跳转时指定的页面名称。

如果原子化服务的页面跳转是通过[Navigation](../../../ui/arkts-navigation-architecture.md)实现的，可以通过ROUTER_NAME、PAGE_SOURCE_FILE及BUILD_FUNCTION联合使用指定跳转的页面。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-ROUTER_NAME = 'ohos.param.atomicservice.routerName'--><!--Device-Params-ROUTER_NAME = 'ohos.param.atomicservice.routerName'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## PAGE_SOURCE_FILE

```TypeScript
PAGE_SOURCE_FILE = 'ohos.param.atomicservice.pageSourceFile'
```

表示原子化服务的页面源文件。

如果原子化服务的页面跳转是通过[Navigation](../../../ui/arkts-navigation-architecture.md)实现的，可以通过ROUTER_NAME、PAGE_SOURCE_FILE及BUILD_FUNCTION联合使用指定跳转的页面。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-PAGE_SOURCE_FILE = 'ohos.param.atomicservice.pageSourceFile'--><!--Device-Params-PAGE_SOURCE_FILE = 'ohos.param.atomicservice.pageSourceFile'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## BUILD_FUNCTION

```TypeScript
BUILD_FUNCTION = 'ohos.param.atomicservice.buildFunction'
```

表示原子化服务的生成函数。

如果原子化服务的页面跳转是通过[Navigation](../../../ui/arkts-navigation-architecture.md)实现的，可以通过ROUTER_NAME、PAGE_SOURCE_FILE及BUILD_FUNCTION联合使用指定跳转的页面。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-BUILD_FUNCTION = 'ohos.param.atomicservice.buildFunction'--><!--Device-Params-BUILD_FUNCTION = 'ohos.param.atomicservice.buildFunction'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## SUB_PACKAGE_NAME

```TypeScript
SUB_PACKAGE_NAME = 'ohos.param.atomicservice.subpackageName'
```

表示原子化服务的分包名。应用程序包支持多模块开发，每个应用程序包可能包含多个HAP或HSP。原子化服务为了实现快速启动效果，对HAP和HSP文件大小做了限制，并同时优化了启动机制，原子化服务的这种多模块开发方式称为“分包”。

打开原子化服务的时候，可以通过设置该参数拉起对应的分包。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Params-SUB_PACKAGE_NAME = 'ohos.param.atomicservice.subpackageName'--><!--Device-Params-SUB_PACKAGE_NAME = 'ohos.param.atomicservice.subpackageName'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## APP_INSTANCE_KEY

```TypeScript
APP_INSTANCE_KEY = 'ohos.extra.param.key.appInstance'
```

表示具体的应用实例。

在[应用创建多实例](../../../quick-start/multiInstance.md)时，系统会为每个实例分配唯一的标识。应用跳转时，开发者可以通过设置该参数指定希望跳转到的已创建的应用实例。

**起始版本：** 14

<!--Device-Params-APP_INSTANCE_KEY = 'ohos.extra.param.key.appInstance'--><!--Device-Params-APP_INSTANCE_KEY = 'ohos.extra.param.key.appInstance'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## CREATE_APP_INSTANCE_KEY

```TypeScript
CREATE_APP_INSTANCE_KEY = 'ohos.extra.param.key.createAppInstance'
```

表示是否创建新应用实例。默认为false，表示不创建新应用实例。

开发者可以通过设置该参数为true拉起新的应用实例。需要注意的是，被拉起的应用需要支持多实例，参考[应用创建多实例](../../../quick-start/multiInstance.md)。

**起始版本：** 14

<!--Device-Params-CREATE_APP_INSTANCE_KEY = 'ohos.extra.param.key.createAppInstance'--><!--Device-Params-CREATE_APP_INSTANCE_KEY = 'ohos.extra.param.key.createAppInstance'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## CALLER_APP_CLONE_INDEX

```TypeScript
CALLER_APP_CLONE_INDEX = 'ohos.param.callerAppCloneIndex'
```

表示拉起方应用的分身索引。

**起始版本：** 14

<!--Device-Params-CALLER_APP_CLONE_INDEX = 'ohos.param.callerAppCloneIndex'--><!--Device-Params-CALLER_APP_CLONE_INDEX = 'ohos.param.callerAppCloneIndex'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## DESTINATION_PLUGIN_ABILITY

```TypeScript
DESTINATION_PLUGIN_ABILITY = 'ohos.params.pluginAbility'
```

指示目标Ability是插件Ability。

**起始版本：** 19

<!--Device-Params-DESTINATION_PLUGIN_ABILITY = 'ohos.params.pluginAbility'--><!--Device-Params-DESTINATION_PLUGIN_ABILITY = 'ohos.params.pluginAbility'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## APP_LAUNCH_TRUSTLIST

```TypeScript
APP_LAUNCH_TRUSTLIST = 'ohos.params.appLaunchTrustList'
```

表示隐式启动时的应用过滤列表。

隐式启动时仅匹配列表中的应用，值为string类型的[AppIdentifier](./bundleManager/BundleInfo:BundleInfo.AppIdentifier)数组，过滤列表最多支持50个应用，传入空数组不生效。

**起始版本：** 17

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-Params-APP_LAUNCH_TRUSTLIST = 'ohos.params.appLaunchTrustList'--><!--Device-Params-APP_LAUNCH_TRUSTLIST = 'ohos.params.appLaunchTrustList'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## ATOMIC_SERVICE_SHARE_ROUTER

```TypeScript
ATOMIC_SERVICE_SHARE_ROUTER = 'ohos.params.atomicservice.shareRouter'
```

表示被拉起的原子化服务的页面栈信息。仅当拉起方为UIAbilityContext，被拉起方为原子化服务时生效。

例如，某原子化服务中包含首页和第2页，如果希望直接拉起原子化服务的第2页，可以在拉起原子化服务时通过该字段传递第2页的页面栈信息。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Params-ATOMIC_SERVICE_SHARE_ROUTER = 'ohos.params.atomicservice.shareRouter'--><!--Device-Params-ATOMIC_SERVICE_SHARE_ROUTER = 'ohos.params.atomicservice.shareRouter'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## LAUNCH_REASON_MESSAGE

```TypeScript
LAUNCH_REASON_MESSAGE = 'ohos.params.launchReasonMessage'
```

表示应用拉起的原因。

调用方必须为系统应用，且需要申请ohos.permission.SET_LAUNCH_REASON_MESSAGE权限。当前取值支持：

"ReasonMessage_SystemShare"：表示系统分享拉起。

"ReasonMessage_DesktopShortcut"：表示桌面快捷方式拉起。

"ReasonMessage_Notification"：表示通知拉起。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Params-LAUNCH_REASON_MESSAGE = 'ohos.params.launchReasonMessage'--><!--Device-Params-LAUNCH_REASON_MESSAGE = 'ohos.params.launchReasonMessage'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## ABILITY_UNIFIED_DATA_KEY

```TypeScript
ABILITY_UNIFIED_DATA_KEY = 'ohos.param.ability.udKey'
```

表示基于[UDMF](../../apis-arkdata/arkts-apis/arkts-data-unifieddatachannel.md)进行文件分享时使用的唯一标识。该字段只允许系统应用设置，三方应用可以读取。

当Want中存在URI授权Flag字段（即[FLAG_AUTH_READ_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md)或[FLAG_AUTH_WRITE_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md)），且同时存在PARAMS_STREAM字段时，该字段将不生效。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Params-ABILITY_UNIFIED_DATA_KEY = 'ohos.param.ability.udKey'--><!--Device-Params-ABILITY_UNIFIED_DATA_KEY = 'ohos.param.ability.udKey'-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

