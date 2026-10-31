# OH_ArkUI_TextController
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yao_qiaoming1-->
<!--Designer: @xiangyuan6-->
<!--Tester: @mateng_Holtens-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_TextController OH_ArkUI_TextController
```

## 概述

定义文本组件的控制器，用于在Native侧对文本组件进行控制和交互。可通过[OH_ArkUI_TextController_Create](capi-text-h.md#oh_arkui_textcontroller_create)创建控制器对象，创建后必须在使用完毕后调用[OH_ArkUI_TextController_Destroy](capi-text-h.md#oh_arkui_textcontroller_destroy)接口销毁对象以释放资源，二者必须成对使用，否则会导致内存泄漏。创建控制器后，可使用[OH_ArkUI_TextController_SetStyledString](capi-native-type-h.md#oh_arkui_textcontroller_setstyledstring)等接口设置文本组件的属性字符串，实现对文本内容的动态管理和样式控制。适用于需要在Native层操作文本组件的场景。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [text.h](capi-text-h.md)
