# GetBrightnessOptions

获取屏幕亮度的参数对象。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-unnamed-export interface GetBrightnessOptions--><!--Device-unnamed-export interface GetBrightnessOptions-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-GetBrightnessOptions-complete?: () => void--><!--Device-GetBrightnessOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-GetBrightnessOptions-fail?: (data: string, code: number) => void--><!--Device-GetBrightnessOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## success

```TypeScript
success?: (data: BrightnessResponse) => void
```

接口调用成功的回调函数。data为[BrightnessResponse]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型的返回值。

**类型：** (data: BrightnessResponse) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-GetBrightnessOptions-success?: (data: BrightnessResponse) => void--><!--Device-GetBrightnessOptions-success?: (data: BrightnessResponse) => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

