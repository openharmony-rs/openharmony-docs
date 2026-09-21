# AccessibilityExtensionContext

```TypeScript
export type AccessibilityExtensionContext = _AccessibilityExtensionContext.default
```

Indicates the context of the accessibility extension. For details, see [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c.md).

**Since:** 10

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Type:** _AccessibilityExtensionContext.default

**Examples**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class EntryAbility extends AccessibilityExtensionAbility {
  onConnect(): void {
    let accessibilityContext = this.context;
  } 
}
```
