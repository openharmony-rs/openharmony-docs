# offApplicationFocusStateChange

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## offApplicationFocusStateChange

```TypeScript
function offApplicationFocusStateChange(callback?: Callback<boolean>): void
```

Unregister the callback for application process focus state changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result whether application process focused or not. If not provided, all callbacks for the given event type will be removed. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

const callback = (bool: boolean) => {
  // ...
}
try {
  window.onApplicationFocusStateChange(callback);
  window.offApplicationFocusStateChange(callback);
  // Unregister all the callbacks that have been registered through on().
  window.offApplicationFocusStateChange(); 
} catch (exception) {
  console.error(`Failed to enable or disable the listener for application focus state changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
