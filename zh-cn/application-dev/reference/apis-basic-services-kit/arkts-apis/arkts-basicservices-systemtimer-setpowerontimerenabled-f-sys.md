# setPowerOnTimerEnabled（系统接口）

## 导入模块

```TypeScript
import { systemTimer } from '@kit.BasicServicesKit';
```

## setPowerOnTimerEnabled

```TypeScript
function setPowerOnTimerEnabled(options?: PowerOnTimerEnabledOptions): Promise<void>
```

Sets the enabled state of the power-on timers that match the conditions specified in **options**. This API uses a promise to return the result.

The matching conditions and enabled state are specified through [PowerOnTimerEnabledOptions](arkts-basicservices-systemtimer-powerontimerenabledoptions-i-sys.md). When the enabled state is set to **false**, the matching power-on timers will no longer be triggered at device power-on, but the timers themselves are not deleted. When the enabled state is set to **true**, the matching power-on timers will be triggered at device power-on again. Only timers that meet the power-on timer conditions are restored.

> **NOTE:** 
> The enabled state set by this API is valid only during the current device run. After the device is restarted,
> the enabled state needs to be set again.

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemTimer-function setPowerOnTimerEnabled(options?: PowerOnTimerEnabledOptions): Promise<void>--><!--Device-systemTimer-function setPowerOnTimerEnabled(options?: PowerOnTimerEnabledOptions): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PowerOnTimerEnabledOptions](arkts-basicservices-systemtimer-powerontimerenabledoptions-i-sys.md) | 否 | Options for enabling or disabling the power-on timer, including the matching conditions and the enabled state. See [PowerOnTimerEnabledOptions](arkts-basicservices-systemtimer-powerontimerenabledoptions-i-sys.md). If this parameter is not specified, all power-on timers are enabled. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
