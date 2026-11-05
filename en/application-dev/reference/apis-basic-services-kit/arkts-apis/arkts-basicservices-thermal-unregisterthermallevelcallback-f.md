# unregisterThermalLevelCallback

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## unregisterThermalLevelCallback

```TypeScript
function unregisterThermalLevelCallback(callback?: Callback<void>): void
```

Unsubscribe from the callback notification when the hot level changes. Use callback asynchronous callback. This method is used in conjunction with thermal.registerThermalLevelCallback, Used to cancel a previously registered hot gear callback. No error is reported when unsubscribing from an unregistered callback, and no operation is performed.

**Since:** 9

<!--Device-thermal-function unregisterThermalLevelCallback(callback?: Callback<void>): void--><!--Device-thermal-function unregisterThermalLevelCallback(callback?: Callback<void>): void-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback function. Notification callback after the deregistration is complete. No value is returned. This parameter is used only to receive notifications indicating that the subscription is canceled. This callback function is invoked when the subscription is canceled successfully. If this parameter is not transferred, the subscription cancellation still takes effect, but no callback notification is triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Examples**

```TypeScript
try {
    thermal.unregisterThermalLevelCallback(() => {
        console.info('unsubscribe thermal level success.');
    });
    console.info('unregister thermal level callback success.');
} catch(err) {
    console.error('unregister thermal level callback failed, err: ' + err);
}
```
