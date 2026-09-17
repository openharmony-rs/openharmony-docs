# InputDeviceData

Provides information about an input device.

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## axisRanges

```TypeScript
axisRanges: Array<AxisRange>
```

Axis information of the input device.

**Type:** Array&lt;[AxisRange](arkts-input-inputdevice-axisrange-i.md)&gt;

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## bus

```TypeScript
bus: number
```

Bus type of the input device. By default, the bus type reported by the input device prevails.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## displayId

```TypeScript
displayId?: number
```

Indicates the bound target displayId.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## id

```TypeScript
id: number
```

Unique ID of the input device. If a physical device is repeatedly plugged and unplugged, its ID may change.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## isLocal

```TypeScript
isLocal?: boolean
```

Whether the input device is a local device.

The value **true** indicates that the device is a local device, and the value **false** indicates that the device is a non-local device.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## isVirtual

```TypeScript
isVirtual?: boolean
```

Whether the input device is a virtual device.

The value **true** indicates that the device is a virtual device, and the value **false** indicates that the device is a non-virtual device.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## name

```TypeScript
name: string
```

Name of the input device.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## phys

```TypeScript
phys: string
```

Physical address of the input device.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## product

```TypeScript
product: number
```

Product information of the input device.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## sources

```TypeScript
sources: Array<SourceType>
```

Input sources supported by the input device, including the keyboard, mouse, touchscreen, trackball, touchpad, and joystick.

**Type:** Array&lt;[SourceType](arkts-input-inputdevice-sourcetype-t.md)&gt;

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## uniq

```TypeScript
uniq: string
```

Unique ID of the input device.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## vendor

```TypeScript
vendor: number
```

Vendor information of the input device.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## version

```TypeScript
version: number
```

Version information of the input device.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice
