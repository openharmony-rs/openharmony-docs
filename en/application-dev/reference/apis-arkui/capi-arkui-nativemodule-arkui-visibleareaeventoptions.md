# ArkUI_VisibleAreaEventOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-23T07:09:16.631Z pushedAt=2026-11-25T01:18:27.341Z nl=1 -->

```c
typedef struct ArkUI_VisibleAreaEventOptions ArkUI_VisibleAreaEventOptions
```

## Overview

Defines the options for visible area change listening, including the threshold array, expected update interval, and visible area calculation mode. This struct is suitable for scenarios where you need to listen for visible area changes of a component and trigger updates at specified thresholds.

Before using this struct type, you need to call [OH_ArkUI_VisibleAreaEventOptions_Create](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_create) to create an **ArkUI_VisibleAreaEventOptions** object. Then, you can configure listening behavior using the following APIs:

Use [OH_ArkUI_VisibleAreaEventOptions_SetRatios](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setratios) to set a threshold array, which defines the threshold conditions for triggering visible area changes.

Use [OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) to set an expected update interval, which defines the minimum time interval between two visible area change notifications.

Use [OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setmeasurefromviewport) to set a calculation mode of a visible area, which defines whether to calculate the visible ratio from the viewport area.

To obtain the parameter values that have been set, you can:

Use [OH_ArkUI_VisibleAreaEventOptions_GetRatios](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getratios) to obtain the threshold array.

Use [OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getexpectedupdateinterval) to obtain the expected update interval.

Use [OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getmeasurefromviewport) to obtain the visible area calculation mode.

After using the object, call [OH_ArkUI_VisibleAreaEventOptions_Dispose](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_dispose) to dispose of the resources.

**Since**: 17

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_attributes.h](capi-common-attributes-h.md)
