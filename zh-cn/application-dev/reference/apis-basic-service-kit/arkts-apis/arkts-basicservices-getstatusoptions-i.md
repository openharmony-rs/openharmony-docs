# GetStatusOptions

包含接口调用结果的对象。

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) => void

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## success

```TypeScript
success?: (data: BatteryResponse) => void
```

接口调用成功的回调函数，data为{@link BatteryResponse}类型的返回值。

**类型：** (data: BatteryResponse) => void

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

