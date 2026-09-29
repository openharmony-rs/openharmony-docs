# AxisRange

```TypeScript
interface AxisRange
```

Defines the axis range of an input device.

**Since:** 8

<!--Device-inputDevice-interface AxisRange--><!--Device-inputDevice-interface AxisRange-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## axis

```TypeScript
axis: AxisType
```

Axis type of an input device.

**Type:** [AxisType](arkts-input-inputdevice-axistype-t.md)

**Since:** 8

<!--Device-AxisRange-axis: AxisType--><!--Device-AxisRange-axis: AxisType-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## flat

```TypeScript
flat: number
```

Benchmark value of the axis.

**Type:** number

**Since:** 9

<!--Device-AxisRange-flat: int--><!--Device-AxisRange-flat: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## fuzz

```TypeScript
fuzz: number
```

Fuzzy value of the axis.

**Type:** number

**Since:** 9

<!--Device-AxisRange-fuzz: int--><!--Device-AxisRange-fuzz: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## max

```TypeScript
max: number
```

Maximum value of the axis.

**Type:** number

**Since:** 8

<!--Device-AxisRange-max: int--><!--Device-AxisRange-max: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## min

```TypeScript
min: number
```

Minimum value of the axis.

**Type:** number

**Since:** 8

<!--Device-AxisRange-min: int--><!--Device-AxisRange-min: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## resolution

```TypeScript
resolution: number
```

Resolution of the axis.

**Type:** number

**Since:** 9

<!--Device-AxisRange-resolution: int--><!--Device-AxisRange-resolution: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## source

```TypeScript
source: SourceType
```

Input sources supported by the input device, including the keyboard, mouse, touchscreen, trackball, touchpad, and joystick.

**Type:** [SourceType](arkts-input-inputdevice-sourcetype-t.md)

**Since:** 8

<!--Device-AxisRange-source: SourceType--><!--Device-AxisRange-source: SourceType-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice
