# registerHibernateCallback (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## registerHibernateCallback

```TypeScript
function registerHibernateCallback(callback: HibernateCallback): void
```

Registers a callback to be invoked when the device enters or exits hibernation.

**Since:** 26.1.0

**Required permissions:** ohos.permission.POWER_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-power-function registerHibernateCallback(callback: HibernateCallback): void--><!--Device-power-function registerHibernateCallback(callback: HibernateCallback): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [HibernateCallback](arkts-basicservices-power-hibernatecallback-i-sys.md) | Yes | Callback object containing onHibernate and onWakeup methods. onHibernate is called when entering hibernation (no parameters). onWakeup is called when exiting hibernation, with hibernateResult indicating whether the hibernation succeeded. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4900400](../errorcode-power.md#4900400-invalid-input-parameter) | Parameter error. Possible causes: The callback object is missing onHibernate or onWakeup function members. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
