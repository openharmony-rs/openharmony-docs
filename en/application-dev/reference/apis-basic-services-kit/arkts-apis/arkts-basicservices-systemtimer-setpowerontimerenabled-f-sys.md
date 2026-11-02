# setPowerOnTimerEnabled (System API)

## Modules to Import

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

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-systemTimer-function setPowerOnTimerEnabled(options?: PowerOnTimerEnabledOptions): Promise<void>--><!--Device-systemTimer-function setPowerOnTimerEnabled(options?: PowerOnTimerEnabledOptions): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PowerOnTimerEnabledOptions](arkts-basicservices-systemtimer-powerontimerenabledoptions-i-sys.md) | No | Options for enabling or disabling the power-on timer, including the matching conditions and the enabled state. See [PowerOnTimerEnabledOptions](arkts-basicservices-systemtimer-powerontimerenabledoptions-i-sys.md). If this parameter is not specified, all power-on timers are enabled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
