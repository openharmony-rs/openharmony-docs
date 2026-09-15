# OH_ArkUI_FontWeightConfigs

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8a65b118b29a0c9d1936c3b96f0e90c33fab49ab translatedAt=2026-08-21T04:06:47.351Z pushedAt=2026-08-21T06:01:07.967Z -->

```c
typedef struct OH_ArkUI_FontWeightConfigs OH_ArkUI_FontWeightConfigs
```

## Overview

Defines the font weight configurations of text. It is suitable for scenarios that require precise control over text font weight or where the text font weight needs to follow device font setting changes. You can create a text font weight configuration object through [OH_ArkUI_FontWeightConfigs_Create](capi-text-h.md#oh_arkui_fontweightconfigs_create), and must call [OH_ArkUI_FontWeightConfigs_Destroy](capi-text-h.md#oh_arkui_fontweightconfigs_destroy) to destroy the object and release resources after use to avoid memory leaks. After the configuration object is created, you can set and query the information through the following APIs: use [OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight](capi-text-h.md#oh_arkui_fontweightconfigs_setenablevariablefontweight) to set whether to enable variable font weight adjustment, use [OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight](capi-text-h.md#oh_arkui_fontweightconfigs_getenablevariablefontweight) to check whether variable font weight adjustment is enabled, use [OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory](capi-text-h.md#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) to set whether the text font weight is updated with the font weight level of the device, and use [OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory](capi-text-h.md#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) to check whether the text font weight is updated with the font weight level of the device. When this configuration object is used and is not a null pointer, if the user does not explicitly make the configuration through the APIs, each configuration item uses its default value (variable font weight adjustment is disabled by default, and text font weight is updated with the font weight level of the device by default). When this configuration object is a null pointer, the default values are not used, and the text font weight behavior is the same as that of the parent component.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [text.h](capi-text-h.md)