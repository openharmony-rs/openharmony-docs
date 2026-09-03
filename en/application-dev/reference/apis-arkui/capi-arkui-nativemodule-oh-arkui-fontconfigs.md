# OH_ArkUI_FontConfigs

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8a65b118b29a0c9d1936c3b96f0e90c33fab49ab translatedAt=2026-08-21T01:46:16.116Z pushedAt=2026-08-21T03:45:44.845Z -->

```c
typedef struct OH_ArkUI_FontConfigs OH_ArkUI_FontConfigs
```

## Overview

Defines the font configurations of text. Currently, it supports setting and obtaining the font weight configuration through related APIs, and is applicable to scenarios that require custom font weight display effects. You can create a font configuration object through the [OH_ArkUI_FontConfigs_Create](capi-text-h.md#oh_arkui_fontconfigs_create) API and destroy it through the [OH_ArkUI_FontConfigs_Destroy](capi-text-h.md#oh_arkui_fontconfigs_destroy) API. After the configurations are created, you can set and query them through the following APIs: set the font weight configuration through the [OH_ArkUI_FontConfigs_SetFontWeightConfigs](capi-text-h.md#oh_arkui_fontconfigs_setfontweightconfigs) API, and obtain the font weight configuration through the [OH_ArkUI_FontConfigs_GetFontWeightConfigs](capi-text-h.md#oh_arkui_fontconfigs_getfontweightconfigs) API.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [text.h](capi-text-h.md)