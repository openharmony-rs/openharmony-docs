# Params

Defines **Params** (specifying the action that can be performed) in the Want.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## ABILITY_BACK_TO_OTHER_MISSION_STACK

```TypeScript
ABILITY_BACK_TO_OTHER_MISSION_STACK = 'ability.params.backToOtherMissionStack'
```

Whether redirection back across mission stacks is supported.

This parameter controls the redirection-back logic across applications, altering the application transition behavior when the user presses the back button. For example, if UIAbility A is currently displayed and UIAbility B is launched with this parameter set to **true**, exiting UIAbility B will return to UIAbility A. If this parameter is not set, the system defaults to returning to the home screen. Note that this parameter is only supported for system applications and does not take effect for third-party applications.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## ABILITY_RECOVERY_RESTART

```TypeScript
ABILITY_RECOVERY_RESTART = 'ohos.ability.params.abilityRecoveryRestart'
```

Whether the ability has been restarted due to a fault.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## CONTENT_TITLE_KEY

```TypeScript
CONTENT_TITLE_KEY = 'ohos.extra.param.key.contentTitle'
```

Title for sharing in an atomic service.

You can set the sharing title using this field in the [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare) callback.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## SHARE_ABSTRACT_KEY

```TypeScript
SHARE_ABSTRACT_KEY = 'ohos.extra.param.key.shareAbstract'
```

Content abstract for sharing in an atomic service.

You can set the sharing abstract using this field in the [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare) callback.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## SHARE_URL_KEY

```TypeScript
SHARE_URL_KEY = 'ohos.extra.param.key.shareUrl'
```

URL link for sharing in an atomic service.

You can set the URL link using this field in the [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare) callback.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## SUPPORT_CONTINUE_PAGE_STACK_KEY

```TypeScript
SUPPORT_CONTINUE_PAGE_STACK_KEY = 'ohos.extra.param.key.supportContinuePageStack'
```

Whether to migrate the page stack information during cross-device migration. The default value is **true**, indicating that the page stack information is automatically migrated during cross-device migration.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## SUPPORT_CONTINUE_SOURCE_EXIT_KEY

```TypeScript
SUPPORT_CONTINUE_SOURCE_EXIT_KEY = 'ohos.extra.param.key.supportContinueSourceExit'
```

Whether the source application exits during cross-device migration. The default value is** true**, indicating that the source application automatically exits during cross-device migration.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## SHOW_MODE_KEY

```TypeScript
SHOW_MODE_KEY = 'ohos.extra.param.key.showMode'
```

Display mode of the [EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md). The value is an enumerated value of [ShowMode](arkts-ability-wantconstant-showmode-e.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## PARAMS_STREAM

```TypeScript
PARAMS_STREAM = 'ability.params.stream'
```

List of file URIs authorized to the target. The value must be an array of file URIs of the string type. For details about how to obtain the file URI, see [fileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md). This field must be used in conjunction with file URI [read/write flag](arkts-ability-wantconstant-flags-e.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## APP_CLONE_INDEX_KEY

```TypeScript
APP_CLONE_INDEX_KEY = 'ohos.extra.param.key.appCloneIndex'
```

Index of an application clone.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## CALLER_REQUEST_CODE

```TypeScript
CALLER_REQUEST_CODE = 'ohos.extra.param.key.callerRequestCode'
```

Request code

that uniquely identifies the caller of startAbilityForResult or [openLink](arkts-ability-uiabilitycontext-c.md#openlink). When either of the APIs is called to start an ability, the target ability returns the result to the caller based on the request code.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## PAGE_PATH

```TypeScript
PAGE_PATH = 'ohos.param.atomicservice.pagePath'
```

Page path for an atomic service.

If page redirection in an atomic service is implemented using [router](../../../ui/arkts-routing.md), you can use this parameter to specify the target page, for example, **library/ets/pages/menu**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## ROUTER_NAME

```TypeScript
ROUTER_NAME = 'ohos.param.atomicservice.routerName'
```

Router name for page redirection in an atomic service.

If page redirection in an atomic service is implemented using [Navigation](../../../ui/arkts-navigation-architecture.md), you can use **ROUTER_NAME**, **PAGE_SOURCE_FILE**, and **BUILD_FUNCTION** together to specify the target page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## PAGE_SOURCE_FILE

```TypeScript
PAGE_SOURCE_FILE = 'ohos.param.atomicservice.pageSourceFile'
```

Source file for the page in an atomic service.

If page redirection in an atomic service is implemented using [Navigation](../../../ui/arkts-navigation-architecture.md), you can use **ROUTER_NAME**, **PAGE_SOURCE_FILE**, and **BUILD_FUNCTION** together to specify the target page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## BUILD_FUNCTION

```TypeScript
BUILD_FUNCTION = 'ohos.param.atomicservice.buildFunction'
```

Build function for the page in an atomic service.

If page redirection in an atomic service is implemented using [Navigation](../../../ui/arkts-navigation-architecture.md), you can use **ROUTER_NAME**, **PAGE_SOURCE_FILE**, and **BUILD_FUNCTION** together to specify the target page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## SUB_PACKAGE_NAME

```TypeScript
SUB_PACKAGE_NAME = 'ohos.param.atomicservice.subpackageName'
```

Sub-package name for an atomic service. Application packages can be developed with multiple modules, and each package may include one or multiple HAPs or HSPs. To enhance the launch speed, atomic services restrict the size of HAP and HSP files and optimize the startup process. This modular development approach is known as sub- packaging.

When you open an atomic service, you can use this parameter to activate the specific sub-package.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## APP_INSTANCE_KEY

```TypeScript
APP_INSTANCE_KEY = 'ohos.extra.param.key.appInstance'
```

Specific application instance.

When you create [multiple instances](../../../quick-start/multiInstance.md) of an application, the system assigns a unique ID to each instance. During application transitions, you can use this parameter to specify which created application instance you want to transition to.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityBase

## CREATE_APP_INSTANCE_KEY

```TypeScript
CREATE_APP_INSTANCE_KEY = 'ohos.extra.param.key.createAppInstance'
```

Whether to create an application instance. The default value is **false**, indicating that no new application instance is created.

You can set this parameter to **true** to launch a new application instance. Note that the application to be launched must support multiple instances. For details, see [Creating an Application Multi-Instance](../../../quick-start/multiInstance.md).

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityBase

## CALLER_APP_CLONE_INDEX

```TypeScript
CALLER_APP_CLONE_INDEX = 'ohos.param.callerAppCloneIndex'
```

Clone index of the caller.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityBase

## DESTINATION_PLUGIN_ABILITY

```TypeScript
DESTINATION_PLUGIN_ABILITY = 'ohos.params.pluginAbility'
```

The target ability is a plugin ability.

**Since:** 19

**System capability:** SystemCapability.Ability.AbilityBase

## APP_LAUNCH_TRUSTLIST

```TypeScript
APP_LAUNCH_TRUSTLIST = 'ohos.params.appLaunchTrustList'
```

Filter list of applications for implicit launch.

Only applications in the list are matched during implicit launch. The value is an array of AppIdentifier of the string type. The filter list supports a maximum of 50 applications. Passing an empty array will have no effect.

**Since:** 17

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Ability.AbilityBase

## ATOMIC_SERVICE_SHARE_ROUTER

```TypeScript
ATOMIC_SERVICE_SHARE_ROUTER = 'ohos.params.atomicservice.shareRouter'
```

Page stack information of the atomic service being launched. This parameter takes effect only when the caller is a UIAbilityContext and the callee is an atomic service.

For example, if an atomic service contains a home page and a second page, and you want to directly launch the second page, you can pass the page stack information of the second page through this field when launching the atomic service.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityBase

## LAUNCH_REASON_MESSAGE

```TypeScript
LAUNCH_REASON_MESSAGE = 'ohos.params.launchReasonMessage'
```

Reason for launching the application.

The caller must be a system application and must request the ohos.permission.SET_LAUNCH_REASON_MESSAGE permission. The following values are supported:

**ReasonMessage_SystemShare**: The application is launched through system sharing.

**ReasonMessage_DesktopShortcut**: The application is launched through a home screen shortcut.

**ReasonMessage_Notification**: The application is launched through a notification.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityBase

## ABILITY_UNIFIED_DATA_KEY

```TypeScript
ABILITY_UNIFIED_DATA_KEY = 'ohos.param.ability.udKey'
```

Unique identifier for file sharing based on [UDMF](../../apis-arkdata/arkts-apis/arkts-arkdata-data-unifieddatachannel.md). This field can only be set by system applications, but third-party applications can read it.

If the Want contains a URI authorization flag (for example, [FLAG_AUTH_READ_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md) or [FLAG_AUTH_WRITE_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md)) and the **PARAMS_STREAM** field is also present, this field does not take effect.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityBase
