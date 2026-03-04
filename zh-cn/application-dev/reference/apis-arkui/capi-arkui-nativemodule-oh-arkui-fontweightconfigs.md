# OH_ArkUI_FontWeightConfigs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_FontWeightConfigs OH_ArkUI_FontWeightConfigs
```

## 概述

定义文本的字体粗细配置。可以通过[OH_ArkUI_FontWeightConfigs_Create](capi-native-type-h.md#oh_arkui_fontweightconfigs_create) 接口创建对应的文本字体粗细配置对象。可以通过[OH_ArkUI_FontWeightConfigs_Destroy](capi-native-type-h.md#oh_arkui_fontweightconfigs_destroy) 接口销毁文本字体粗细配置对象。配置创建后通过[OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight](capi-native-type-h.md#oh_arkui_fontweightconfigs_setenablevariablefontweight) 接口设置是否启用可变字体粗细调节。配置创建后通过[OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight](capi-native-type-h.md#oh_arkui_fontweightconfigs_getenablevariablefontweight) 接口查看是否启用了可变字体粗细调节。配置创建后通过[OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory](capi-native-type-h.md#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) 接口设置文本字体粗细是否跟随设备的字体粗细级别更新。配置创建后通过[OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory](capi-native-type-h.md#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) 接口查看文本字体粗细是否跟随设备的字体粗细级别更新。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

