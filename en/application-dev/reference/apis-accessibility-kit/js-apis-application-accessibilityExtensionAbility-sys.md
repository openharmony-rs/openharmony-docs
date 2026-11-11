# @ohos.application.AccessibilityExtensionAbility (AccessibilityExtensionAbility) (System API)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @fanzexuan-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=bb39966feaa0eb2bb100f2870d5ac4317b98024f translatedAt=2026-11-06T08:13:06.694Z pushedAt=2026-11-09T09:19:26.550Z nl=1 -->

AccessibilityExtensionAbility provides accessibility extension capabilities based on the ExtensionAbility framework, including connecting to and disconnecting from accessibility services, processing accessibility events, and processing accessibility key events.

**Lifecycle flow:** onAccessibilityConnect (connection callback, used for initialization) → onAccessibilityEventInfo/onAccessibilityKeyEvent (processing accessibility events and key events) → onAccessibilityDisconnect (disconnection callback, used for resource reclamation).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module. For details about other public APIs, see [@ohos.application.AccessibilityExtensionAbility](js-apis-application-accessibilityExtensionAbility.md).

## Modules to Import

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';
```
## AccessibilityEventInfo

Describes the accessibility event information.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Properties

| Name                           | Type                                      | Read-Only  | Optional  | Description                                      |
| ----------------------------- | ---------------------------------------- | ---- | ---- | ---------------------------------------- |
| eventType                     | [AccessibilityEventType](js-apis-accessibility-sys.md#accessibilityeventtype) | No    | No    | Accessibility event type. |
| target                        | [AccessibilityElement](js-apis-inner-application-accessibilityExtensionContext-sys.md#accessibilityelement) | No    | Yes    | Target component where the event occurs. When the accessibility event involves a specific component, this property contains the component information. |
| timestamp                     | number                                   | No    | Yes    | Event timestamp, in milliseconds. The default value is 0. |
| extraInfo                     | string                                   | No    | Yes    | The default value is an empty string.<br>Additional event information, which is a JSON string. It is set based on the actual event scenario, and is an empty string when there is no corresponding information. It contains the following fields:<br>- addText: the specific text content added when text content is added.<br>- removeText: the specific text content removed when text content is deleted.<br>- beforeText: the text content before the text content changes.<br>- addedCount: the number of characters added to the text content.<br>- removedCount: the number of characters removed from the text content.<br>- startIndex: the index item before and after list scrolling, or the start index of the edit box.<br>- endIndex: the index item before and after list scrolling, or the end index of the edit box.<br>- scrollX: the horizontal scroll offset when a scroll event occurs, in pixels (px).<br>- scrollY: the vertical scroll offset when a scroll event occurs, in pixels (px).<br>- scrollSource: the trigger source of the scroll event.<br>- itemCounts: the total number of items in a list or page-turning component.<br>- currentIndex: the index of the current item in a list or page-turning component.<br>- candidateIds: the candidate focus IDs carried by the event when the focus is invisible.<br>- touchGuideGestureType: the type of the touch browsing gesture. |

## AccessibilityExtensionAbility

AccessibilityExtensionAbility provides accessibility extension capabilities based on the ExtensionAbility framework, including connecting to and disconnecting from accessibility services, processing accessibility events, and processing accessibility key events.

### onAccessibilityConnect

onAccessibilityConnect(): void

Callback invoked when the accessibility service is successfully connected.

When the user enables AccessibilityExtensionAbility, the system service calls this API after the connection is established to notify the ability that it has been successfully connected. You can implement service logic initialization in this method. This API can be overridden as required.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityConnect(): void {
    console.info('AxExtensionAbility onAccessibilityConnect');
  }
}
```

### onAccessibilityDisconnect

onAccessibilityDisconnect(): void

Callback invoked when the accessibility service is successfully disconnected.

When the user disables AccessibilityExtensionAbility, the system service calls this API after the disconnection is completed. You can implement resource reclamation and service exit operations in this method. This API can be overridden as required.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityDisconnect(): void {
    console.info('AxExtensionAbility onAccessibilityDisconnect');
  }
}
```

### onAccessibilityEventInfo

onAccessibilityEventInfo(event: AccessibilityEventInfo): void

When an accessibility event occurs, the system distributes the event to the connected AccessibilityExtensionAbility and calls this API. You can process service logic based on the event information. This API usually needs to be overridden. For details about event types, see [AccessibilityEventType](js-apis-accessibility-sys.md#accessibilityeventtype).

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                                      | Mandatory  | Description   |
| ----- | ---------------------------------------- | ---- | ----- |
| event | [AccessibilityEventInfo](#accessibilityeventinfo) | Yes | Accessibility event information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
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

### onAccessibilityKeyEvent

onAccessibilityKeyEvent(keyEvent: KeyEvent): boolean

Called when a key is pressed. You can determine whether to consume the event based on the service logic in this method. This API can be overridden as required.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description  |
| -------- | ---------------------------------------- | ---- | ---- |
| keyEvent | [KeyEvent](../apis-input-kit/js-apis-keyevent.md#keyevent) | Yes   | Key event.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | The value **true** indicates that the event is consumed and will not be propagated.<br>The value **false** indicates that the event is not consumed and will continue to be propagated.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
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