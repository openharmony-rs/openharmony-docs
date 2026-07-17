# embedded_component.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the structs and APIs of the **EmbeddedComponent** component.

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
| [ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()](#oh_arkui_embeddedcomponentoption_create) | - | Creates an **EmbeddedComponent** option object.|
| [void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)](#oh_arkui_embeddedcomponentoption_dispose) | - | Disposes of an **EmbeddedComponent** option object.|
| [void OH_ArkUI_EmbeddedComponentOption_SetOnError (ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, const char* name, const char* message))](#oh_arkui_embeddedcomponentoption_setonerror) | - | Sets the **onError** callback for the **EmbeddedComponent** component. This callback is triggered when an error occurs during the running of the **EmbeddedComponent** component.|
| [void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated (ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, AbilityBase_Want* want))](#oh_arkui_embeddedcomponentoption_setonterminated) | - | Sets the **onTerminated** callback for the **EmbeddedComponent** component. This callback is triggered when the **EmbeddedComponent** component exits properly.|

## Function Description

### OH_ArkUI_EmbeddedComponentOption_Create()

```c
ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()
```

**Description**


Creates an **EmbeddedComponent** option object.

**Since:** 20

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* | Pointer to the **EmbeddedComponent** option object.|

### OH_ArkUI_EmbeddedComponentOption_Dispose()

```c
void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)
```

**Description**


Disposes of an **EmbeddedComponent** option object.

**Since:** 20


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the target **EmbeddedComponent** option object.|

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
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the **EmbeddedComponent** option object.|
| void (\*callback)(int32_t code, const char* name, const char* message) | Pointer to the user-defined callback function.<br>- **code**: error code returned when the API call fails. For details about error codes, see [UIExtension Error Codes](errorcode-uiextension.md).<br>- **name**: error name returned when the API call fails.<br>- **message**: detailed error message returned when the API call fails.|


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
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the **EmbeddedComponent** option object.|
| void (\*callback)(int32_t code, [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)* want) | Pointer to the user-defined callback function.<br>- **code**: result code returned when the started [EmbeddedUIExtensionAbility](../apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md) exits. If the **EmbeddedUIExtensionAbility** exits by calling [terminateSelfWithResult](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateselfwithresult), the result code is the value set by the **EmbeddedUIExtensionAbility**. If the **EmbeddedUIExtensionAbility** exits by calling [terminateSelf](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateself), the result code is the default value **0**.<br>- **want**: data returned when the **EmbeddedUIExtensionAbility** exits.  |
