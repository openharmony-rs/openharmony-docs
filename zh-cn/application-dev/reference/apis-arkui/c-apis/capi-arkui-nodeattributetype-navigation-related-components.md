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

Defines whether to show the arrow when the mouse pointer hovers over the navigation point indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator. The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow). The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li> <li>.?object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator. The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow). The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li> <li>.object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.</li> </ul>

**起始版本：** 12


