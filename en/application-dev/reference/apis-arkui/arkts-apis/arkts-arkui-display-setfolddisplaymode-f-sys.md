# setFoldDisplayMode (System API)

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## setFoldDisplayMode

```TypeScript
function setFoldDisplayMode(mode: FoldDisplayMode): void
```

Sets the display mode of the foldable device.

**Since:** 10

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md) | Yes | Display mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_FULL;
  // Set the display mode to full-screen display.
  display.setFoldDisplayMode(mode);
} catch (exception) {
  console.error(`Failed to change the fold display mode. Code: ${exception.code}, message: ${exception.message}`);
}
```

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_MAIN;
  // Set the display mode to main screen display and specify the reason as "backSelfie".
  display.setFoldDisplayMode(mode, 'backSelfie');
} catch (exception) {
  console.error(`Failed to change the fold display mode. Code: ${exception.code}, message: ${exception.message}`);
}
```


## setFoldDisplayMode

```TypeScript
function setFoldDisplayMode(mode: FoldDisplayMode, reason: string): void
```

Sets the display mode of the foldable device, with the reason for the change specified.

**Since:** 19

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md) | Yes | Display mode. |
| reason | string | Yes | Reason for changing the display mode. If this parameter is not set, an empty string is used by default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

See [setFoldDisplayMode](#setfolddisplaymode)
