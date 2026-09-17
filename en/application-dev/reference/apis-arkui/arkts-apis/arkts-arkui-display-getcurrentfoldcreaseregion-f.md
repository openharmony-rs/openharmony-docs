# getCurrentFoldCreaseRegion

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getCurrentFoldCreaseRegion

```TypeScript
function getCurrentFoldCreaseRegion(): FoldCreaseRegion
```

Obtains the crease region of the foldable device in the current display mode.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [FoldCreaseRegion](arkts-arkui-display-foldcreaseregion-i.md) | Crease region of the device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
let data: display.FoldCreaseRegion = display.getCurrentFoldCreaseRegion();
console.info(`Succeeded in obtaining current fold crease region. Data: ${JSON.stringify(data)}`);
```
