# isFoldable

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## isFoldable

```TypeScript
function isFoldable(): boolean
```

Checks whether this device is foldable.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the device is foldable. **true** if foldable, **false** otherwise. For small-screen foldable devices where the outer screen serves only as an auxiliary display (and cannot be customized by applications), the return value is always **false**. For other foldable devices, the return value is always **true**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
let ret: boolean = false;
ret = display.isFoldable();
```
