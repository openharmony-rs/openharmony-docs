# OH_ArkUI_BackgroundColorStyle

```c
typedef struct OH_ArkUI_BackgroundColorStyle OH_ArkUI_BackgroundColorStyle
```

## 概述

定义背景颜色样式，支持自定义背景颜色和圆角半径，适用于为属性字符串设置背景高亮效果，例如搜索结果高亮、重点文本标记、标签式文本展示等场景，可提升文本的视觉层次和可辨识度。 调用{@link OH_ArkUI_BackgroundColorStyle_Create}接口创建背景颜色样式对象。<br>对象创建后，调用{@link OH_ArkUI_BackgroundColorStyle_SetColor}和<br>{@link OH_ArkUI_BackgroundColorStyle_SetRadius}接口设置背景颜色和圆角半径。<br>调用{@link OH_ArkUI_BackgroundColorStyle_GetColor}和{@link OH_ArkUI_BackgroundColorStyle_GetRadius}接口获取背景颜色和圆角半径。<br>使用完毕后，调用{@link OH_ArkUI_BackgroundColorStyle_Destroy}接口销毁背景颜色样式对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)

