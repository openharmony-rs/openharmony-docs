# SetKeepScreenOnOptions

设置屏幕常亮的参数对象。

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

## keepScreenOn

```TypeScript
keepScreenOn: boolean
```

true表示保持屏幕常亮，false表示取消屏幕常亮。

**类型：** boolean

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

