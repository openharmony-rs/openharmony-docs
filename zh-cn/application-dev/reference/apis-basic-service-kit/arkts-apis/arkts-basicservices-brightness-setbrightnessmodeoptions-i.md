# SetBrightnessModeOptions

设置屏幕亮度模式的参数对象。

**起始版本：** 3

**废弃版本：** 7

<!--Device-unnamed-export interface SetBrightnessModeOptions--><!--Device-unnamed-export interface SetBrightnessModeOptions-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## 导入模块

```TypeScript
import { BrightnessResponse, BrightnessModeResponse, SetBrightnessModeOptions, GetBrightnessModeOptions, SetBrightnessOptions, GetBrightnessOptions, SetKeepScreenOnOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessModeOptions-complete?: () => void--><!--Device-SetBrightnessModeOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessModeOptions-fail?: (data: string, code: number) => void--><!--Device-SetBrightnessModeOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## mode

```TypeScript
mode: number
```

0表示手动调节屏幕亮度模式，1表示自动调节屏幕亮度模式。

**类型：** number

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessModeOptions-mode: number--><!--Device-SetBrightnessModeOptions-mode: number-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessModeOptions-success?: () => void--><!--Device-SetBrightnessModeOptions-success?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

