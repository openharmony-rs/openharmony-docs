# AccessibilityExtensionAbility

AccessibilityExtensionAbility基于ExtensionAbility框架，提供辅助功能扩展业务的能力。

**起始版本：** 23

<!--Device-unnamed-declare class AccessibilityExtensionAbility--><!--Device-unnamed-declare class AccessibilityExtensionAbility-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, ElementAttributeKeys, ElementAttributeValues, FocusDirection, FocusType, Rect, WindowType, AccessibilityEvent, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, FocusDirection, Rect, WindowType, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
```

## onAccessibilityEvent

```TypeScript
onAccessibilityEvent(event: AccessibilityEvent): void
```

当无障碍事件发生时回调此接口，可在该方法中根据事件信息进行业务逻辑处理。通常需要重写该方法。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityExtensionAbility-onAccessibilityEvent(event: AccessibilityEvent): void--><!--Device-AccessibilityExtensionAbility-onAccessibilityEvent(event: AccessibilityEvent): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [AccessibilityEvent](arkts-accessibility-application-accessibilityextensionability-accessibilityevent-i.md) | 是 | 无障碍事件信息。 |

**示例**

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityEvent } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityEvent(event: AccessibilityEvent): void {
    console.info('AxExtensionAbility onAccessibilityEvent');
    if (event.eventType === 'click') {
      console.info('AxExtensionAbility onAccessibilityEvent: click');
    }
  }
}
```

## onConnect

```TypeScript
onConnect(): void
```

用户启用AccessibilityExtensionAbility时，系统服务完成连接后回调此接口，可在该方法中执行初始化业务逻辑操作。该方法可选择性重写。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityExtensionAbility-onConnect(): void--><!--Device-AccessibilityExtensionAbility-onConnect(): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**示例**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onConnect(): void {
    console.info('AxExtensionAbility onConnect');
  }
}
```

## onDisconnect

```TypeScript
onDisconnect(): void
```

用户停用AccessibilityExtensionAbility时，系统服务完成断开连接后回调此接口，可在该方法中执行资源回收和退出业务操作。该方法可选择性重写。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityExtensionAbility-onDisconnect(): void--><!--Device-AccessibilityExtensionAbility-onDisconnect(): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**示例**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onDisconnect(): void {
    console.info('AxExtensionAbility onDisconnect');
  }
}
```

## onKeyEvent

```TypeScript
onKeyEvent(keyEvent: KeyEvent): boolean
```

在按键按下时回调此接口，可在该方法中根据业务判断是否消费事件。该方法可选择性重写。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityExtensionAbility-onKeyEvent(keyEvent: KeyEvent): boolean--><!--Device-AccessibilityExtensionAbility-onKeyEvent(keyEvent: KeyEvent): boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyEvent | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | 是 | 按键事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示此事件被消费，不会继续传递。 <br>返回false表示此事件未被消费，会继续传递。 |

**示例**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';
import { KeyEvent } from '@kit.InputKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onKeyEvent(keyEvent: KeyEvent): boolean {
    console.info('AxExtensionAbility onKeyEvent');
    if (keyEvent.key.code === 16) {
      console.info('AxExtensionAbility onKeyEvent: intercept 16');
      return true;
    }
    return false;
  }
}
```

## context

```TypeScript
context: AccessibilityExtensionContext
```

表示辅助功能扩展的上下文环境。

**类型：** [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-t.md)

**起始版本：** 23

<!--Device-AccessibilityExtensionAbility-context: AccessibilityExtensionContext--><!--Device-AccessibilityExtensionAbility-context: AccessibilityExtensionContext-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

