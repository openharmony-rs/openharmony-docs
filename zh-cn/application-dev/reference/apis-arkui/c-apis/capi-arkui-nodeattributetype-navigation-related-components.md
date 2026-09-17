# 导航类组件

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_SWIPER_SHOW_DISPLAY_ARROW

```c
NODE_SWIPER_SHOW_DISPLAY_ARROW
```

**描述：**

Defines whether to show the arrow when the mouse pointer hovers over the navigation point indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator.<br>The parameter type is {@link ArkUI_SwiperArrow}.<br>The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li><br><li>.?object: arrow style. The parameter type is {@link ArkUI_SwiperArrowStyle}.<br>This parameter is supported since API version 19.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator.<br>The parameter type is {@link ArkUI_SwiperArrow}.<br>The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li><br><li>.object: arrow style. The parameter type is {@link ArkUI_SwiperArrowStyle}. This parameter is supported since API version 19.</li> </ul>

**起始版本：** 12


