# InputDeviceData

```TypeScript
interface InputDeviceData
```

Provides information about an input device.

**Since:** 8

<!--Device-inputDevice-interface InputDeviceData--><!--Device-inputDevice-interface InputDeviceData-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## axisRanges

```TypeScript
axisRanges: Array<AxisRange>
```

Axis range of the input device.

**Type:** Array&lt;[AxisRange](arkts-input-inputdevice-axisrange-i.md)&gt;

**Since:** 8

<!--Device-InputDeviceData-axisRanges: Array<AxisRange>--><!--Device-InputDeviceData-axisRanges: Array<AxisRange>-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## bus

```TypeScript
bus: number
```

Bus type of the input device. By default, the bus type reported by the input device prevails.

**Type:** number

**Since:** 9

<!--Device-InputDeviceData-bus: int--><!--Device-InputDeviceData-bus: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## displayId

```TypeScript
readonly displayId?: number
```

ID of the bound target display. This field exists when there is a binding relationship in the system, and does not exist when there is no binding.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputDeviceData-readonly displayId?: int--><!--Device-InputDeviceData-readonly displayId?: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## id

```TypeScript
id: number
```

Unique ID of the input device. If a physical device is repeatedly plugged and unplugged, its ID may change.

**Type:** number

**Since:** 8

<!--Device-InputDeviceData-id: int--><!--Device-InputDeviceData-id: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## isLocal

```TypeScript
isLocal?: boolean
```

Whether the input device is a local device.<br>The value **true** indicates a local device, and **false** indicates a non-local device. If this field does not exist, the default value is **false**.

**Type:** boolean

**Since:** 23

<!--Device-InputDeviceData-isLocal?: boolean--><!--Device-InputDeviceData-isLocal?: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## isVirtual

```TypeScript
isVirtual?: boolean
```

Whether the input device is a virtual device.<br>The value **true** indicates a virtual device, and **false** indicates a non-virtual device. If this field does not exist, the default value is **false**.

**Type:** boolean

**Since:** 23

<!--Device-InputDeviceData-isVirtual?: boolean--><!--Device-InputDeviceData-isVirtual?: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## name

```TypeScript
name: string
```

Name of the input device.

**Type:** string

**Since:** 8

<!--Device-InputDeviceData-name: string--><!--Device-InputDeviceData-name: string-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## phys

```TypeScript
phys: string
```

Physical address of the input device.

**Type:** string

**Since:** 9

<!--Device-InputDeviceData-phys: string--><!--Device-InputDeviceData-phys: string-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## product

```TypeScript
product: number
```

Product information of the input device.

**Type:** number

**Since:** 9

<!--Device-InputDeviceData-product: int--><!--Device-InputDeviceData-product: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## sources

```TypeScript
sources: Array<SourceType>
```

Input sources supported by the input device, including the keyboard, mouse, touchscreen, trackball, touchpad, and joystick.

**Type:** Array&lt;[SourceType](arkts-input-inputdevice-sourcetype-t.md)&gt;

**Since:** 8

<!--Device-InputDeviceData-sources: Array<SourceType>--><!--Device-InputDeviceData-sources: Array<SourceType>-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## uniq

```TypeScript
uniq: string
```

Unique ID of the input device.

**Type:** string

**Since:** 9

<!--Device-InputDeviceData-uniq: string--><!--Device-InputDeviceData-uniq: string-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## vendor

```TypeScript
vendor: number
```

Vendor information of the input device.

**Type:** number

**Since:** 9

<!--Device-InputDeviceData-vendor: int--><!--Device-InputDeviceData-vendor: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## version

```TypeScript
version: number
```

Version information of the input device.

**Type:** number

**Since:** 9

<!--Device-InputDeviceData-version: int--><!--Device-InputDeviceData-version: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice
