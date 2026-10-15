# ArkUI_VisibleAreaEventOptions

```c
typedef struct ArkUI_VisibleAreaEventOptions ArkUI_VisibleAreaEventOptions
```

## Overview

Defines the options for visible area change listening, including the threshold array, expected update interval, and visible area calculation mode. This struct can be used to load or release resources based on the visible ratio of a component, and is suitable for scenarios where you need to listen for visible area changes of a component and trigger updates at specified thresholds.<br> When using this struct, you need to first call [OH_ArkUI_VisibleAreaEventOptions_Create](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_create) to create an **ArkUI_VisibleAreaEventOptions** parameter object. After the object is created, you can configure the listening behavior through the following APIs:<br> Use [OH_ArkUI_VisibleAreaEventOptions_SetRatios](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setratios) to set a threshold array, which defines the threshold conditions for triggering visible area changes.<br> Use [OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) to set an expected update interval, which defines the minimum time interval between two visible area change notifications.<br> Use [OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_setmeasurefromviewport) to set a calculation mode of a visible area, which defines whether to calculate the visible ratio from the viewport area.<br> To obtain the parameter values that have been set, you can:<br> Use [OH_ArkUI_VisibleAreaEventOptions_GetRatios](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getratios) to obtain the threshold array.<br> Use [OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getexpectedupdateinterval) to obtain the expected update interval.<br> Use [OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_getmeasurefromviewport) to obtain the visible area calculation mode.<br> When the **ArkUI_VisibleAreaEventOptions** object is no longer needed, call [OH_ArkUI_VisibleAreaEventOptions_Dispose](capi-common-attributes-h.md#oh_arkui_visibleareaeventoptions_dispose) to release resources.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 17

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_attributes.h](capi-common-attributes-h.md)

