# InputDeviceData

描述输入设备的信息。

**起始版本：** 8

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## axisRanges

```TypeScript
axisRanges: Array<AxisRange>
```

输入设备的轴信息。

**类型：** Array<AxisRange>

**起始版本：** 8

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## bus

```TypeScript
bus: number
```

输入设备的总线类型，该值以输入设备上报为准。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## id

```TypeScript
id: number
```

输入设备的唯一标识，同一个物理设备反复插拔，设备ID可能会发生变化。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## isLocal

```TypeScript
isLocal?: boolean
```

输入设备是否为本地设备。

true表示是本地设备，false表示是非本地设备。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## isVirtual

```TypeScript
isVirtual?: boolean
```

输入设备是否为虚拟设备。

true表示是虚拟设备，false表示是非虚拟设备。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## name

```TypeScript
name: string
```

输入设备的名称。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## phys

```TypeScript
phys: string
```

输入设备的物理地址。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## product

```TypeScript
product: number
```

输入设备的产品信息。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## sources

```TypeScript
sources: Array<SourceType>
```

输入设备的输入能力。包括键盘、鼠标、触摸屏、轨迹球、触控板、操纵杆等。

**类型：** Array<SourceType>

**起始版本：** 8

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## uniq

```TypeScript
uniq: string
```

输入设备的唯一标识。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## vendor

```TypeScript
vendor: number
```

输入设备的厂商信息。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## version

```TypeScript
version: number
```

输入设备的版本信息。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

