# OH_ArkUI_CustomSpan
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_CustomSpan OH_ArkUI_CustomSpan
```

## 概述

定义自定义绘制Span。 <br>        可以通过[OH_ArkUI_CustomSpan_Create](capi-styled-string-h.md#oh_arkui_customspan_create)接口创建对应的自定义绘制Span对象。 <br>        可以通过[OH_ArkUI_CustomSpan_Destroy](capi-styled-string-h.md#oh_arkui_customspan_destroy)接口销毁自定义绘制Span对象。 <br>        对象创建后通过[OH_ArkUI_CustomSpan_RegisterOnMeasureCallback](capi-styled-string-h.md#oh_arkui_customspan_registeronmeasurecallback)和[OH_ArkUI_CustomSpan_RegisterOnDrawCallback](capi-styled-string-h.md#oh_arkui_customspan_registerondrawcallback)接口分别注册测量和绘制回调函数。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)