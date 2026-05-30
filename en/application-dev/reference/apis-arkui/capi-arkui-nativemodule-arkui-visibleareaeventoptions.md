# ArkUI_VisibleAreaEventOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_VisibleAreaEventOptions ArkUI_VisibleAreaEventOptions
```

## Overview

Defines the parameters for visible area change events.

Before using this struct type, you need to call [OH_ArkUI_VisibleAreaEventOptions_Create](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_create) to create an **ArkUI_VisibleAreaEventOptions** object. Then, you can configure listening behavior using the following APIs:

Use [OH_ArkUI_VisibleAreaEventOptions_SetRatios](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_setratios) to set a threshold array, which defines the threshold conditions for triggering visible area changes.

Use [OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) to set an expected update interval.

Use [OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_setmeasurefromviewport) to set a calculation mode of a visible area.

To obtain the parameter values that have been set, you can:

Use [OH_ArkUI_VisibleAreaEventOptions_GetRatios](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_getratios) to obtain the threshold array.

Use [OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_getexpectedupdateinterval) to obtain the expected update interval.

Use [OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_getmeasurefromviewport) to obtain the calculation mode of the visible area.

After using the APIs, call [OH_ArkUI_VisibleAreaEventOptions_Dispose](capi-native-type-h.md#oh_arkui_visibleareaeventoptions_dispose) to dispose of the resources.

**Since**: 17

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)
