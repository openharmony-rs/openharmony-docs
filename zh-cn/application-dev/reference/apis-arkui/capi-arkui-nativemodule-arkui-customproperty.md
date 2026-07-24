# ArkUI_CustomProperty
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_CustomProperty ArkUI_CustomProperty
```

## 概述

定义表示组件自定义属性的 ArkUI_CustomProperty 结构体。通过相关接口，可以为 ArkUI 组件添加、移除和获取自定义属性，以及获取自定义属性的字符串值。

**起始版本：** 14

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

**相关接口：** 
| 名称                                                                              | 描述 |
|---------------------------------------------------------------------------------|------|
| [OH_ArkUI_NodeUtils_AddCustomProperty](capi-native-node-h.md#oh_arkui_nodeutils_addcustomproperty) | 添加组件的自定义属性。 |
| [OH_ArkUI_NodeUtils_RemoveCustomProperty](capi-native-node-h.md#oh_arkui_nodeutils_removecustomproperty) | 移除组件已设置的自定义属性。 |
| [OH_ArkUI_NodeUtils_GetCustomProperty](capi-native-node-h.md#oh_arkui_nodeutils_getcustomproperty) | 获取组件的自定义属性，并通过handle返回ArkUI_CustomProperty实例。 |
| [OH_ArkUI_CustomProperty_Destroy](capi-native-type-h.md#oh_arkui_customproperty_destroy) | 销毁 ArkUI_CustomProperty 实例。 |
| [OH_ArkUI_CustomProperty_GetStringValue](capi-native-type-h.md#oh_arkui_customproperty_getstringvalue) | 获取自定义属性的字符串值。 |
