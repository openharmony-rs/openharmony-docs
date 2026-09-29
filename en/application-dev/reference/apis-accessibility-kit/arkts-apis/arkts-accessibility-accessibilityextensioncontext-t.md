# AccessibilityExtensionContext

```TypeScript
export type AccessibilityExtensionContext = _AccessibilityExtensionContext.default
```

Indicates the context of the accessibility extension. For details, see [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c.md).

**Since:** 10

<!--Device-unnamed-export type AccessibilityExtensionContext = _AccessibilityExtensionContext.default--><!--Device-unnamed-export type AccessibilityExtensionContext = _AccessibilityExtensionContext.default-End-->

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
