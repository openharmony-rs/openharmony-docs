# onApplicationFocusStateChange

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## onApplicationFocusStateChange

```TypeScript
function onApplicationFocusStateChange(callback: Callback<boolean>): void
```

Register the callback for application process focus state changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result whether application process focused or not. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

try {
  window.onApplicationFocusStateChange((data) =>{
      console.info(`Succeeded in enabling the listener for application focus state changes. Data: ${data}`);
  })
} catch(exception){
  console.error(`Failed to enable the listener for application focus state changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
