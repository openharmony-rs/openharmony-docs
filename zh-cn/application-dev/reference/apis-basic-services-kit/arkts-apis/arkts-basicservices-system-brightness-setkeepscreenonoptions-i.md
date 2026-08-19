# SetKeepScreenOnOptions

设置屏幕常亮的参数对象。

**起始版本：** 3

**废弃版本：** 7

<!--Device-unnamed-export interface SetKeepScreenOnOptions--><!--Device-unnamed-export interface SetKeepScreenOnOptions-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## 导入模块

```TypeScript
import { Brightness, BrightnessModeResponse, BrightnessResponse, GetBrightnessModeOptions, GetBrightnessOptions, SetBrightnessModeOptions, SetBrightnessOptions, SetKeepScreenOnOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数，无论接口调用成功或失败都会执行。当需要在操作完成后执行清理或状态更新等逻辑时传入，不传入时不执行结束回调逻辑。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetKeepScreenOnOptions-complete?: () => void--><!--Device-SetKeepScreenOnOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetKeepScreenOnOptions-fail?: (data: string, code: number) => void--><!--Device-SetKeepScreenOnOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## keepScreenOn

```TypeScript
keepScreenOn: boolean
```

true表示保持屏幕常亮（仅阻止系统无活动超时灭屏，无法阻止用户主动操作或常亮时刻结束等导致的灭屏），false表示取消屏幕常亮。

**类型：** boolean

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetKeepScreenOnOptions-keepScreenOn: boolean--><!--Device-SetKeepScreenOnOptions-keepScreenOn: boolean-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 7

<!--Device-SetKeepScreenOnOptions-success?: () => void--><!--Device-SetKeepScreenOnOptions-success?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

