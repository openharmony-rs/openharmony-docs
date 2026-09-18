# showToast

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## showToast

```TypeScript
function showToast(options: ShowToastOptions): void
```

Displays the notification text.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** showToast

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowToastOptions](arkts-arkui-prompt-showtoastoptions-i.md) | Yes | Options. |

**Examples**

```TypeScript
import prompt from '@ohos.prompt'
prompt.showToast({
  message: 'Message Info',
  duration: 2000
});
```
