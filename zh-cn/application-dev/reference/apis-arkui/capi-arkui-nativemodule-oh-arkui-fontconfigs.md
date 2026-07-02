# OH_ArkUI_FontConfigs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_FontConfigs OH_ArkUI_FontConfigs
```

## 概述

定义文本的字体配置。可以通过[OH_ArkUI_FontConfigs_Create](capi-text-h.md#oh_arkui_fontconfigs_create) 接口创建文本字体配置对象。可以通过[OH_ArkUI_FontConfigs_Destroy](capi-text-h.md#oh_arkui_fontconfigs_destroy) 接口销毁文本字体配置对象。配置创建后通过[OH_ArkUI_FontConfigs_SetFontWeightConfigs](capi-text-h.md#oh_arkui_fontconfigs_setfontweightconfigs) 接口设置文本的字体粗细配置。配置创建后通过[OH_ArkUI_FontConfigs_GetFontWeightConfigs](capi-text-h.md#oh_arkui_fontconfigs_getfontweightconfigs) 接口获取文本的字体粗细配置。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [text.h](capi-text-h.md)

