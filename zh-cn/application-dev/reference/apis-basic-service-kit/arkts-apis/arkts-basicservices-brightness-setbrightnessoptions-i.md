# SetBrightnessOptions

设置屏幕亮度的参数对象。

**起始版本：** 3

**废弃版本：** 7

<!--Device-unnamed-export interface SetBrightnessOptions--><!--Device-unnamed-export interface SetBrightnessOptions-End-->

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

**类型：** () => void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessOptions-complete?: () => void--><!--Device-SetBrightnessOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) => void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessOptions-fail?: (data: string, code: number) => void--><!--Device-SetBrightnessOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessOptions-success?: () => void--><!--Device-SetBrightnessOptions-success?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## value

```TypeScript
value: number
```

屏幕亮度，值为1-255之间的整数。

- 如果值小于等于0，系统按1处理。

- 如果值大于255，系统按255处理。

- 如果值为小数，系统将处理为整数。例如设置为8.1，系统按8处理。

**类型：** number

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetBrightnessOptions-value: number--><!--Device-SetBrightnessOptions-value: number-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

