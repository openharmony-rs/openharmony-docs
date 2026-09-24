# embedded_component.h

## Overview

Defines embedded component attribute and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md) | AbilityBase_Want | Declares the Ability base want. |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | ArkUI_EmbeddedComponentOption | Define the EmbeddedComponentOption for the EmbeddedComponent. |

### Macro

| Name | Description |
| -- | -- |
| ARKUI_EMBEDDED_COMPONENT_H | Defines embedded component attribute and interface.<br>**Since**: 12<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()](#oh_arkui_embeddedcomponentoption_create) | Creates an **EmbeddedComponent** option object. |
| [void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)](#oh_arkui_embeddedcomponentoption_dispose) | Disposes of an **EmbeddedComponent** option object. |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, const char* name, const char* message))](#oh_arkui_embeddedcomponentoption_setonerror) | Sets the {@link onError} callback for the **EmbeddedComponent** component. This callback is triggered when an error occurs during the running of the **EmbeddedComponent** component. |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, AbilityBase_Want* want))](#oh_arkui_embeddedcomponentoption_setonterminated) | Sets the {@link onTerminated} callback for the **EmbeddedComponent** component. This callback is triggered when the **EmbeddedComponent** component exits properly. |

## Function description

### OH_ArkUI_EmbeddedComponentOption_Create()

```c
ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()
```

**Description**

Creates an **EmbeddedComponent** option object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_EmbeddedComponentOption*](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | Pointer to the EmbeddedComponent option object. |

### OH_ArkUI_EmbeddedComponentOption_Dispose()

```c
void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)
```

**Description**

Disposes of an **EmbeddedComponent** option object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the target **EmbeddedComponent** option object. |

### OH_ArkUI_EmbeddedComponentOption_SetOnError()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, const char* name, const char* message))
```

**Description**

Sets the {@link onError} callback for the **EmbeddedComponent** component. This callback is triggered when an error occurs during the running of the **EmbeddedComponent** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_EmbeddedComponentOption\* option | Pointer to the **EmbeddedComponent** option object. |
| void (\*callback)(int32_t code | Callback function that will called when error occurs during the running of the **EmbeddedComponent** component |

### OH_ArkUI_EmbeddedComponentOption_SetOnTerminated()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, AbilityBase_Want* want))
```

**Description**

Sets the {@link onTerminated} callback for the **EmbeddedComponent** component. This callback is triggered when the **EmbeddedComponent** component exits properly.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_EmbeddedComponentOption\* option | Pointer to the **EmbeddedComponent** option object. |
| void (\*callback)(int32_t code | Callback function that will called when the **EmbeddedComponent** component exits properly. |


