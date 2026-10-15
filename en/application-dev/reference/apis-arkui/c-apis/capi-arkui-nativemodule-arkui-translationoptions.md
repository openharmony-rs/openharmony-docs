# ArkUI_TranslationOptions

```c
typedef struct ArkUI_TranslationOptions {...} ArkUI_TranslationOptions
```

## Overview

Defines the translation options for component transition, used to set the translation distance of a component in the x, y, and z directions during the transition.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type_visual.h](capi-native-type-visual-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float x | X-axis translation distance, in vp. Value principles: A positive value indicates translation to the right, a negative value indicates translation to the left, and **0** indicates no translation. Default value: **0**. |
| float y | Y-axis translation distance, in vp. Value principles: A positive value indicates translation downward, a negative value indicates translation upward, and **0** indicates no translation. Default value: **0**. |
| float z | Z-axis translation distance, in vp. Value principles: A positive value indicates translation toward the observer, a negative value indicates translation away from the observer, and **0** indicates no translation. When moving along the z-axis, since the observation point remains unchanged, the component will be scaled up as the value of **z** approaches the observation point and scaled in as it moves away. Default value: **0**. |


