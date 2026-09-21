# AccessibilityExtensionContext

```TypeScript
export type AccessibilityExtensionContext = _AccessibilityExtensionContext.default
```

表示辅助功能扩展的上下文环境，请参考[AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c.md)。

**起始版本：** 10

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** _AccessibilityExtensionContext.default

**示例**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class EntryAbility extends AccessibilityExtensionAbility {
  onConnect(): void {
    let accessibilityContext = this.context;
  } 
}
```
