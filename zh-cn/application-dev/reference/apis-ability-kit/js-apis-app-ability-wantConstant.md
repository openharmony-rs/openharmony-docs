# @ohos.app.ability.wantConstant (Want常量)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->


wantConstant模块提供了[Want](js-apis-app-ability-want.md)操作相关的系统预设枚举和常量，例如在启动Ability（应用组件）时常用的Flag、Param参数等。这些预置常量定义了系统支持的标准化参数名称和标志位，开发者在进行应用跳转、跨端迁移、原子化服务启动等场景中，可以使用这些常量来设置Want对象的参数字段，确保参数名称的规范性和一致性。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { wantConstant } from '@kit.AbilityKit';
```

## Params

[Want.parameters](js-apis-app-ability-want.md#want)字段常用的系统预置关键字。开发者可以通过这些预置关键字设置或获取应用跳转等场景中额外携带的参数信息。例如在[UIAbility](js-apis-app-ability-uiAbility.md)的启动阶段，如果从onCreate回调的入参want字段中获取到ABILITY_RECOVERY_RESTART的值为true，则表示当前UIAbility发生了故障重启。

**系统能力**：SystemCapability.Ability.AbilityBase

| 名称                    | 值                                 | 说明                                                                           |
| ----------------------- | ---------------------------------- | ------------------------------------------------------------------------------ |
| ABILITY_BACK_TO_OTHER_MISSION_STACK   | ability.params.backToOtherMissionStack     | 表示是否支持跨任务链返回。<br>该参数用于控制跨应用的UIAbility返回逻辑，其核心作用是改变用户执行返回键时的应用跳转行为。例如现有UIAbility A和UIAbility B，当前前台显示的是UIAbility A，随后系统服务又拉起UIAbility B（同时在Want的Params字段配置该参数为true），那么，当UIAbility B退出时，会返回到UIAbility A（即返回到最近一次的访问任务）。如果未配置该参数，则默认直接返回桌面。需要注意的是，该字段仅支持系统设置，三方应用传入该字段不生效。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。  |
| ABILITY_RECOVERY_RESTART<sup>10+</sup> | ohos.ability.params.abilityRecoveryRestart | 表示当前Ability是否发生了故障恢复重启。故障恢复重启是指在Ability因异常崩溃等原因自动重启后，系统设置该参数为true，开发者可在onCreate回调中检查该参数判断是否为故障恢复场景。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| CONTENT_TITLE_KEY<sup>10+</sup>       | ohos.extra.param.key.contentTitle  | 表示原子化服务分享的标题。<br>在跨端分享的[onShare](js-apis-app-ability-uiAbility.md#onshare10)回调中，开发者可通过该字段设置分享的标题。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。  |
| SHARE_ABSTRACT_KEY<sup>10+</sup>      | ohos.extra.param.key.shareAbstract | 表示原子化服务分享的内容摘要。<br>在跨端分享的[onShare](js-apis-app-ability-uiAbility.md#onshare10)回调中，开发者可通过该字段设置分享的摘要。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。  |
| SHARE_URL_KEY<sup>10+</sup>           | ohos.extra.param.key.shareUrl      | 表示原子化服务分享的URL链接。<br>在跨端分享的[onShare](js-apis-app-ability-uiAbility.md#onshare10)回调中，开发者可通过该字段设置分享的URL链接。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。  |
| SUPPORT_CONTINUE_PAGE_STACK_KEY<sup>10+</sup>    | ohos.extra.param.key.supportContinuePageStack  | 表示在跨端迁移过程中是否迁移页面栈信息。默认值为true，表示在跨端迁移过程中自动迁移页面栈信息。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。|
| SUPPORT_CONTINUE_SOURCE_EXIT_KEY<sup>10+</sup>  | ohos.extra.param.key.supportContinueSourceExit      | 表示跨端迁移源端应用是否退出。默认值为true，表示在跨端迁移过程中源端应用自动退出。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。|
| SHOW_MODE_KEY<sup>12+</sup>  | ohos.extra.param.key.showMode      | 表示[EmbeddableUIAbility](js-apis-app-ability-embeddableUIAbility.md)的显示模式，值为枚举类型[ShowMode](#showmode12)。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。|
| PARAMS_STREAM<sup>12+</sup>  | ability.params.stream  | 表示授权给目标方的文件URI列表。对应的value必须是string类型的文件URI数组。文件URI的获取参考[fileUri](../apis-core-file-kit/js-apis-file-fileuri.md)格式规范。该字段需要与文件URI读写[Flags](#flags)配合使用。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。 |
| APP_CLONE_INDEX_KEY<sup>12+</sup>  | ohos.extra.param.key.appCloneIndex  | 表示分身应用索引。分身应用是指同一应用的多个独立实例，系统为每个实例分配唯一的索引值，用于区分不同的应用实例。在应用跳转场景中，开发者可通过设置该参数指定目标分身应用。索引值的获取方式请参考[分身应用开发指导](../../application-models/app-clone.md)。 <br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。 |
| CALLER_REQUEST_CODE<sup>12+</sup>  | ohos.extra.param.key.callerRequestCode  | 表示应用拉起的请求码。<br>当调用[startAbilityForResult](js-apis-inner-application-uiAbilityContext.md#startabilityforresult)或[openLink](js-apis-inner-application-uiAbilityContext.md#openlink12)拉起目标方Ability时，需要目标方返回结果。为了确保目标方能够将结果准确返回到调用方，系统会自动生成唯一的requestCode，以标识本次调用。 <br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。 |
| PAGE_PATH<sup>12+</sup>  | ohos.param.atomicservice.pagePath | 表示原子化服务的页面路径。<br>如果原子化服务的页面跳转是通过[router](../../ui/arkts-routing.md)实现的，可以使用该参数指定跳转的页面，例如"library/ets/pages/menu"。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。  |
| ROUTER_NAME<sup>12+</sup>  | ohos.param.atomicservice.routerName | 表示原子化服务的页面路由名称，即进行页面跳转时指定的页面名称。<br>如果原子化服务的页面跳转是通过[Navigation](../../ui/arkts-navigation-architecture.md)实现的，可以通过ROUTER_NAME、PAGE_SOURCE_FILE及BUILD_FUNCTION联合使用指定跳转的页面。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。  |
| PAGE_SOURCE_FILE<sup>12+</sup>  | ohos.param.atomicservice.pageSourceFile | 表示原子化服务的页面源文件。<br>如果原子化服务的页面跳转是通过[Navigation](../../ui/arkts-navigation-architecture.md)实现的，可以通过ROUTER_NAME、PAGE_SOURCE_FILE及BUILD_FUNCTION联合使用指定跳转的页面。其中ROUTER_NAME为路由名称，PAGE_SOURCE_FILE为页面源文件路径，BUILD_FUNCTION为页面构建函数名，三个参数需要一一对应。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。  |
| BUILD_FUNCTION<sup>12+</sup>  | ohos.param.atomicservice.buildFunction | 表示原子化服务的生成函数。<br>如果原子化服务的页面跳转是通过[Navigation](../../ui/arkts-navigation-architecture.md)实现的，可以通过ROUTER_NAME、PAGE_SOURCE_FILE及BUILD_FUNCTION联合使用指定跳转的页面。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。  |
| SUB_PACKAGE_NAME<sup>12+</sup>  | ohos.param.atomicservice.subpackageName | 表示原子化服务的分包名。应用程序包支持多模块开发，每个应用程序包可能包含多个HAP或HSP。原子化服务为了实现快速启动效果，对HAP（Harmony Ability Package）和HSP（Harmony Shared Package）文件大小做了限制，并同时优化了启动机制，原子化服务的这种多模块开发方式称为“分包”。<br>打开原子化服务的时候，可以通过设置该参数拉起对应的分包。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。  |
| APP_INSTANCE_KEY<sup>14+</sup>  | ohos.extra.param.key.appInstance  | 表示具体的应用实例。<br>在[应用创建多实例](../../quick-start/multiInstance.md)时，系统会为每个实例分配唯一的标识。应用跳转时，开发者可以通过设置该参数指定希望跳转到的已创建的应用实例。需要注意的是，被拉起的应用需要支持多实例，且指定的实例需已创建，参考[应用创建多实例](../../quick-start/multiInstance.md)。 |
| CREATE_APP_INSTANCE_KEY<sup>14+</sup>  | ohos.extra.param.key.createAppInstance  | 表示是否创建新应用实例。默认为false，表示不创建新应用实例。<br>开发者可以通过设置该参数为true拉起新的应用实例。需要注意的是，被拉起的应用需要支持多实例，参考[应用创建多实例](../../quick-start/multiInstance.md)。 |
| CALLER_APP_CLONE_INDEX<sup>14+</sup>  | ohos.param.callerAppCloneIndex  | 表示拉起方应用的分身索引。应用跳转时，系统通过该字段标识调用方的分身身份，以便目标应用能够识别来源。该字段通常由系统自动设置，开发者一般无需手动配置。|
| APP_LAUNCH_TRUSTLIST<sup>17+</sup>  | ohos.params.appLaunchTrustList  | 表示隐式启动时的应用过滤列表。<br>隐式启动时仅匹配列表中的应用，值为string类型的[AppIdentifier](js-apis-bundleManager-bundleInfo.md#signatureinfo)数组，过滤列表最多支持50个应用。传入空数组不生效。传入超过50个应用时，系统将抛出异常（或自动截断为前50个，或返回错误码XX，需根据实际行为补充）。<br>**原子化服务API**：从API version 17开始，该接口支持在原子化服务中使用。 |
| LAUNCH_REASON_MESSAGE<sup>18+</sup>  | ohos.params.launchReasonMessage  | 表示应用拉起的原因。<br>调用方必须为系统应用，且需要申请ohos.permission.SET_LAUNCH_REASON_MESSAGE权限，三方应用传入该字段不生效。当前取值支持：<br>"ReasonMessage_SystemShare"：表示系统分享拉起。<br>"ReasonMessage_DesktopShortcut"：表示桌面快捷方式拉起。<br>"ReasonMessage_Notification"：表示通知拉起。<br>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。 |
| DESTINATION_PLUGIN_ABILITY<sup>19+</sup>  | ohos.params.pluginAbility  | 表示目标Ability是插件Ability，设置该Flag后，系统将目标Ability识别为插件Ability，并以插件模式进行拉起。在拉起插件Ability时，开发者需要在Want中将该字段设置为true，以此标识目标Ability的类型。插件Ability具备专属的生命周期与运行模式，和普通Ability存在区别，其详细使用说明请参考[插件化开发指导](../../application-models/plugin-ability.md)。<br>**原子化服务API**：从API version 19开始，该接口支持在原子化服务中使用。 |
ATOMIC_SERVICE_SHARE_ROUTER<sup>20+</sup> | ohos.params.atomicservice.shareRouter | 表示被拉起的原子化服务的页面栈信息，用于指定跳转的目标页面。值为string类型的页面栈信息，开发者可以通过[UIAbilityContext](js-apis-inner-application-uiAbilityContext.md)获取当前页面栈信息并传递。仅当拉起方为UIAbilityContext，被拉起方为原子化服务时生效。<br>例如，某原子化服务中包含首页和第2页，如果希望直接拉起原子化服务的第2页，可以在拉起原子化服务时通过该字段传递第2页的页面栈信息。<br>**说明**：从API version 26.0.0开始，如果拉起方具有ohos.permission.START_ABILITY_TO_PAGE权限，目标方不是原子化服务也能生效。<br>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。 |
| ABILITY_UNIFIED_DATA_KEY<sup>20+</sup>  | ohos.param.ability.udKey  | 表示基于[unifiedDataChannel](../apis-arkdata/js-apis-data-unifiedDataChannel.md)进行文件分享时使用的唯一标识。该字段只允许系统应用设置，三方应用可以读取。<br>当Want中存在URI授权Flag字段（即[FLAG_AUTH_READ_URI_PERMISSION](#flags)或[FLAG_AUTH_WRITE_URI_PERMISSION](#flags)），且同时存在PARAMS_STREAM字段时，该字段将不生效。 <br>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。|

## Flags

[Want.flags](js-apis-app-ability-want.md#want)字段常用的系统预置关键字。开发者可以通过这些预置关键字设置或获取应用跳转等场景中额外携带的标志位信息。

**系统能力**：SystemCapability.Ability.AbilityBase

| 名称                                 | 值       | 说明                                                         |
| ------------------------------------ | ---------- | ------------------------------------------------------------ |
| FLAG_AUTH_READ_URI_PERMISSION        | 0x00000001 | 表示临时授予接收方读取该URI指向的数据的权限。该权限仅在接收方应用运行期间有效，且仅限于读取URI指定的数据。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。                                  |
| FLAG_AUTH_WRITE_URI_PERMISSION       | 0x00000002 | 表示临时授予接收方写入该URI指向的数据的权限。该权限仅在接收方应用运行期间有效，且仅限于写入URI指定的数据。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。                                  |
| FLAG_AUTH_PERSISTABLE_URI_PERMISSION<sup>12+</sup> | 0x00000040 | 表示该URI可被接收方持久化。接收方可以通过[fileShare.persistPermission](../apis-core-file-kit/js-apis-fileShare.md#filesharepersistpermission11)接口进行权限持久化。|
| FLAG_INSTALL_ON_DEMAND               | 0x00000800 | 表示拉起原子化服务时开启免安装功能。<br>- 如果开启了免安装功能，当系统检测到被拉起的原子化服务未安装时，会自动安装原子化服务，再进行拉起。<br>- 如果未开启免安装功能，当原子化服务未安装时，将拉起失败。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。                              |
| FLAG_START_WITHOUT_TIPS<sup>11+</sup>              | 0x40000000 | 表示是否关闭匹配失败弹窗功能。设置此标志位时关闭弹窗，不设置时保持默认弹窗行为。<br>通过[隐式方式拉起应用](../../application-models/app-startup-overview.md)时，如果没有能够匹配的应用，默认会弹出提示弹窗“暂无可用打开方式”。开发者可以通过该字段屏蔽该弹窗。       |
| FLAG_ABILITY_ON_COLLABORATE<sup>18+</sup> | 0x00002000 | 在多设备协同场景下，调用方应用通过DMS系统发起请求并且在Flags中设置此标志位时，协同方应用才会触发生命周期回调方法[onCollaborate()](js-apis-app-ability-uiAbility.md#oncollaborate18)。 |

## ShowMode<sup>12+</sup>

表示[EmbeddableUIAbility](js-apis-app-ability-embeddableUIAbility.md)被拉起时的显示模式。

**系统能力**：SystemCapability.Ability.AbilityBase

| 名称                                | 值 | 说明           |
| ----------------------------------- |---|--------------|
| WINDOW        | 0 | 表示独立窗口拉起模式。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。  |
| EMBEDDED_FULL       | 1 | 表示嵌入式全屏拉起模式。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。 |
| EMBEDDED_HALF<sup>23+</sup>       | 2 | 表示嵌入式半屏拉起模式。<br>**模型约束：** 此接口仅可在Stage模型下使用。<br>**原子化服务API**：从API version 23开始，该接口支持在原子化服务中使用。 |

## Action

表示要执行的通用操作。

**起始版本：** 26.0.0

**系统能力**：SystemCapability.Ability.AbilityBase

| 名称                                | 值 | 说明           |
| ----------------------------------- |---|--------------|
| ACTION_SEND_TO_DATA        | ohos.want.action.sendToData | 指示启动向指定接收方发送消息界面的操作。  |
