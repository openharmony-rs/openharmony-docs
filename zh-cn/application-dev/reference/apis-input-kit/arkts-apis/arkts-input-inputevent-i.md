# InputEvent

设备上报的基本事件。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## actionTime

```TypeScript
actionTime: number
```

上报输入事件的时间，表示系统启动运行至今逝去的微秒数，单位为微秒（μs）。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## deviceId

```TypeScript
deviceId: number
```

输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## id

```TypeScript
id: number
```

事件ID。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenId

```TypeScript
screenId: number
```

目标屏幕ID。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowId

```TypeScript
windowId: number
```

目标窗口ID。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

