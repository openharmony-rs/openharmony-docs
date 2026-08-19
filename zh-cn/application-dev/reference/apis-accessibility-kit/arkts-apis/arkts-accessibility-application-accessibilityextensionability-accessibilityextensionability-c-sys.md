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

## onAccessibilityConnect

```TypeScript
onAccessibilityConnect(): void
```

连接无障碍服务成功后的回调函数。 用户启用AccessibilityExtensionAbility时，系统服务完成连接后回调该接口，通知Ability已成功连接。开发者可在该方法中完成初始化业务逻辑操作，该方法可选择性重写。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionAbility-onAccessibilityConnect(): void--><!--Device-AccessibilityExtensionAbility-onAccessibilityConnect(): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityConnect(): void {
    console.info('AxExtensionAbility onAccessibilityConnect');
  }
}
```

## onAccessibilityDisconnect

```TypeScript
onAccessibilityDisconnect(): void
```

断开无障碍服务成功后的回调函数。 用户停用AccessibilityExtensionAbility时，系统服务完成断开连接后回调该接口，可在该方法中执行资源回收和退出业务操作。该方法可选择性重写。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionAbility-onAccessibilityDisconnect(): void--><!--Device-AccessibilityExtensionAbility-onAccessibilityDisconnect(): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityDisconnect(): void {
    console.info('AxExtensionAbility onAccessibilityDisconnect');
  }
}
```

## onAccessibilityEventInfo

```TypeScript
onAccessibilityEventInfo(event: AccessibilityEventInfo): void
```

当无障碍事件发生时，系统将事件分发至已连接的AccessibilityExtensionAbility并回调该接口，可根据事件信息处理业务逻辑。通常需要重写。事件类型的详细说明请参见 [AccessibilityEventType](arkts-accessibility-accessibility-accessibilityeventtype-e-sys.md)。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionAbility-onAccessibilityEventInfo(event: AccessibilityEventInfo): void--><!--Device-AccessibilityExtensionAbility-onAccessibilityEventInfo(event: AccessibilityEventInfo): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [AccessibilityEventInfo](arkts-accessibility-application-accessibilityextensionability-accessibilityeventinfo-i-sys.md) | 是 | 无障碍事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityEventInfo, AccessibilityEventType } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityEventInfo(event: AccessibilityEventInfo): void {
    console.info('AxExtensionAbility onAccessibilityEventInfo');
    if (event.eventType === AccessibilityEventType.TYPE_CLICK) {
      console.info('AxExtensionAbility onAccessibilityEventInfo: click');
    }
  }
}
```

## onAccessibilityKeyEvent

```TypeScript
onAccessibilityKeyEvent(keyEvent: KeyEvent): boolean
```

在按键按下时回调该接口，可在该方法中根据业务判断是否消费事件。该方法可选择性重写。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionAbility-onAccessibilityKeyEvent(keyEvent: KeyEvent): boolean--><!--Device-AccessibilityExtensionAbility-onAccessibilityKeyEvent(keyEvent: KeyEvent): boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyEvent | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | 是 | 按键事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示此事件被消费，不会继续传递。 <br>返回false表示此事件未被消费，会继续传递。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';
import { KeyEvent, KeyCode } from '@kit.InputKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityKeyEvent(keyEvent: KeyEvent): boolean {
    console.info('AxExtensionAbility onAccessibilityKeyEvent');
    if (keyEvent.key.code === KeyCode.KEYCODE_VOLUME_UP) {
      console.info('AxExtensionAbility onAccessibilityKeyEvent: intercept 16');
      return true;
    }
    return false;
  }
}
```

