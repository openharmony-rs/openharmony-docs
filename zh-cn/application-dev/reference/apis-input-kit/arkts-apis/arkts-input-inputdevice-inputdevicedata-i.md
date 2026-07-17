# InputDeviceData

描述输入设备的信息。

**起始版本：** 8

<!--Device-inputDevice-interface InputDeviceData--><!--Device-inputDevice-interface InputDeviceData-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## axisRanges

```TypeScript
axisRanges: Array<AxisRange>
```

输入设备的轴信息。

**类型：** Array<AxisRange>

**起始版本：** 8

<!--Device-InputDeviceData-axisRanges: Array<AxisRange>--><!--Device-InputDeviceData-axisRanges: Array<AxisRange>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## bus

```TypeScript
bus: number
```

输入设备的总线类型，该值以输入设备上报为准。

**类型：** number

**起始版本：** 9

<!--Device-InputDeviceData-bus: int--><!--Device-InputDeviceData-bus: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## id

```TypeScript
id: number
```

输入设备的唯一标识，同一个物理设备反复插拔，设备ID可能会发生变化。

**类型：** number

**起始版本：** 8

<!--Device-InputDeviceData-id: int--><!--Device-InputDeviceData-id: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## isLocal

```TypeScript
isLocal?: boolean
```

输入设备是否为本地设备。

true表示是本地设备，false表示是非本地设备。

**类型：** boolean

**起始版本：** 23

<!--Device-InputDeviceData-isLocal?: boolean--><!--Device-InputDeviceData-isLocal?: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## isVirtual

```TypeScript
isVirtual?: boolean
```

输入设备是否为虚拟设备。

true表示是虚拟设备，false表示是非虚拟设备。

**类型：** boolean

**起始版本：** 23

<!--Device-InputDeviceData-isVirtual?: boolean--><!--Device-InputDeviceData-isVirtual?: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## name

```TypeScript
name: string
```

输入设备的名称。

**类型：** string

**起始版本：** 8

<!--Device-InputDeviceData-name: string--><!--Device-InputDeviceData-name: string-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## phys

```TypeScript
phys: string
```

输入设备的物理地址。

**类型：** string

**起始版本：** 9

<!--Device-InputDeviceData-phys: string--><!--Device-InputDeviceData-phys: string-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## product

```TypeScript
product: number
```

输入设备的产品信息。

**类型：** number

**起始版本：** 9

<!--Device-InputDeviceData-product: int--><!--Device-InputDeviceData-product: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## sources

```TypeScript
sources: Array<SourceType>
```

输入设备的输入能力。包括键盘、鼠标、触摸屏、轨迹球、触控板、操纵杆等。

**类型：** Array<SourceType>

**起始版本：** 8

<!--Device-InputDeviceData-sources: Array<SourceType>--><!--Device-InputDeviceData-sources: Array<SourceType>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## uniq

```TypeScript
uniq: string
```

输入设备的唯一标识。

**类型：** string

**起始版本：** 9

<!--Device-InputDeviceData-uniq: string--><!--Device-InputDeviceData-uniq: string-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## vendor

```TypeScript
vendor: number
```

输入设备的厂商信息。

**类型：** number

**起始版本：** 9

<!--Device-InputDeviceData-vendor: int--><!--Device-InputDeviceData-vendor: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## version

```TypeScript
version: number
```

输入设备的版本信息。

**类型：** number

**起始版本：** 9

<!--Device-InputDeviceData-version: int--><!--Device-InputDeviceData-version: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

