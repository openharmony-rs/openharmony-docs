# GetStatusOptions

包含接口调用选项的对象，包括成功、失败和完成回调函数。

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export interface GetStatusOptions--><!--Device-unnamed-export interface GetStatusOptions-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## 导入模块

```TypeScript
import { Battery, BatteryResponse, GetStatusOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数，无论接口调用成功或失败都会执行。当需要在接口调用完成后执行清理或通知操作时传入此回调。不传入时无结束通知。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 6

<!--Device-GetStatusOptions-complete?: () => void--><!--Device-GetStatusOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 6

<!--Device-GetStatusOptions-fail?: (data: string, code: number) => void--><!--Device-GetStatusOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## success

```TypeScript
success?: (data: BatteryResponse) => void
```

接口调用成功的回调函数，data为[BatteryResponse](arkts-basicservices-system-battery-batteryresponse-i.md)类型的返回值。

**类型：** (data: BatteryResponse) =&gt; void

**起始版本：** 3

**废弃版本：** 6

<!--Device-GetStatusOptions-success?: (data: BatteryResponse) => void--><!--Device-GetStatusOptions-success?: (data: BatteryResponse) => void-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

