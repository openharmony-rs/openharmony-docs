# setPowerKeyFilteringStrategy (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## setPowerKeyFilteringStrategy

```TypeScript
function setPowerKeyFilteringStrategy(strategy: PowerKeyFilteringStrategy): void
```

Sets the power key filtering strategy. After the power service subscribes to the power key event, this API is used to configure the processing mode of this event.

For details about the power key filtering strategy, see [power.PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md).

**Since:** 21

**Required permissions:** ohos.permission.POWER_MANAGER

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md) | Yes | Power key filtering strategy. The value must be of the enum type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
try {
    power.setPowerKeyFilteringStrategy(power.PowerKeyFilteringStrategy.LONG_PRESS_FILTERING_ONCE);
} catch(err) {
    console.error('setPowerKeyFilteringStrategy failed, err: ' + err);
}
```
