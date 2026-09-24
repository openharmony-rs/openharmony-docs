# OH_ArkUI_TextStyle

```c
typedef struct OH_ArkUI_TextStyle OH_ArkUI_TextStyle
```

## 概述

定义文本字体样式，用于设置文本的字体颜色、大小、样式等属性，适用于需要自定义文本显示效果的场景。 调用{@link OH_ArkUI_TextStyle_Create}接口创建文本字体样式对象。<br>调用{@link OH_ArkUI_TextStyle_Destroy}接口销毁文本字体样式对象。销毁后不应再调用OH_ArkUI_TextStyle_SetXXX系列接口。<br>对象创建成功后，调用OH_ArkUI_TextStyle_SetXXX系列接口设置具体样式；若创建失败则不可调用SetXXX系列接口。<br>例如，调用{@link OH_ArkUI_TextStyle_SetFontColor}设置字体颜色。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)

