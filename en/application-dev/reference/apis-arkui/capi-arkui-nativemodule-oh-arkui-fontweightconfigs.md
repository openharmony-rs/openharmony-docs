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

## Overview

Defines the font weight configuration of text. [OH_ArkUI_FontWeightConfigs_Create](capi-native-type-h.md#oh_arkui_fontweightconfigs_create) can be used to create a text font weight configuration object. [OH_ArkUI_FontWeightConfigs_Destroy](capi-native-type-h.md#oh_arkui_fontweightconfigs_destroy) can be used to destroy the text font weight configuration object. After the object is created, [OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight](capi-native-type-h.md#oh_arkui_fontweightconfigs_setenablevariablefontweight) can be used to set whether to enable variable font weight adjustment. After the object is created, [OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight](capi-native-type-h.md#oh_arkui_fontweightconfigs_getenablevariablefontweight) can be used to check whether variable font weight adjustment is enabled. After the object is created, [OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory](capi-native-type-h.md#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) can be used to set whether the text font weight is updated with the font weight level of the device. After the object is created, [OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory](capi-native-type-h.md#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) can be used to check whether the text font weight is updated with the font weight level of the device. When the object is used and is not a null pointer, if the user does not explicitly make the configuration through the API, the default values are used. When the object is a null pointer, the default values are not used, and the text font weight behavior is the same as that of the parent component.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)
