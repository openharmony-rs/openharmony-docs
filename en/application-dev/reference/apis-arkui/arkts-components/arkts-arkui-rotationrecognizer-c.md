# RotationRecognizer

Implements a rotation gesture recognizer. Inherits from [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md).

**Inheritance/Implementation:** RotationRecognizer extends [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getAngle

```TypeScript
getAngle(): number
```

Obtains the minimum angle change required for the rotation gesture to be recognized.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum angle change required for the rotation gesture to be recognized, in degrees (deg).<br>Value range: [0, +∞) <br>**NOTE:** <br>If the provided angle is less than or equal to 0 or greater than 360, it is converted to the default value **1**. |
