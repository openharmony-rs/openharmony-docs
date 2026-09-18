# ComponentInfo

Implements a **ComponentInfo** object, which provides the size, position, translation, scaling, rotation, and affine matrix information of the component.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## localOffset

```TypeScript
localOffset: Offset
```

Offset of the component relative to the parent component.

**Type:** [Offset](arkts-arkui-componentutils-offset-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate: RotateResult
```

Rotation of the component.

**Type:** [RotateResult](arkts-arkui-componentutils-rotateresult-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale: ScaleResult
```

Scaling of the component.

**Type:** [ScaleResult](arkts-arkui-componentutils-scaleresult-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenOffset

```TypeScript
screenOffset: Offset
```

Offset of the component relative to the screen.

**Type:** [Offset](arkts-arkui-componentutils-offset-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: Size
```

Component size.

**Type:** Size

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transform

```TypeScript
transform: Matrix4Result
```

Affine matrix of the component, which is a 4x4 matrix object created based on the input parameter.

**Type:** [Matrix4Result](arkts-arkui-componentutils-matrix4result-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translate

```TypeScript
translate: TranslateResult
```

Translation of the component.

**Type:** [TranslateResult](arkts-arkui-componentutils-translateresult-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowOffset

```TypeScript
windowOffset: Offset
```

Offset of the component relative to the window.

**Type:** [Offset](arkts-arkui-componentutils-offset-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
