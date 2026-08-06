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

## 概述

定义跨语言配置项，用于配置目标节点的跨语言访问能力，例如是否允许跨语言修改属性；从API version 26.0.0开始，还可配置节点树跨语言操作状态。

**起始版本：** 15

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

**相关接口：** 
| 名称                                                                              | 描述 |
|---------------------------------------------------------------------------------| -- |
| [OH_ArkUI_NodeUtils_SetCrossLanguageOption](capi-native-node-h.md#oh_arkui_nodeutils_setcrosslanguageoption) | 设置目标节点的跨语言配置项。 |
| [OH_ArkUI_NodeUtils_GetCrossLanguageOption](capi-native-node-h.md#oh_arkui_nodeutils_getcrosslanguageoption) | 获取目标节点的跨语言配置项。 |
| [OH_ArkUI_CrossLanguageOption_Create](capi-native-type-h.md#oh_arkui_crosslanguageoption_create) | 创建跨语言配置项实例。使用完毕后，需调用[OH_ArkUI_CrossLanguageOption_Destroy](capi-native-type-h.md#oh_arkui_crosslanguageoption_destroy)销毁实例。 |
| [OH_ArkUI_CrossLanguageOption_Destroy](capi-native-type-h.md#oh_arkui_crosslanguageoption_destroy) | 销毁跨语言配置项实例。 |
| [OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_setattributesettingstatus) | 设置配置项中是否允许跨语言修改属性。 |
| [OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_getattributesettingstatus) | 获取配置项中是否允许跨语言修改属性。 |
| [OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_settreeoperatingstatus) | 设置跨语言配置项的节点树操作状态。 |
| [OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoption_gettreeoperatingstatus) | 获取跨语言配置项的节点树操作状态。 |
