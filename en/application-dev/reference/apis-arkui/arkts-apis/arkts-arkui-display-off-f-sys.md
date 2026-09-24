# off (System API)

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## off('privateModeChange')

```TypeScript
function off(type: 'privateModeChange', callback?: Callback<boolean>): void
```

Unsubscribes from privacy mode changes of this display.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'privateModeChange' | Yes | Event type. The value is fixed at **'privateModeChange'**, indicating that the privacy mode of the display is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to return whether the privacy mode of the display is changed. **true** if changed, **false** otherwise. If this parameter is not specified, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
try {
  // Unregister the callback for listening to privacy mode changes.
  display.off('privateModeChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Code: ${exception.code}, message: ${exception.message}`);
}
```
