# @ohos.app.ability.wantConstant (Want Constants)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=acba00b4edca6db1d20615b479cf478c7de4ec19 translatedAt=2026-09-03T10:41:36.429Z pushedAt=2026-09-05T10:47:30.464Z -->


The wantConstant module provides the system preset enums and constants related to [Want](js-apis-app-ability-want.md) operations, such as the commonly used Flag and Param parameters when starting an Ability (application component). These preset constants define the standardized parameter names and flag bits supported by the system. Developers can use these constants to set the parameter fields of a Want object in scenarios such as application redirection, cross-device migration, and atomic service startup, ensuring the standardization and consistency of parameter names.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { wantConstant } from '@kit.AbilityKit';
```

## Params

Enumerates the common system-defined keywords for the [Want.parameters](js-apis-app-ability-want.md#want) field. You can use these predefined keywords to set or retrieve additional parameter information carried in application transitions. For example, during the launch phase of a [UIAbility](js-apis-app-ability-uiAbility.md), if the value of **ABILITY_RECOVERY_RESTART** obtained from the **want** field in the **onCreate** callback is **true**, the current UIAbility has restarted due to a fault.

**System capability**: SystemCapability.Ability.AbilityBase

| Name                   | Value                                | Description                                                                          |
| ----------------------- | ---------------------------------- | ------------------------------------------------------------------------------ |
| ABILITY_BACK_TO_OTHER_MISSION_STACK   | ability.params.backToOtherMissionStack     | Indicates whether to support returning across mission stacks.<br>This parameter controls the return logic of cross-application UIAbility. Its core purpose is to change the application jump behavior when the user presses the back key. For example, suppose there are UIAbility A and UIAbility B. UIAbility A is currently displayed in the foreground, and then the system service starts UIAbility B (with this parameter set to true in the Params field of Want). In this case, when UIAbility B exits, it returns to UIAbility A (that is, returns to the most recently accessed task). If this parameter is not configured, the system returns to the home screen by default. Note that this field can be set only by the system. If a third-party application passes this field, it does not take effect.<br>**Atomic service API**: Since API version 11, this API is supported in atomic services.  |
| ABILITY_RECOVERY_RESTART<sup>10+</sup> | ohos.ability.params.abilityRecoveryRestart | Indicates whether the current Ability has been restarted due to fault recovery. Fault recovery restart means that after an Ability is automatically restarted due to an abnormal crash or other reasons, the system sets this parameter to true. Developers can check this parameter in the onCreate callback to determine whether it is a fault recovery scenario.<br>**Atomic service API**: Since API version 11, this API is supported in atomic services. |
| CONTENT_TITLE_KEY<sup>10+</sup>       | ohos.extra.param.key.contentTitle  | Title for sharing in an atomic service.<br>You can set the sharing title using this field in the [onShare](js-apis-app-ability-uiAbility.md#onshare10) callback.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| SHARE_ABSTRACT_KEY<sup>10+</sup>      | ohos.extra.param.key.shareAbstract | Content abstract for sharing in an atomic service.<br>You can set the sharing abstract using this field in the [onShare](js-apis-app-ability-uiAbility.md#onshare10) callback.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| SHARE_URL_KEY<sup>10+</sup>           | ohos.extra.param.key.shareUrl      | URL link for sharing in an atomic service.<br>You can set the URL link using this field in the [onShare](js-apis-app-ability-uiAbility.md#onshare10) callback.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| SUPPORT_CONTINUE_PAGE_STACK_KEY<sup>10+</sup>    | ohos.extra.param.key.supportContinuePageStack  | Whether to migrate the page stack information during cross-device migration. The default value is **true**, indicating that the page stack information is automatically migrated during cross-device migration.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| SUPPORT_CONTINUE_SOURCE_EXIT_KEY<sup>10+</sup>  | ohos.extra.param.key.supportContinueSourceExit      | Whether the source application exits during cross-device migration. The default value is** true**, indicating that the source application automatically exits during cross-device migration.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| SHOW_MODE_KEY<sup>12+</sup>  | ohos.extra.param.key.showMode      | Indicates the display mode of [EmbeddableUIAbility](js-apis-app-ability-embeddableUIAbility.md). The value is of the enum type [ShowMode](#showmode12).<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.|
| PARAMS_STREAM<sup>12+</sup>  | ability.params.stream  | Indicates the list of file URIs authorized to the target party. The corresponding value must be an array of file URIs of the string type. For how to obtain file URIs, see the [fileUri](../apis-core-file-kit/js-apis-file-fileuri.md) format specification. This field must be used together with the file URI read/write [Flags](#flags).<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
| APP_CLONE_INDEX_KEY<sup>12+</sup>  | ohos.extra.param.key.appCloneIndex  | Indicates the index of an app clone. An app clone refers to multiple independent instances of the same application. The system assigns a unique index to each instance to distinguish different application instances. In application jump scenarios, developers can set this parameter to specify the target app clone.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
| CALLER_REQUEST_CODE<sup>12+</sup>  | ohos.extra.param.key.callerRequestCode  | Request code<br>that uniquely identifies the caller of [startAbilityForResult](js-apis-inner-application-uiAbilityContext.md#startabilityforresult) or [openLink](js-apis-inner-application-uiAbilityContext.md#openlink12). When either of the APIs is called to start an ability, the target ability returns the result to the caller based on the request code.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| PAGE_PATH<sup>12+</sup>  | ohos.param.atomicservice.pagePath | Page path for an atomic service.<br>If page redirection in an atomic service is implemented using [router](../../ui/arkts-routing.md), you can use this parameter to specify the target page, for example, **library/ets/pages/menu**.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| ROUTER_NAME<sup>12+</sup>  | ohos.param.atomicservice.routerName | Router name for page redirection in an atomic service.<br>If page redirection in an atomic service is implemented using [Navigation](../../ui/arkts-navigation-architecture.md), you can use **ROUTER_NAME**, **PAGE_SOURCE_FILE**, and **BUILD_FUNCTION** together to specify the target page.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| PAGE_SOURCE_FILE<sup>12+</sup>  | ohos.param.atomicservice.pageSourceFile | Indicates the page source file of an atomic service.<br>If the page navigation of an atomic service is implemented through [Navigation](../../ui/arkts-navigation-architecture.md), you can use ROUTER_NAME, PAGE_SOURCE_FILE, and BUILD_FUNCTION together to specify the page to navigate to. ROUTER_NAME is the route name, PAGE_SOURCE_FILE is the page source file path, and BUILD_FUNCTION is the page builder function name. The three parameters must correspond to each other one by one.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.  |
| BUILD_FUNCTION<sup>12+</sup>  | ohos.param.atomicservice.buildFunction | Build function for the page in an atomic service.<br>If page redirection in an atomic service is implemented using [Navigation](../../ui/arkts-navigation-architecture.md), you can use **ROUTER_NAME**, **PAGE_SOURCE_FILE**, and **BUILD_FUNCTION** together to specify the target page.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| SUB_PACKAGE_NAME<sup>12+</sup>  | ohos.param.atomicservice.subpackageName | Indicates the subpackage name of an atomic service. An application package supports multi-module development, and each application package may contain multiple HAPs or HSPs. To achieve fast startup, atomic services impose limits on the file sizes of HAPs (Harmony Ability Package) and HSPs (Harmony Shared Package), and optimize the startup mechanism. This multi-module development approach of atomic services is called "subpackaging".<br>When opening an atomic service, you can set this parameter to start the corresponding subpackage.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.  |
| APP_INSTANCE_KEY<sup>14+</sup>  | ohos.extra.param.key.appInstance  | Indicates a specific application instance.<br>When [creating multiple instances of an application](../../quick-start/multiInstance.md), the system assigns a unique identifier to each instance. During application jump, developers can set this parameter to specify the created application instance to jump to. Note that the application to be started must support multiple instances, and the specified instance must have been created. For details, see [Creating Multiple Instances of an Application](../../quick-start/multiInstance.md). |
| CREATE_APP_INSTANCE_KEY<sup>14+</sup>  | ohos.extra.param.key.createAppInstance  | Whether to create an application instance. The default value is **false**, indicating that no new application instance is created.<br>You can set this parameter to **true** to launch a new application instance. Note that the application to be launched must support multiple instances. For details, see [Creating an Application Multi-Instance](../../quick-start/multiInstance.md).|
| CALLER_APP_CLONE_INDEX<sup>14+</sup>  | ohos.param.callerAppCloneIndex  | Indicates the app clone index of the caller application. For details, see [Creating an App Clone](../../quick-start/app-clone.md).|
| APP_LAUNCH_TRUSTLIST<sup>17+</sup>  | ohos.params.appLaunchTrustList  | Indicates the application filter list for implicit launch.<br>During implicit launch, only applications in the list are matched. The value is an array of [AppIdentifier](js-apis-bundleManager-bundleInfo.md#signatureinfo) of the string type. The filter list supports a maximum of 50 applications. Passing an empty array does not take effect.<br>**Atomic service API**: Since API version 17, this API is supported in atomic services. |
| LAUNCH_REASON_MESSAGE<sup>18+</sup>  | ohos.params.launchReasonMessage  | Indicates the reason for launching an application.<br>The caller must be a system application and must have the ohos.permission.SET_LAUNCH_REASON_MESSAGE permission. If a third-party application passes this field, it does not take effect. The supported values are as follows:<br>"ReasonMessage_SystemShare": indicates that the application is launched by system sharing.<br>"ReasonMessage_DesktopShortcut": indicates that the application is launched by a desktop shortcut.<br>"ReasonMessage_Notification": indicates that the application is launched by a notification.<br>**Atomic service API**: Since API version 18, this API is supported in atomic services. |
| DESTINATION_PLUGIN_ABILITY<sup>19+</sup>  | ohos.params.pluginAbility  | Indicates that the target Ability is a plugin Ability. After this flag is set, the system identifies the target Ability as a plugin Ability and starts it in plugin mode. When starting a plugin Ability, developers need to set this field to true in Want to identify the type of the target Ability. A plugin Ability has its own dedicated lifecycle and running mode, which differ from those of a common Ability. |
| ATOMIC_SERVICE_SHARE_ROUTER<sup>20+</sup> | ohos.params.atomicservice.shareRouter | Indicates the page stack information of the atomic service to be started, which is used to specify the target page to navigate to. The value is page stack information of the string type. Developers can obtain the current page stack information through [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md) and pass it. This field takes effect only when the caller is a UIAbilityContext and the callee is an atomic service.<br>For example, an atomic service contains a home page and a second page. If you want to directly start the second page of the atomic service, you can pass the page stack information of the second page through this field when starting the atomic service.<br>**Note:** Since API version 26.0.0, if the caller has the ohos.permission.START_ABILITY_TO_PAGE permission, this field also takes effect when the target is not an atomic service.<br>**Atomic service API**: Since API version 20, this API is supported in atomic services. |
| ABILITY_UNIFIED_DATA_KEY<sup>20+</sup>  | ohos.param.ability.udKey  | Indicates the unique identifier used for file sharing based on [unifiedDataChannel](../apis-arkdata/js-apis-data-unifiedDataChannel.md). This field can be set only by system applications, and third-party applications can read it.<br>When the Want contains a URI authorization flag field (that is, [FLAG_AUTH_READ_URI_PERMISSION](#flags) or [FLAG_AUTH_WRITE_URI_PERMISSION](#flags)) and also contains the PARAMS_STREAM field, this field does not take effect. <br>**Atomic service API**: Since API version 20, this API is supported in atomic services.|

## Flags

Enumerates the common preset keywords of the [Want.flags](js-apis-app-ability-want.md#want) field. You can use these predefined keywords to set or retrieve additional flag information carried in application transitions.

**System capability**: SystemCapability.Ability.AbilityBase

| Name                                | Value      | Description                                                        |
| ------------------------------------ | ---------- | ------------------------------------------------------------ |
| FLAG_AUTH_READ_URI_PERMISSION        | 0x00000001 | Temporarily grants the recipient the permission to read the data pointed to by this URI. The permission is valid only while the recipient application is running and is limited to reading the data specified by the URI.<br>**Atomic service API:** This API can be used in atomic services since API version 11.                                  |
| FLAG_AUTH_WRITE_URI_PERMISSION       | 0x00000002 | Temporarily grants the recipient the permission to write the data pointed to by this URI. The permission is valid only while the recipient application is running and is limited to writing the data specified by the URI.<br>**Atomic service API:** This API can be used in atomic services since API version 11.                                  |
| FLAG_AUTH_PERSISTABLE_URI_PERMISSION<sup>12+</sup> | 0x00000040 | Indicates that this URI can be persisted by the recipient. The recipient can persist the permission through the [fileShare.persistPermission](../apis-core-file-kit/js-apis-fileShare.md#filesharepersistpermission11) API.|
| FLAG_INSTALL_ON_DEMAND               | 0x00000800 | Enables on-demand installation when launching an atomic service.<br>- If enabled, the system automatically installs the atomic service if it is not already installed before proceeding with the launch.<br>- If disabled, the launch fails if the atomic service is not installed.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                             |
| FLAG_START_WITHOUT_TIPS<sup>11+</sup>              | 0x40000000 | Indicates whether to disable the dialog box that appears when no match is found. When this flag is set, the dialog box is disabled; when it is not set, the default dialog box behavior is retained.<br>When an application is started [implicitly](../../application-models/app-startup-overview.md), if no application can be matched, a dialog box with the message "No available way to open" is displayed by default. Developers can use this field to suppress the dialog box.       |
| FLAG_ABILITY_ON_COLLABORATE<sup>18+</sup> | 0x00002000 | In a multi-device collaboration scenario, when the caller application initiates a request through the DMS and sets this flag in Flags, the collaborator application triggers the lifecycle callback method [onCollaborate()](js-apis-app-ability-uiAbility.md#oncollaborate18). |

## ShowMode<sup>12+</sup>

Enumerates the display modes of an [EmbeddableUIAbility](js-apis-app-ability-embeddableUIAbility.md) when it is launched.

**System capability**: SystemCapability.Ability.AbilityBase

| Name                               | Value| Description          |
| ----------------------------------- |---|--------------|
| WINDOW        | 0 | Independent window launch mode.<br>**Atomic service API:** Since API version 12, this API is supported in atomic services.  |
| EMBEDDED_FULL       | 1 | Embedded full-screen launch mode.<br>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| EMBEDDED_HALF<sup>23+</sup>       | 2 | Embedded half-screen launch mode.<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API:** Since API version 23, this API is supported in atomic services. |

## Action

Enumerates the common operations to perform.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AbilityBase

**Model restriction:** This API can be used only in the stage model.

| Name                                | Value | Description          |
| ----------------------------------- |---|--------------|
| ACTION_SEND_TO_DATA        | ohos.want.action.sendToData | Indicates the operation of starting the UI for sending a message to a specified receiver.  |
