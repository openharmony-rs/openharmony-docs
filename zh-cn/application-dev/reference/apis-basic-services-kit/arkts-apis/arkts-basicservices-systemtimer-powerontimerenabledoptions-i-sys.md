# PowerOnTimerEnabledOptions（系统接口）

```TypeScript
interface PowerOnTimerEnabledOptions
```

Defines the options for [setPowerOnTimerEnabled](arkts-basicservices-systemtimer-setpowerontimerenabled-f-sys.md).

**起始版本：** 26.2.0

<!--Device-systemTimer-interface PowerOnTimerEnabledOptions--><!--Device-systemTimer-interface PowerOnTimerEnabledOptions-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { systemTimer } from '@kit.BasicServicesKit';
```

## enable

```TypeScript
enable?: boolean
```

Whether to enable the power-on timer. The value **true** means to add the timer back to the power-on timer list, and **false** means to remove the timer from the power-on timer list. If this parameter is not specified, the default value is **true**.

**类型：** boolean

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PowerOnTimerEnabledOptions-enable?: boolean--><!--Device-PowerOnTimerEnabledOptions-enable?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## timerName

```TypeScript
timerName?: string
```

Timer name. The value cannot be an empty string, and the maximum length is 64 bytes. If this parameter is not specified, the operation applies to all power-on timers.

**类型：** string

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PowerOnTimerEnabledOptions-timerName?: string--><!--Device-PowerOnTimerEnabledOptions-timerName?: string-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。
