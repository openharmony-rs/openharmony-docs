# GetBrightnessModeOptions

获取屏幕亮度模式的参数对象。

**起始版本：** 3

**废弃版本：** 7

<!--Device-unnamed-export interface GetBrightnessModeOptions--><!--Device-unnamed-export interface GetBrightnessModeOptions-End-->

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

<!--Device-GetBrightnessModeOptions-complete?: () => void--><!--Device-GetBrightnessModeOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-GetBrightnessModeOptions-fail?: (data: string, code: number) => void--><!--Device-GetBrightnessModeOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## success

```TypeScript
success?: (data: BrightnessModeResponse) => void
```

接口调用成功的回调函数。data为[BrightnessModeResponse](arkts-basicservices-brightness-brightnessmoderesponse-i.md)类型的返回值。

**类型：** (data: BrightnessModeResponse) =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-GetBrightnessModeOptions-success?: (data: BrightnessModeResponse) => void--><!--Device-GetBrightnessModeOptions-success?: (data: BrightnessModeResponse) => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

