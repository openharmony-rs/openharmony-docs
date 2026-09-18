# setFoldStatusLocked (System API)

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## setFoldStatusLocked

```TypeScript
function setFoldStatusLocked(locked: boolean): void
```

Sets whether to lock the current fold status of the foldable device.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locked | boolean | Yes | Whether to lock the current fold status of the foldable device. **true** to lock, **false** otherwise. |

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
  let locked: boolean = false;
  // Set the fold status to not locked.
  display.setFoldStatusLocked(locked);
} catch (exception) {
  console.error(`Failed to change the fold status locked mode. Code: ${exception.code}, message: ${exception.message}`);
}
```
