# OH_ArkUI_TextController

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yao_qiaoming1-->
<!--Designer: @xiangyuan6-->
<!--Tester: @mateng_Holtens-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-08-21T04:07:38.939Z pushedAt=2026-08-21T06:37:25.830Z -->

```c
typedef struct OH_ArkUI_TextController OH_ArkUI_TextController
```

## Overview

Defines a text component controller, which is used to control and interact with the text component on the native side. You can create a controller object through [OH_ArkUI_TextController_Create](capi-text-h.md#oh_arkui_textcontroller_create). When the object is created, you must call [OH_ArkUI_TextController_Destroy](capi-text-h.md#oh_arkui_textcontroller_destroy) to destroy it and release resources after use. The two must be used in pairs; otherwise, memory leaks will occur. After the controller is created, you can use APIs such as [OH_ArkUI_TextController_SetStyledString](capi-native-type-h.md#oh_arkui_textcontroller_setstyledstring) to set the styled string of the text component, implementing dynamic management and style control of the text content. This is applicable to scenarios where the text component needs to be operated at the native layer.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [text.h](capi-text-h.md)