# PowerOnTimerEnabledOptions (System API)

```TypeScript
interface PowerOnTimerEnabledOptions
```

Defines the options for [setPowerOnTimerEnabled](arkts-basicservices-systemtimer-setpowerontimerenabled-f-sys.md).

**Since:** 26.1.0

<!--Device-systemTimer-interface PowerOnTimerEnabledOptions--><!--Device-systemTimer-interface PowerOnTimerEnabledOptions-End-->

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { systemTimer } from '@kit.BasicServicesKit';
```

## enable

```TypeScript
enable?: boolean
```

Whether to enable the power-on timer. The value **true** means to add the timer back to the power-on timer list, and **false** means to remove the timer from the power-on timer list. If this parameter is not specified, the default value is **true**.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PowerOnTimerEnabledOptions-enable?: boolean--><!--Device-PowerOnTimerEnabledOptions-enable?: boolean-End-->

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## timerName

```TypeScript
timerName?: string
```

Timer name. The value cannot be an empty string, and the maximum length is 64 bytes. If this parameter is not specified, the operation applies to all power-on timers.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PowerOnTimerEnabledOptions-timerName?: string--><!--Device-PowerOnTimerEnabledOptions-timerName?: string-End-->

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.
