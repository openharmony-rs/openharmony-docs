# OH_ArkUI_UrlStyle

```c
typedef struct OH_ArkUI_UrlStyle OH_ArkUI_UrlStyle
```

## 概述

定义链接样式，用于为属性字符串中的文本设置可点击的URL链接效果，适用于需要在文本内容中嵌入可交互链接的场景，可提升文本的交互性和用户体验。 调用{@link OH_ArkUI_UrlStyle_Create}接口创建链接样式对象。<br>调用{@link OH_ArkUI_UrlStyle_Destroy}接口销毁链接样式对象。<br>创建链接样式对象后，调用{@link OH_ArkUI_UrlStyle_SetUrl}接口设置链接地址。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)

