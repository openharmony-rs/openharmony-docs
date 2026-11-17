# unregisterHibernateCallback (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## unregisterHibernateCallback

```TypeScript
function unregisterHibernateCallback(): void
```

Unregisters the callback invoked when the device enters or exits hibernation. All registered hibernation callbacks are removed.

**Since:** 26.1.0

**Required permissions:** ohos.permission.POWER_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-power-function unregisterHibernateCallback(): void--><!--Device-power-function unregisterHibernateCallback(): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
