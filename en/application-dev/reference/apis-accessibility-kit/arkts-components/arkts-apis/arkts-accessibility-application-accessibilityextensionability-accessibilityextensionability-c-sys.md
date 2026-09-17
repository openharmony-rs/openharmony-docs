# AccessibilityExtensionAbility

AccessibilityExtensionAbility provides accessibility extension capabilities based on the ExtensionAbility framework, including connecting to and disconnecting from accessibility services, processing accessibility events, and processing accessibility key events.

**Lifecycle flow:** onAccessibilityConnect (connection callback, used for initialization) → onAccessibilityEventInfo/onAccessibilityKeyEvent (processing accessibility events and key events) → onAccessibilityDisconnect (disconnection callback, used for resource reclamation).

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## Modules to Import

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, ElementAttributeKeys, ElementAttributeValues, FocusDirection, FocusType, Rect, WindowType, AccessibilityEvent, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
```

## onAccessibilityConnect

```TypeScript
onAccessibilityConnect(): void
```

Callback invoked when the accessibility service is successfully connected.

When the user enables AccessibilityExtensionAbility, the system service calls this API after the connection is established to notify the ability that it has been successfully connected. You can implement service logic initialization in this method. This API can be overridden as required.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

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

Callback invoked when the accessibility service is successfully disconnected.

When the user disables AccessibilityExtensionAbility, the system service calls this API after the disconnection is completed. You can implement resource reclamation and service exit operations in this method. This API can be overridden as required.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

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

When an accessibility event occurs, the system distributes the event to the connected AccessibilityExtensionAbility and calls this API. You can process service logic based on the event information. This API usually needs to be overridden. For details about event types, see [AccessibilityEventType](arkts-accessibility-accessibility-accessibilityeventtype-e-sys.md).

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [AccessibilityEventInfo](arkts-accessibility-application-accessibilityextensionability-accessibilityeventinfo-i-sys.md) | Yes | Accessibility event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

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

Called when a key is pressed. You can determine whether to consume the event based on the service logic in this method. This API can be overridden as required.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyEvent | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | Yes | Key event. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the event is consumed and will not be propagated.<br>The value **false** indicates that the event is not consumed and will continue to be propagated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

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
