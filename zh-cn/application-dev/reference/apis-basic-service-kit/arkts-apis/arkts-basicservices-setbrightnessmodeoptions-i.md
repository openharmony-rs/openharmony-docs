# SetBrightnessModeOptions

设置屏幕亮度模式的参数对象。

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) => void

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## mode

```TypeScript
mode: number
```

0表示手动调节屏幕亮度模式，1表示自动调节屏幕亮度模式。

**类型：** number

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

