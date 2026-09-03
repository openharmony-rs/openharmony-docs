# embedded_component.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=86516607de4ae31b89a087b4feaa5c2b41c67026 translatedAt=2026-08-21T04:09:43.856Z pushedAt=2026-08-21T08:57:02.471Z -->

## Overview

Defines the structs and APIs of the **EmbeddedComponent** component option (**ArkUI_EmbeddedComponentOption**). You can use these APIs to create and dispose of the component option object, and set the exception callback (**onError**) and normal exit callback (**onTerminated**) for the **EmbeddedComponent** component. This applies to scenarios where the **EmbeddedUIExtensionAbility** component needs to be embedded in an application and its lifecycle needs to be managed, and where exception and normal exit events need to be listened for, helping you flexibly handle state changes during component running.

**File to include:** <arkui/node_attributes/embedded_component.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[embedded_component_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md) | AbilityBase_Want | Declares **Want** of an ability.|
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | ArkUI_EmbeddedComponentOption | Defines the **EmbeddedComponentOption** parameter for **EmbeddedComponent**.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()](#oh_arkui_embeddedcomponentoption_create) | - | Creates an **EmbeddedComponent** component option object.|
| [void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)](#oh_arkui_embeddedcomponentoption_dispose) | - | Disposes of the **EmbeddedComponent** component option object. |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, const char* name, const char* message))](#oh_arkui_embeddedcomponentoption_setonerror) | - | Sets the **onError** callback of the **EmbeddedComponent** component. This callback is triggered when an exception occurs during the running of the **EmbeddedComponent** component. |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, AbilityBase_Want* want))](#oh_arkui_embeddedcomponentoption_setonterminated) | - | Sets the **onTerminated** callback of the **EmbeddedComponent** component. This callback is triggered when the **EmbeddedComponent** component exits normally. |

## Function Description

### OH_ArkUI_EmbeddedComponentOption_Create()

```c
ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()
```

**Description**

Creates an **EmbeddedComponent** component option object. The returned object needs to be disposed of by **OH_ArkUI_EmbeddedComponentOption_Dispose** when it is no longer used.

**Since:** 20

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* | Pointer to the **EmbeddedComponent** component option object.|

### OH_ArkUI_EmbeddedComponentOption_Dispose()

```c
void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)
```

**Description**

Destroys the **EmbeddedComponent** component option object. The object must be created by **OH_ArkUI_EmbeddedComponentOption_Create**, and it should not be used after being disposed of.

**Since:** 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the **EmbeddedComponent** component option object to be disposed of. It cannot be null and must be a valid object created by **OH_ArkUI_EmbeddedComponentOption_Create()**. |

### OH_ArkUI_EmbeddedComponentOption_SetOnError()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, const char* name, const char* message))
```

**Description**

Sets the [onError](../apis-arkui/arkui-ts/ts-container-embedded-component.md#onerror) callback for the **EmbeddedComponent** component. This callback is triggered when an error occurs during the running of the **EmbeddedComponent** component.

**Since:** 20

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the **EmbeddedComponent** component option object.|
| void (\*callback)(int32_t code, const char* name, const char* message) | Pointer to a custom callback. If this callback is not set, no callback is triggered when an exception occurs during the running of the **EmbeddedComponent** component.<br>- **code**: error code returned when an exception occurs during the running of the component. For details about the error codes, see [UIExtension Error Codes](errorcode-uiextension.md).<br>- **name**: name returned when an exception occurs during the running of the component.<br>- **message**: detailed information returned when an exception occurs during the running of the component. |

### OH_ArkUI_EmbeddedComponentOption_SetOnTerminated()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, AbilityBase_Want* want))
```

**Description**

Sets the [onTerminated](../apis-arkui/arkui-ts/ts-container-embedded-component.md#onterminated) callback for the **EmbeddedComponent** component. This callback is triggered when the **EmbeddedComponent** component exits properly.

**Since:** 20

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the **EmbeddedComponent** component option object.|
| void (\*callback)(int32_t code, [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)* want) | Pointer to a custom callback. If this callback is not set, it is not triggered when the **EmbeddedComponent** component exits normally.<br>- **code**: result code returned when the started [EmbeddedUIExtensionAbility](../apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md) exits. If **EmbeddedUIExtensionAbility** exits by calling [terminateSelfWithResult](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateselfwithresult), the result code is the value set by **EmbeddedUIExtensionAbility**. If **EmbeddedUIExtensionAbility** exits by calling [terminateSelf](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateself), the result code is the default value **0**.<br>- **want**: data returned when the started **EmbeddedUIExtensionAbility** exits. If **EmbeddedUIExtensionAbility** exits by calling [terminateSelfWithResult](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateselfwithresult), the returned data is the data set by **EmbeddedUIExtensionAbility**. If **EmbeddedUIExtensionAbility** exits by calling [terminateSelf](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateself), the returned data is the default value. |