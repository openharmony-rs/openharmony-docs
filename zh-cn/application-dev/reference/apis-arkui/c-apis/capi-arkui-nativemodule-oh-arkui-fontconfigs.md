# OH_ArkUI_FontConfigs

```c
typedef struct OH_ArkUI_FontConfigs OH_ArkUI_FontConfigs
```

## 概述

定义文本的字体配置，当前支持通过相关接口设置和获取字体粗细配置，适用于需要自定义字体粗细显示效果的场景。 可以通过{@link OH_ArkUI_FontConfigs_Create}接口创建字体配置对象，通过{@link OH_ArkUI_FontConfigs_Destroy}接口销毁字体配置对象。<br> 配置创建后通过{@link OH_ArkUI_FontConfigs_SetFontWeightConfigs}接口设置字体粗细配置，<br> 通过{@link OH_ArkUI_FontConfigs_GetFontWeightConfigs}接口获取字体粗细配置。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [text.h](capi-text-h.md)

