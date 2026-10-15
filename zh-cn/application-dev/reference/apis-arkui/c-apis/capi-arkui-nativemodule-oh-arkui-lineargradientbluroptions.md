# OH_ArkUI_LinearGradientBlurOptions

```c
typedef struct OH_ArkUI_LinearGradientBlurOptions OH_ArkUI_LinearGradientBlurOptions
```

## 概述

定义线性渐变模糊效果的选项。<br> 选项包括模糊半径、渐变停止点和方向。通过[OH_ArkUI_NativeModule_LinearGradientBlurOptions_Create](capi-native-type-visual-h.md#oh_arkui_nativemodule_lineargradientbluroptions_create)创建时， 默认值为：blurRadius = 0（不模糊），fractionStops = {0.0, 0.0, 0.0, 1.0}（两个停止点：位置0处模糊值为0， 位置1处模糊值为0，表示整个渐变方向上无模糊），direction = [OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_BOTTOM](capi-native-type-visual-h.md#oh_arkui_lineargradientblurdirection)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type_visual.h](capi-native-type-visual-h.md)

