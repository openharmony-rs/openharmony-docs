# OH_ArkUI_NativeModule_LineSpacingOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_NativeModule_LineSpacingOptions OH_ArkUI_NativeModule_LineSpacingOptions
```

## 概述

定义文本行间距选项对象，用于配置文本行间距是否仅在行与行之间生效。可以通过[OH_ArkUI_NativeModule_LineSpacingOptions_Create](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_create)接口创建行间距选项对象，创建后必须在使用完毕后调用[OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy)接口销毁对象以释放资源。二者必须成对使用，否则会导致内存泄漏。创建对象后，可使用[OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_setonlybetweenlines)接口设置行间距是否仅在行与行之间生效，通过[OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_getonlybetweenlines)接口获取行间距配置。适用于需要精确控制文本行间距显示效果的场景，如排版要求首尾行不加行间距的文本显示。

**起始版本：** 26.1.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [text.h](capi-text-h.md)