# startBlinking (System API)

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## startBlinking

```TypeScript
function startBlinking(mode: BlinkingMode, scenario: BlinkingScenario): BlinkResultCode
```

Enables the flash or screen for blinking reminders.

**Since:** 26.0.0

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [BlinkingMode](arkts-accessibility-config-blinkingmode-e-sys.md) | Yes | Blinking mode, indicating screen blinking or flash blinking. |
| scenario | [BlinkingScenario](arkts-accessibility-config-blinkingscenario-e-sys.md) | Yes | Scenario that triggers blinking. |

**Return value:**

| Type | Description |
| --- | --- |
| [BlinkResultCode](arkts-accessibility-config-blinkresultcode-e-sys.md) | Result code returned by the API call. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed.<br>A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality.Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.IPC communication failed. <br>4.Failed to obtain the accessibility service proxy. |

**Examples**

```TypeScript
import { config } from '@kit.AccessibilityKit';

try {
  let code: config.BlinkResultCode = config.startBlinking(config.BlinkingMode.SINGLE_BLINK, config.BlinkingScenario.ALARM);
  console.info(`Succeeded in startBlinking, result code: ${code}`);
} catch (err) {
  console.error(`Failed to call startBlinking, code is ${err.code}, message is ${err.message}`);
}
```
