# ArkUI_CrossLanguageOption
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_CrossLanguageOption ArkUI_CrossLanguageOption
```

## Overview

Defines a cross-language configuration option, which is used to configure the cross-language access capability of a target node, for example, whether cross-language attribute modification is allowed. Since API version 26.0.0, you can also configure cross-language operation status of a node tree.

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

**Related APIs**
| Name                                                                             | Description|
|---------------------------------------------------------------------------------| -- |
| [OH_ArkUI_NodeUtils_SetCrossLanguageOption](capi-native-node-h.md#oh_arkui_nodeutils_setcrosslanguageoption) | Sets a cross-language configuration option for a target node.|
| [OH_ArkUI_NodeUtils_GetCrossLanguageOption](capi-native-node-h.md#oh_arkui_nodeutils_getcrosslanguageoption) | Obtains the cross-language configuration option of the target node.|
| [OH_ArkUI_CrossLanguageOption_Create](capi-native-type-h.md#oh_arkui_crosslanguageoption_create) | Creates an instance of the cross-language configuration option. After using the instance, call [OH_ArkUI_CrossLanguageOption_Destroy](capi-native-type-h.md#oh_arkui_crosslanguageoption_destroy) to destroy it.|
| [OH_ArkUI_CrossLanguageOption_Destroy](capi-native-type-h.md#oh_arkui_crosslanguageoption_destroy) | Destroys an instance of the cross-language configuration option.|
| [OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_setattributesettingstatus) | Sets whether cross-language attribute setting is allowed in the configuration option.|
| [OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_getattributesettingstatus) | Checks whether cross-language attribute setting is allowed in the configuration option.|
| [OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_settreeoperatingstatus) | Sets the node tree operation state of a cross-language configuration option.|
| [OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_gettreeoperatingstatus) | Obtains the node tree operation state of a cross-language configuration option.|
