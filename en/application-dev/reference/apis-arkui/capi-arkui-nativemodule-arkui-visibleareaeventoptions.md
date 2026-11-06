# ArkUI_VisibleAreaEventOptions

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-21T01:45:43.237Z pushedAt=2026-08-21T03:32:32.918Z -->

```c
typedef struct ArkUI_VisibleAreaEventOptions ArkUI_VisibleAreaEventOptions
```

## Overview

Defines the options for visible area change listening, including the threshold array, expected update interval, and visible area calculation mode. This struct can be used to load or release resources based on the visible ratio of a component, and is suitable for scenarios where you need to listen for visible area changes of a component and trigger updates at specified thresholds.

When using this struct, you need to first call [OH_ArkUI_VisibleAreaEventOptions_Create](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_create) to create an **ArkUI_VisibleAreaEventOptions** parameter object. After the object is created, you can configure the listening behavior through the following APIs:

Use [OH_ArkUI_VisibleAreaEventOptions_SetRatios](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setratios) to set a threshold array, which defines the threshold conditions for triggering visible area changes.

Use [OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) to set an expected update interval, which defines the minimum time interval between two visible area change notifications.

Use [OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setmeasurefromviewport) to set a calculation mode of a visible area, which defines whether to calculate the visible ratio from the viewport area.

To obtain the parameter values that have been set, you can:

Use [OH_ArkUI_VisibleAreaEventOptions_GetRatios](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getratios) to obtain the threshold array.

Use [OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getexpectedupdateinterval) to obtain the expected update interval.

Use [OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getmeasurefromviewport) to obtain the visible area calculation mode.

When the **ArkUI_VisibleAreaEventOptions** object is no longer needed, call [OH_ArkUI_VisibleAreaEventOptions_Dispose](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_dispose) to release resources.

**Since**: 17

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_attributes.h](capi-common-attributes-h.md)