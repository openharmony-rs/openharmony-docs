# AccessibilityExtensionContext (System API)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=5afea8900a93c1d5d53117a86ba6b7c5d998328d translatedAt=2026-08-07T07:20:05.453Z pushedAt=2026-08-07T09:55:09.663Z -->

The **AccessibilityExtensionContext** module, inherited from **ExtensionContext**, provides context for **AccessibilityExtensionAbility**.

The Accessibility Extension Context module provides a context environment, supporting accessibility apps in configuring information types of interest, querying node information, gesture injection, and more.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This page contains only the system APIs of this module. For other public APIs, see [AccessibilityExtensionContext (Accessibility Extension Context)](js-apis-inner-application-accessibilityExtensionContext.md).

## Usage

Before using AccessibilityExtensionContext, obtain an AccessibilityExtensionContext instance through an AccessibilityExtensionAbility subclass instance.

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class EntryAbility extends AccessibilityExtensionAbility {
  onConnect(): void {
    let axContext = this.context; 
  } 
}
```

## Parameter<sup>20+</sup>

Provides parameter values for specific settings when an accessibility node element performs a specific action. Different action types require different parameter fields. For details about the mapping between action types and parameter fields, see [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction) (actions that can be performed by an accessibility node element).

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                  | Type     | Read-Only  |Optional| Description                                |
| ------------------- | ------ | ---- | ----|--------------------------------- |
| setText             | string | No   | Yes |Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).SET_TEXT. Text content to set for the component.                 |
| selectTextBegin     | string | No  | Yes |Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).SET_SELECTION. Start coordinate for selecting text within the component, for example, '2'. Must be set together with selectTextEnd and selectTextInForWard.        |
| selectTextEnd       | string | No   | Yes |Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).SET_SELECTION. End coordinate for selecting text within the component, for example, '8'. Must be set together with selectTextBegin and selectTextInForWard.      |
| selectTextInForWard | boolean   | No    | Yes |Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).SET_SELECTION. Whether to select forward when selecting text within the component. The value true means forward selection, and false means backward selection. Must be set together with selectTextBegin and selectTextEnd. |
| offset              | string | No   | Yes |Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).SET_CURSOR_POSITION. Character offset for setting the cursor, for example, '1'.    |
| spanId              | string | No   |Yes |Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).SPAN_CLICK. Text ID for tapping the hyperlink text.                |
| scrollType | string | No | Yes |Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).SCROLL_FORWARD or SCROLL_BACKWARD. Component scroll type. The value 'fullScreen' means full-screen scrolling, and 'halfScreen' means half-screen scrolling. |
| injectActionType | [InjectActionType](./js-apis-accessibility-sys.md#injectactiontype) | No   | Yes |Sets the injected action type. Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).INJECT_ACTION.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|
| customAction          | string | No   | Yes | Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).EXECUTE_CUSTOM_ACTION. Name of the custom action.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| accessibilityFocusScene          | [AccessibilityFocusScene](./js-apis-accessibility-sys.md#accessibilityfocusscene) | No   | Yes | Configured when executing [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction).ACCESSIBILITY_FOCUS. Accessibility focus scenario.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |

**Example**

When selecting characters from index 0 to 7 in the text input box, the parameters set by the executeAction(AccessibilityAction.SET_SELECTION, parameter) method are as follows:

```ts
import { Parameter } from '@kit.AccessibilityKit';

let parameter : Parameter = { selectTextBegin: '0', selectTextEnd: '8', selectTextInForWard: true };
```

## AccessibilityGrid<sup>20+</sup>

Accessibility grid information. For details, see the property currentItem in [AccessibilityElement](#accessibilityelement).

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                  | Type     | Read-Only  |Optional| Description                                |
| ------------------- | ------ | ---- | ----|--------------------------------- |
| rowIndex             | number | No   |No |Grid row index.                 |
| columnIndex          | number | No  | No|Grid column index.        |

## AccessibilitySpan<sup>20+</sup>

Hyperlink text information for accessibility. For details, see the attribute spans in [AccessibilityElement](#accessibilityelement).

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                  | Type     | Read-Only  |Optional| Description                                |
| ------------------- | ------ | ---- | ----|--------------------------------- |
| spanId             | number | No   |No |Hyperlink text number.                 |
| spanText          | string | No | No|Text content of the hyperlink text.        |
| accessibilityText          | string | No  | No|Accessibility text of the hyperlink text.        |
| accessibilityDescription          | string | No  | No|Accessibility description of the hyperlink text.        |
| accessibilityLevel          | string | No  | No|Accessibility level of the hyperlink text. 'auto': whether the text can be identified by accessibility is determined by the system; 'yes': can be identified by accessibility; 'no': cannot be identified by accessibility; 'no-hide-descendants': the current text and its child content cannot be identified by accessibility.        |

## FocusRule<sup>23+</sup>

type FocusRule = 'bypassSelf' | 'bypassSelfDescendants' | 'checkSelf' | 'checkSelfBypassDescendants'

Describes how to determine the focus capability of the starting node and its child nodes when searching for focusable nodes.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type            | Description          |
| -------- | ------- |
| 'bypassSelf'       | Skips the check on the starting node and only checks its child nodes. The value is fixed to the 'bypassSelf' string.|
| 'bypassSelfDescendants'     | Skips the check on the starting node and all its child nodes. The value is fixed to the 'bypassSelfDescendants' string.|
| 'checkSelf'     | Checks whether the starting node can gain focus first. If yes, uses it directly; if not, continues to check its child nodes. The value is fixed to the 'checkSelf' string.|
| 'checkSelfBypassDescendants' | Checks whether the starting node can gain focus first. If yes, uses it; if not, skips the check on all child nodes. The value is fixed to the 'checkSelfBypassDescendants' string.|

## FocusCondition<sup>23+</sup>

type FocusCondition = 'forward' | 'backward' | 'findLast' | 'getForwardScrollAncestor' | 'getBackwardScrollAncestor' | 'getScrollableAncestor'

Describes the method for querying focusable nodes.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type       | Description      |
| -------- | ------- |
| 'forward'       | The next focusable node after the current node. The value is fixed to the 'forward' string.|
| 'backward'     | The previous focusable node before the current node. The value is fixed to the 'backward' string.|
| 'findLast'     | The last node among the child nodes of the starting node. The value is fixed to the 'findLast' string.|
| 'getForwardScrollAncestor' | The scrollable parent component that supports forward scrolling. The value is fixed to the 'getForwardScrollAncestor' string.|
| 'getBackwardScrollAncestor'| The scrollable parent component that supports backward scrolling. The value is fixed to the 'getBackwardScrollAncestor' string.|
| 'getScrollableAncestor' | The scrollable parent component that supports scrolling in any direction. The value is fixed to the 'getScrollableAncestor' string.|

## FocusMoveResult<sup>23+</sup>

Return value type of the accessibility node query.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                  | Type     | Read-Only  |Optional| Description                                |
| ------------------- | ------ | ---- | ----|--------------------------------- |
| target | Array&lt;[AccessibilityElement](#accessibilityelement)&gt; | No | No | List of accessibility nodes returned by the query.|
| result | [FocusMoveResultCode](./js-apis-accessibility-sys.md#focusmoveresultcode23)  | No | No | Result type of the accessibility node query.|

## AccessibilityExtensionContext

Provides the context environment for the Accessibility extension, including capabilities such as launching foreground pages, querying nodes, obtaining focus elements, screen-on control, and pre-close callback management. It is suitable for scenarios where accessibility assistive apps interact with system UIs. An instance of AccessibilityExtensionContext must be obtained through an AccessibilityExtensionAbility subclass instance.

### startAbility<sup>12+</sup>

startAbility(want: Want): Promise\<void>

Starts a foreground page. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../../reference/apis-ability-kit/js-apis-app-ability-want.md) | Yes | Want type parameter, which passes in the information about the ability to start, such as the ability name and bundle name. |

**Return value**

| Type | Description |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | ---------------------------------------- |
| 201 | The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let want: Want = {
      bundleName: 'com.huawei.hmos.photos',
      abilityName: 'com.huawei.hmos.photos.MainAbility'
    };

    this.context.startAbility(want).then(() => {
      console.info(`succeeded in starting ability`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to start ability. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### getElements<sup>18+</sup>

getElements(windowId: number, elementId?: number): Promise<Array&lt;AccessibilityElement&gt;>

Queries all descendant accessibility nodes in a specified window or under a specified node in batches. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| windowId | number | Yes | ID of the window to query. |
| elementId | number | No | ID of the node to query. If this parameter is passed, all child nodes under this node (excluding the node itself) are queried. If this parameter is not passed or **-1** is passed, the complete node tree (including the root node) in the specified window is queried. The default value is **-1**. |

**Return value**

| Type                                  | Description                     |
| ----------------------------------- | ---------------------- |
| Promise<Array&lt;[AccessibilityElement](#accessibilityelement)&gt;> | Promise used to return the list of all child nodes in the current window or under the current node. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: number = 10;
    let elementId: number = 10;

    this.context.getElements(windowId, elementId).then((data:AccessibilityElement[]) => {
      console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### getDefaultFocusedElementIds<sup>18+</sup>

getDefaultFocusedElementIds(windowId: number): Promise&lt;Array&lt;number&gt;&gt;

Queries the list of default focus element IDs customized by the app. This API uses a promise to return the result.

Default focus refers to the element that the accessibility service prioritizes for focusing when a window is opened.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| windowId | number | Yes | ID of the window to query. |

**Return value**

| Type                                  | Description                     |
| ----------------------------------- | ---------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the list of custom default focus IDs in the current window. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: number = 10;

    this.context.getDefaultFocusedElementIds(windowId).then((data: number[]) => {
      console.info(`succeeded in getting default focus, ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get default focus. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### holdRunningLockSync<sup>20+</sup>

holdRunningLockSync(): void

Holds the RunningLock. After the lock is held, the screen will not automatically turn off. After this method is called, call [unholdRunningLockSync](#unholdrunninglocksync20) to release the lock and restore the automatic screen-off mechanism when the screen no longer needs to stay on.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.holdRunningLockSync();
    } catch (err) {
      console.error(`Failed to hold RunningLock. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

### unholdRunningLockSync<sup>20+</sup>

unholdRunningLockSync(): void

Releases the RunningLock and restores automatic screen-off. Used in pair with [holdRunningLockSync](#holdrunninglocksync20).

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.unholdRunningLockSync();
    } catch (err) {
      console.error(`Failed to unhold RunningLock. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

### on('preDisconnect')<sup>20+</sup>

on(type: 'preDisconnect', callback: Callback&lt;void&gt;): void

Registers a callback with the accessibility service, which is invoked before the accessibility service closes this Accessibility Extension Service. This API uses an asynchronous callback to return the result.

This registration function must be used together with [notifyDisconnect](#notifydisconnect20). If [notifyDisconnect](#notifydisconnect20) is not called, the Accessibility Extension Service is automatically closed after a default wait of 30 seconds.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Listening event name, which is fixed to 'preDisconnect', indicating the event that the Accessibility Extension Service is about to be closed. |
| callback | Callback&lt;void&gt; | Yes | Callback invoked when the Accessibility Extension Service is about to be closed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.on('preDisconnect', () => {
        console.info(`To do something before accessibilityExtension disconnect.`);
      });
    } catch (err) {
      console.error(`Failed to register. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

### off('preDisconnect')<sup>20+</sup>

off(type: 'preDisconnect', callback?: Callback&lt;void&gt;): void

Unregisters the pre-disconnect callback registered with the accessibility service. This callback must be registered via on('preDisconnect') before it can be unregistered. After unregistration, the callback will no longer be executed before the accessibility service closes this extension service.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Event name, which is fixed to 'preDisconnect', indicating that the accessibility extension service is about to be closed. |
| callback | Callback&lt;void&gt; | No | Callback for the event that the accessibility extension service is about to be closed. It must be the same as the callback in [on('preDisconnect')](#onpredisconnect20). If this parameter is not specified, all registered events are unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.off('preDisconnect');
    } catch (err) {
      console.error(`Failed to unRegister. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

### notifyDisconnect<sup>20+</sup>

notifyDisconnect(): void

Notifies the accessibility service that the accessibility extension service can be closed.

This function must be used together with the pre-disconnection registration API [on('preDisconnect')](#onpredisconnect20). If the pre-disconnection registration function has not been called, calling this function directly has no effect.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.notifyDisconnect();
    } catch (err) {
      console.error(`Failed to notify accessibility. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

### getAccessibilityFocusedElement<sup>20+</sup>

getAccessibilityFocusedElement(): Promise\<AccessibilityElement>

Obtains the element that currently has the accessibility focus. This API uses a promise to return the result.

The accessibility focus refers to the node currently focused by the accessibility service, which is different from the input focus.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                                 | Description                    |
| ----------------------------------- | ---------------------- |
| Promise\<[AccessibilityElement](#accessibilityelement)>| Promise used to return the element that currently has the focus. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300003 | No accessibility permission to perform the operation. |
| 9300006 |  The target application failed to connect to accessibility service. |

**Example**

```ts
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    this.context.getAccessibilityFocusedElement().then((element: AccessibilityElement) => {
      console.info(`succeeded in getting accessibility focused element, ${element.bundleName}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get accessibility focused element. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### getRootInActiveWindow<sup>20+</sup>

getRootInActiveWindow(windowId ?: number): Promise\<AccessibilityElement>

Obtains the root element of the accessibility node tree of the active window. This API uses a promise to return the result.

The active window refers to the foreground app window that currently gains focus.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| windowId | number | No | ID of the window to query. If this parameter is not provided, the root element of the active window is queried by default. |

**Return value**

| Type                                 | Description                    |
| ----------------------------------- | ---------------------- |
| Promise\<[AccessibilityElement](#accessibilityelement)>| Promise used to return the root element of the active window. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300003 | No accessibility permission to perform the operation. |
| 9300006 | The target application failed to connect to accessibility service. |

**Example**

```ts
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: number = 0;

    this.context.getRootInActiveWindow(windowId).then((element: AccessibilityElement) => {
      console.info(`succeeded in getting root in active window element, ${element.bundleName}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get root in active window element. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### getAccessibilityWindowsSync<sup>20+</sup>

getAccessibilityWindowsSync(displayId?: number): Array\<AccessibilityElement>

Obtains the list of all accessibility-accessible windows on the current display device.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| displayId | number | No | Display ID. If this parameter is not provided, the default displayId is used. |

**Return value**

| Type | Description |
| ----------------------------------- | ---------------------- |
| Array\<[AccessibilityElement](#accessibilityelement)> | List of windows. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      let displayId: number = 0;
      let windowList = this.context.getAccessibilityWindowsSync(displayId);
      if (windowList) {
        for (let window of windowList) {
          console.info(`getAccessibilityWindowsSync: windowId: ${window.windowId}`);
        }
      }
    } catch (err) {
     console.error(`Failed to get accessibility windows sync. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

### updateAccessibilityElementProperty

updateAccessibilityElementProperty(elementId: number, windowId: number, node: AccessibilityVirtualNode): Promise&lt;OperateVirtualNodeResult&gt;

Modifies the accessibility node property. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type                                                                           | Mandatory | Description |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| elementId | number | Yes | ID of the accessibility node to modify. |
| windowId | number | Yes | ID of the window of the accessibility node to modify. |
| node | [AccessibilityVirtualNode](#accessibilityvirtualnode) | Yes | Property values of the accessibility node to modify. The modifiable properties include:<br>accessibilityText, accessibilityGroup, accessibilityLevel, checkable, checked, selected, clickable, enabled, customComponentType. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[OperateVirtualNodeResult](./js-apis-accessibility-sys.md#operatevirtualnoderesult)&gt; | Promise used to return the execution result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed.The application does not have the permission required to call the API. |
| 202 | Permission verification failed.A non-system application calls a system API. |
| 9300000 | System abnormality.Possible causes: <br>1.Internal operation failed.<br>2.Failed to obtain the required service or client object (null pointer).<br>3.IPC communication failed.<br>4.Failed to obtain the accessibility service proxy.<br>5.Timed out while waiting for the result of an asynchronous operation. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext,
  AccessibilityVirtualNode,
  OperateVirtualNodeResult
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let elementId: number = 10; // Use the ID of the node whose properties need to be modified.
    let windowId: number = 10; // Use the ID of the window whose properties need to be modified.
    let accessibilityVirtualNode: AccessibilityVirtualNode = {
      virtualNodeId: 1,
      accessibilityText: "accessibilityTextNew"
    }
    this.context.updateAccessibilityElementProperty(elementId, windowId, accessibilityVirtualNode).then((data: OperateVirtualNodeResult)=>{
      console.info(`updateAccessibilityElementProperty: elementId:${elementId} windowId:${windowId}, result:${data}`)
    }).catch((err: BusinessError) => {
      console.error(`failed to update accessibility element property, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

### addAccessibilityVirtualNodes

addAccessibilityVirtualNodes(elementId: number, windowId: number, nodes: Array&lt;AccessibilityVirtualNode&gt;): Promise&lt;OperateVirtualNodeResult&gt;

Adds a virtual accessibility node tree. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type                                                                           | Mandatory | Description |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| elementId | number | Yes | Parent node ID of the virtual node tree to add. |
| windowId | number | Yes | Parent window ID of the virtual node tree to add. |
| nodes | Array<[AccessibilityVirtualNode](#accessibilityvirtualnode)> | Yes | Array of virtual nodes to add. The virtual nodes in the array are organized into a tree based on the parentId and childNodeIds parent-child relationships.|

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[OperateVirtualNodeResult](./js-apis-accessibility-sys.md#operatevirtualnoderesult)&gt; | Promise used to return the execution result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed.The application does not have the permission required to call the API. |
| 202 | Permission verification failed.A non-system application calls a system API. |
| 9300000 | System abnormality.Possible causes: <br>1.Internal operation failed.<br>2.Failed to obtain the required service or client object (null pointer).<br>3.IPC communication failed.<br>4.Failed to obtain the accessibility service proxy.<br>5.Timed out while waiting for the result of an asynchronous operation. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext,
  AccessibilityVirtualNode,
  OperateVirtualNodeResult
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let elementId: number = 10; // Use the parent node ID for which the virtual node tree is to be added.
    let windowId: number = 10; // Use the window ID for which the virtual node tree is to be added.
    let accessibilityVirtualNode: AccessibilityVirtualNode = {
      virtualNodeId: 1,
      accessibilityText: "accessibilityTextNew"
    }
    this.context.addAccessibilityVirtualNodes(elementId, windowId, [accessibilityVirtualNode]).then((data: OperateVirtualNodeResult)=>{
      console.info(`addAccessibilityVirtualNodes: elementId:${elementId} windowId:${windowId}, result:${data}`)
    }).catch((err: BusinessError) => {
      console.error(`failed to add virtual nodes, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

### removeAccessibilityVirtualNodes

removeAccessibilityVirtualNodes(elementId: number, windowId: number): Promise&lt;OperateVirtualNodeResult&gt;

Deletes the added accessibility virtual node tree. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| elementId | number | Yes | ID of the node where the virtual node tree to be deleted is located. |
| windowId  | number | Yes | ID of the window where the virtual node tree to be deleted is located. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[OperateVirtualNodeResult](./js-apis-accessibility-sys.md#operatevirtualnoderesult)&gt; | Promise used to return the execution result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed.The application does not have the permission required to call the API.  |
| 202 | Permission verification failed.A non-system application calls a system API. |
| 9300000 | System abnormality.Possible causes: <br>1.Internal operation failed.<br>2.Failed to obtain the required service or client object (null pointer).<br>3.IPC communication failed.<br>4.Failed to obtain the accessibility service proxy.<br>5.Timed out while waiting for the result of an asynchronous operation. |

**Example**

```ts
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext,
  OperateVirtualNodeResult
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let elementId: number = 10; // Use the parent node ID of the virtual node tree to be removed.
    let windowId: number = 10; // Use the window ID of the virtual node tree to be removed.
    this.context.removeAccessibilityVirtualNodes(elementId, windowId).then((data: OperateVirtualNodeResult)=>{
      console.info(`removeAccessibilityVirtualNodes: elementId:${elementId} windowId:${windowId}, result:${data}`)
    }).catch((err: BusinessError) => {
      console.error(`failed to remove virtual nodes, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## AccessibilityElement

An accessibility node element that provides capabilities such as querying parent/child elements, finding elements by content or focus direction, and performing accessibility actions. It is applicable to scenarios where an accessibility app needs to interact with and operate on UI nodes.

Before calling the APIs of AccessibilityElement, call [AccessibilityExtensionContext.getAccessibilityFocusedElement](#getaccessibilityfocusedelement20) or [AccessibilityExtensionContext.getRootInActiveWindow](#getrootinactivewindow20) to obtain an AccessibilityElement instance.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Attributes

| Name                  | Type                                                             | Read-Only | Optional | Description             |
|----------------------|--------------------------------------------------------------------|------|------|-------------------|
| accessibilityFocused<sup>20+</sup> | boolean | No | Yes | Whether the element gains focus for accessibility purposes. The value **true** indicates that the element has gained focus, and **false** indicates the opposite.<br>Default value: **false**.|
| bundleName<sup>20+</sup> | string                                                             | No  | Yes  | Bundle name.|
| checkable<sup>20+</sup> | boolean | No | Yes | Whether the element is checkable. The value **true** indicates that the element is checkable, and **false** indicates the opposite.<br>Default value: **false**.|
| checked<sup>20+</sup> | boolean | No | Yes | Whether the element is checked. The value **true** indicates that the element is checked, and **false** indicates the opposite.<br>Default value: **false**.|
| clickable<sup>20+</sup> | boolean | No | Yes | Whether the element is clickable. The value **true** indicates that the element is clickable, and **false** indicates the opposite.<br>Default value: **false**.|
| componentId<sup>20+</sup> | number | No | Yes | ID of the component to which the element belongs.<br>Default value: **-1**.|
| componentType<sup>20+</sup> | string                                                             | No  | Yes  | Type of the component to which the element belongs.|
| contents<sup>20+</sup> | Array&lt;string&gt;                                                | No  | Yes  | Content displayed by the element. Default value: empty array.|
| currentIndex<sup>20+</sup> | number                                                             | No  | Yes  | Index of the current item.<br>Default value: **0**.|
| description<sup>20+</sup> | string                                                             | No  | Yes  | Description of the element.|
| editable<sup>20+</sup> | boolean | No | Yes | Whether the element is editable. The value **true** indicates that the element is editable, and **false** indicates the opposite.<br>Default value: **false**.|
| endIndex<sup>20+</sup> | number                                                             | No  | Yes  | Index of the last list item displayed on the screen.<br>Default value: **0**.|
| error<sup>20+</sup> | string                                                             | No  | Yes  | Error state of the element.|
| focusable<sup>20+</sup> | boolean | No | Yes | Whether the element can gain focus (here it refers to accessibility focus, which is different from input focus). The value **true** indicates that the element can gain focus, and **false** indicates the opposite.<br>Default value: **false**.|
| hintText<sup>20+</sup> | string                                                             | No  | Yes  | Hint text.|
| inputType<sup>20+</sup> | number                                                             | No  | Yes  | Type of the input text. Different values correspond to different input modes: **0** indicates no specific type; **1** indicates text; **2** indicates email; **3** indicates date; **4** indicates time; **5** indicates number; **6** indicates password; **7** indicates phone number; **8** indicates username; **9** indicates new password.<br>Default value: **0**.|
| inspectorKey<sup>20+</sup> | string                                                             | No  | Yes  | Inspector key.|
| isActive<sup>20+</sup> | boolean | No | Yes | Whether the element is active. The value **true** indicates that the element is active, and **false** indicates the opposite.<br>Default value: **true**.|
| isEnable<sup>20+</sup> | boolean | No | Yes | Whether the element is enabled. The value **true** indicates that the element is enabled, and **false** indicates the opposite.<br>Default value: **false**.|
| isHint<sup>20+</sup> | boolean | No | Yes | Whether the element is a hint. The value **true** indicates that the element is a hint, and **false** indicates the opposite.<br>Default value: **false**.|
| isFocused<sup>20+</sup> | boolean | No | Yes | Whether the element has gained focus (here it refers to accessibility focus, which is different from input focus). The value **true** indicates that the element has gained focus, and **false** indicates the opposite.<br>Default value: **false**.|
| isPassword<sup>20+</sup> | boolean                                                            | No  | Yes  | Whether the element is a password. The value **true** indicates that the element is a password, and **false** indicates the opposite.<br>Default value: **false**.|
| isVisible<sup>20+</sup> | boolean | No | Yes | Whether the element is visible. The value **true** indicates that the element is visible, and **false** indicates the opposite.<br>Default value: **false**.|
| itemCount<sup>20+</sup> | number                                                             | No  | Yes  | Total number of items.<br>Default value: **0**.|
| lastContent<sup>20+</sup> | string                                                             | No  | Yes  | Content of the last item.|
| layer<sup>20+</sup> | number                                                             | No  | Yes  | Display layer of the element.|
| longClickable<sup>20+</sup> | boolean | No | Yes | Whether the element is long-clickable. The value **true** indicates that the element is long-clickable, and **false** indicates the opposite.<br>Default value: **false**.|
| pageId<sup>20+</sup> | number | No | Yes | Page ID.<br>Default value: **-1**.|
| pluralLineSupported<sup>20+</sup> | boolean | No | Yes | Whether the element supports multi-line text. The value **true** indicates that the element supports multi-line text, and **false** indicates the opposite.<br>Default value: **false**.|
| rect<sup>20+</sup>                 | [Rect](js-apis-inner-application-accessibilityExtensionContext.md#rect)                                                      | No  | Yes  | Area of the element.|
| resourceName<sup>20+</sup>         | string                                                             | No  | Yes  | Resource name of the element.|
| screenRect<sup>20+</sup>           | [Rect](js-apis-inner-application-accessibilityExtensionContext.md#rect)                                                      | No  | Yes  | Display area of the element.|
| scrollable<sup>20+</sup>           | boolean                                                            | No  | Yes  | Whether the element is scrollable. The value **true** indicates that the element is scrollable, and **false** indicates the opposite. When the value conflicts with that of accessibilityScrollable, the value of accessibilityScrollable prevails.<br>Default value: **false**.|
| selected<sup>20+</sup>             | boolean                                                            | No  | Yes  | Whether the element is selected. The value **true** indicates that the element is selected, and **false** indicates the opposite.<br>Default value: **false**.|
| startIndex<sup>20+</sup>           | number                                                             | No  | Yes  | Index of the first list item on the screen.<br>Default value: **0**.|
| text<sup>20+</sup>                 | string                                                             | No  | Yes  | Text content of the element.|
| textLengthLimit<sup>20+</sup>      | number                                                             | No  | Yes  | Maximum text length of the element. Default value: **0**.|
| textMoveUnit<sup>20+</sup>         | [accessibility.TextMoveUnit](js-apis-accessibility.md#textmoveunit)| No  | Yes  | Movement unit for text reading.<br>Default value: **char**.|
| triggerAction<sup>20+</sup>        | [accessibility.Action](js-apis-accessibility.md#action)            | No  | Yes  | Action that triggers the element event.|
| type<sup>20+</sup>                 | [WindowType](js-apis-inner-application-accessibilityExtensionContext.md#windowtype)                                          | No  | Yes  | Window type of the element.|
| valueMax<sup>20+</sup>             | number                                                             | No  | Yes  | Maximum value.<br>Default value: **0**.|
| valueMin<sup>20+</sup>             | number                                                             | No  | Yes  | Minimum value.<br>Default value: **0**.|
| valueNow<sup>20+</sup>             | number                                                             | No  | Yes  | Current value.<br>Default value: **0**.|
| windowId<sup>20+</sup>             | number                                                             | No  | Yes  | Window ID.<br>Default value: **-1**.|
| offset<sup>20+</sup>             | number              | No  | Yes  | Pixel offset of the content area relative to the top coordinate of the scrollable component (such as List and Grid), in pixels (px).<br>Default value: **0**.|
| textType<sup>20+</sup>             | string                                                             | No  | Yes  | Accessibility text type of the element, configured by the accessibilityTextHint attribute of the component.|
| accessibilityText<sup>20+</sup> | string                                                  | No  | Yes  | Accessibility text information of the element.|
| accessibilityStateDescription<sup>23+</sup> | string                                      | No  | Yes  | Custom accessibility state announcement text of the element.<br>**Model restriction:** This API can be used only in the stage model.|
| hotArea<sup>20+</sup>             | [Rect](js-apis-inner-application-accessibilityExtensionContext.md#rect)                                                              | No  | Yes  | Touchable area of the element.|
| customComponentType<sup>20+</sup>             | string                                                             | No  | Yes  | Custom component type. Corresponds to the [AccessibilityRoleType](../apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityroletype18) type of the element.|
| accessibilityNextFocusId<sup>20+</sup>             | number                | No  | Yes  | ID of the next component to gain focus.<br>Default value: **-1**.|
| accessibilityPreviousFocusId<sup>20+</sup>             | number                | No  | Yes  | ID of the previous component to gain focus.<br>Default value: **-1**.|
| extraInfo<sup>20+</sup>             | string     | No  | Yes  | Extra information of the element. The value is a JSON string.|
| accessibilityScrollable<sup>20+</sup>             | boolean                 | No  | Yes  | Whether the element is scrollable for accessibility purposes. This attribute has a higher priority than scrollable. That is, when the value of accessibilityScrollable conflicts with that of scrollable, the value of accessibilityScrollable prevails.<br>The value **true** indicates that the element is scrollable, and **false** indicates the opposite.<br>Default value: **false**.|
| supportedActionNames<sup>20+</sup> | Array&lt;string&gt;                                                | No  | Yes  | Supported action names. Default value: empty array.|
| accessibilityGroup<sup>20+</sup>  | boolean                                                            | No  | Yes  | Whether the element is an accessibility group. The value **true** indicates that the element is an accessibility group, and **false** indicates the opposite.<br>Default value: **false**.|
| accessibilityLevel<sup>20+</sup>             | string                                                             | No  | Yes  | Accessibility level of the component.<br>**'auto'**: The accessibility grouping service and ArkUI jointly determine whether the component can be recognized by accessibility.<br>**'yes'**: The component can be recognized by accessibility.<br>**'no'**: The component cannot be recognized by accessibility.<br>**'no-hide-descendants'**: The component and all its child components cannot be recognized by accessibility. Default value: **'auto'**.|
| navDestinationId<sup>20+</sup>             | number                                                             | No  | Yes  | Navigation destination ID of the component. Default value: **-1**.|
| currentItem<sup>20+</sup>             | [AccessibilityGrid](#accessibilitygrid20)                                                             | No  | Yes  | Current item in the component grid.|
| spans<sup>20+</sup>             | [AccessibilitySpan](#accessibilityspan20)[]                                                             | No  | Yes  | Array of accessibility hyperlink text information of the component. Default value: empty array.|
| accessibilityVisible<sup>20+</sup>  | boolean                                                            | No  | Yes  | Whether the component is visible for accessibility. The value **true** indicates that the component is visible, and **false** indicates the opposite. Default value: **true**.|
| mainWindowId<sup>20+</sup>             | number                                                             | No  | Yes  | Main window ID of the component. Default value: **-1**.|
| clip<sup>20+</sup>  | boolean                                                            | No  | Yes  | Whether the component needs clipping. The value **true** indicates that clipping is needed, and **false** indicates the opposite. Default value: **false**.|
| parentId<sup>20+</sup>             | number                                                             | No  | Yes  | Parent element ID of the component. Default value: **-1**.|
| childrenIds<sup>20+</sup>             | Array\<number>                                                             | No  | Yes  | List of child element IDs of the component. Default value: empty array.|
| isEssential             | boolean              | No   | Yes   | Whether the element is essential to the user. The value **true** indicates that the element is essential, and **false** indicates the opposite. Default value: **false**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| belongTreeId             | number              | No   | Yes   | ID of the component tree to which the element belongs. Default value: **-1**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| childrenTreeId             | number              | No   | Yes   | ID of the child component tree of the element. Default value: **-1**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| customActions             | Array\<string>                                                             | No  | Yes  | List of custom actions supported by the element.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| sourceType             | [AccessibilitySourceType](./js-apis-accessibility-sys.md#accessibilitysourcetype) | No  | Yes  | Source type of the component, used to distinguish default components from newly added or modified virtual components.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |

**Example**

```ts
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: number = 10;

    this.context.getRootInActiveWindow(windowId).then((element: AccessibilityElement) => {
      console.info('AccessibilityElement.checkable: ' + element.checkable);
      console.info('AccessibilityElement.checked: ' + element.checked);
      console.info('AccessibilityElement.clickable: ' + element.clickable);
      console.info('AccessibilityElement.componentId: ' + element.componentId);
      console.info('AccessibilityElement.componentType: ' + element.componentType);
      console.info('AccessibilityElement.contents: ' + element.contents);
      console.info('AccessibilityElement.currentIndex: ' + element.currentIndex);
      console.info('AccessibilityElement.description: ' + element.description);
      // ...
    }).catch((err: BusinessError) => {
      console.error(`Failed to get root in active window. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### enableScreenCurtain<sup>12+</sup>

enableScreenCurtain(isEnable: boolean): void

Enables or disables the screen curtain. When the screen curtain is enabled, the screen content is hidden (the screen dims), but the device still responds to operations normally.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name         | Type                                     | Mandatory   | Description             |
| ----------- | ---------------------------------------- | ---- | -------------- |
| isEnable | boolean | Yes    | Whether to enable the screen curtain. The value `true` means to enable the screen curtain, and `false` means to disable it.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }
    this.context.getRootInActiveWindow().then((rootElement: AccessibilityElement) => {
      console.info(`succeeded in getting root element of the window, ${JSON.stringify(rootElement)}`);
      rootElement.enableScreenCurtain(true);
      console.info(`Succeeded in enabling screen curtain`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to enable screen curtain. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### findElement('elementId')

findElement(type: 'elementId', condition: number): Promise&lt;AccessibilityElement&gt;

Queries the node element in the current active window based on the element ID. This API uses a promise to return the result.

This method and [findElementById](#findelementbyid20) both find a node element by element ID. They are functionally equivalent. It is recommended to use findElementById.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name       | Type                                | Mandatory   | Description                                       |
| --------- | --------------------------------- | ---- | ---------------------------------------- |
| type      | string                            | Yes    | Fixed value **'elementId'**, indicating that the node element in the current active window is queried by element ID. |
| condition | number | Yes    | Element ID of the node element to query.                           |

**Return value**

| Type                                  | Description                               |
| ----------------------------------- | -------------------------------- |
| Promise&lt;[AccessibilityElement](js-apis-inner-application-accessibilityExtensionContext.md#accessibilityelement)&gt; | Promise used to return the result, which is the node element that meets the specified query condition. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                          |
| ------- | ----------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// elementId is 10.
let condition = 10;

// rootElement is an instance of AccessibilityElement, which must be obtained through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
rootElement.findElement('elementId', condition).then((data: AccessibilityElement) => {
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

### findElement('textType')

findElement(type: 'textType', condition: string): Promise\<Array\<AccessibilityElement>>

Searches for all node elements based on the accessibility text type configured in the component's accessibilityTextHint attribute. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type   | Mandatory | Description                                                        |
| --------- | ------ | --------- | ------------------------------------------------------------------ |
| type      | string | Yes       | Fixed to 'textType', indicating that elements are searched by text type. |
| condition | string | Yes       | Accessibility text type condition for the search. All node elements whose accessibilityTextHint attribute matches this text type will be returned. |

**Return value**

| Type                                                                                                                       | Description                                                                        |
| -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Promise&lt;Array&lt;[AccessibilityElement](js-apis-inner-application-accessibilityExtensionContext.md#accessibilityelement)&gt;&gt; | Promise used to return all node elements that match the specified accessibility text type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                          |
| ------- | ----------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// The content of condition must be consistent with the type field value of the target component's accessibilityTextHint attribute.
let condition = 'location'; 

// rootElement is an instance of AccessibilityElement. Obtain it through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
rootElement.findElement('textType', condition).then((data: AccessibilityElement[]) => {
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

### getCursorPosition<sup>12+</sup>

getCursorPosition(): Promise\<number>

Obtains the cursor position in a text component. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                  | Description               |
| ------------------- | ---------------- |
| Promise&lt;number&gt; | Promise used to return the current cursor position. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement. Obtain it through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
rootElement.getCursorPosition().then((data: number) => {
  console.info(`succeeded in getting cursor position, ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get cursor position. Code: ${err.code}, message: ${err.message}`);
});
```

### getCursorPosition<sup>12+</sup>

getCursorPosition(callback: AsyncCallback\<number>): void

Obtains the cursor position in a text component. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name         | Type                                     | Mandatory   | Description             |
| ----------- | ---------------------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | Yes    | Callback used to return the result. If the cursor position is obtained successfully, **err** is undefined and **data** is the position index of the cursor in the text; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement, which must be obtained through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
rootElement.getCursorPosition((err: BusinessError, data: number) => {
  if (err && err.code) {
    console.error(`Failed to get cursor position. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting cursor position, ${data}`);
});
```

### executeAction<sup>20+</sup>

executeAction(action: AccessibilityAction, parameters?: Parameter): Promise&lt;void&gt;

Performs an action on an accessibility node element based on the action type and parameters specified. This API uses a promise to return the result.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name         | Type                                     | Mandatory   | Description                                                       |
| ----------- | ---------------------------------------- | ---- |----------------------------------------------------------|
| action    | [AccessibilityAction](./js-apis-accessibility-sys.md#accessibilityaction)| Yes    | Action that can be performed on the accessibility node.|
| parameters | [Parameter](#parameter20) | No    | Parameter value set when performing the action. This parameter is passed when performing actions that require additional parameter configuration (such as SET_SELECTION, SET_CURSOR_POSITION, etc.); it is not required when performing parameterless actions (such as CLICK, etc.). Defaults to empty if not passed. |

**Return value**

| Type                  | Description               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.     |
| 9300005 | This action is not supported.            |

**Example**

- Action without parameters.

  ```ts
  // Example of parameterless Action:
  import { AccessibilityAction } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // rootElement is an instance of AccessibilityElement, which must be obtained through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
  // Actions without explicit requirements in the description are all parameterless Actions.
  rootElement.executeAction(AccessibilityAction.CLICK).then(() => {
    console.info(`succeeded in performing action CLICK`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to perform action CLICK. Code: ${err?.code}, message: ${err?.message}`);
  });
  ```

- Action with parameters (setSelection).

  ```ts
  // Example of parameterized Action:
  import { AccessibilityAction, Parameter } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // selectTextBegin: start position of the selection.
  // selectTextEnd: end position of the selection.
  // selectTextInForWard: true indicates the front cursor, and false indicates the rear cursor.
  let parameter : Parameter = { selectTextBegin: '0', selectTextEnd: '8', selectTextInForWard: true };
  // rootElement is an instance of AccessibilityElement, which must be obtained through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
  // Example code for setSelection.
  rootElement.executeAction(AccessibilityAction.SET_SELECTION, parameter).then(() => {
    console.info(`succeeded in performing action SET_SELECTION`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to perform action SET_SELECTION. Code: ${err?.code}, message: ${err?.message}`);
  });
  ```

- Action with parameters (setCursorPosition).

  ```ts
  // Example with parameter Action:
  import { AccessibilityAction, Parameter } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // offset: indicates the cursor position to set.
  let parameter : Parameter = { offset: '1' };
  // rootElement is an instance of AccessibilityElement, which must be obtained through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
  // Example code for setCursorPosition.
  rootElement.executeAction(AccessibilityAction.SET_CURSOR_POSITION, parameter).then(() => {
    console.info(`succeeded in performing action SET_CURSOR_POSITION`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to perform action SET_CURSOR_POSITION. Code: ${err?.code}, message: ${err?.message}`);
  });
  ```

### getParent<sup>20+</sup>

getParent(): Promise\<AccessibilityElement>

Obtains the parent element of an accessibility node. This API uses a promise to return the result.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise\<[AccessibilityElement](#accessibilityelement)> | Promise used to return the parent element of the current element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an instance of AccessibilityExtensionContext. Obtain it through the context property of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
axContext.getAccessibilityFocusedElement().then((element: AccessibilityElement) => {
  console.info(`element parent id: ${element.parentId}`);
  element.getParent().then((parent: AccessibilityElement) => {
    console.info(`parent element's parent id: ${parent.parentId}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get parent. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to get accessibility focused element. Code: ${err.code}, message: ${err.message}`);
});
```

### getChildren<sup>20+</sup>

getChildren(): Promise\<Array\<AccessibilityElement>>

Obtains the list of child elements of this element. This API uses a promise to return the result.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise\<Array\<[AccessibilityElement](#accessibilityelement)>> | Promise used to return the list of child elements of the current element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an instance of AccessibilityExtensionContext. It must be obtained through the context property of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
axContext.getAccessibilityFocusedElement().then((element: AccessibilityElement) => {
  console.info(`element childrenIds: ${element.childrenIds}`);
  element.getChildren().then((children: AccessibilityElement[]) => {
    console.info(`children element's size: ${children.length}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get children. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to get accessibility focused element. Code: ${err.code}, message: ${err.message}`);
});
```

### getRoot<sup>20+</sup>

getRoot(): Promise\<AccessibilityElement>

Obtains the root element of the active window. This API uses a promise to return the result.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise\<[AccessibilityElement](#accessibilityelement)> | Promise used to return the root element of the active window.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an instance of AccessibilityExtensionContext, obtained through the context property of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
let windows: AccessibilityElement[] = axContext.getAccessibilityWindowsSync();
for (let window of windows) {
  console.info(`window id: ${window.windowId}`);
  window.getRoot().then((root: AccessibilityElement) => {
    console.info(`root element's componentId: ${root.componentId}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get root. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### findElementByContent<sup>20+</sup>

findElementByContent(condition: string): Promise&lt;Array&lt;AccessibilityElement&gt;&gt;

Searches for node elements by their content text, and returns all node elements that contain the specified text. This API uses a promise to return the result.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| condition | string | Yes | Content text of the element to find. After this parameter is set, all node elements that contain this text content are returned. |

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AccessibilityElement](#accessibilityelement)&gt;&gt; | Promise used to return the result. The value is a list of elements that contain the specified content.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300006 | The target application failed to connect to accessibility service. |

**Example**

```ts
// Page.ets
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
// ...

// AccessibilityExtAbility.ets
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let windowId: number = 10;

// axContext is an instance of AccessibilityExtensionContext, obtained through the context property of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
axContext.getRootInActiveWindow(windowId).then((root: AccessibilityElement) => {
    root.findElementByContent('connect').then((elements: AccessibilityElement[]) => {
        console.info('findElementByContent size=' + elements.length);
    }).catch((err: BusinessError) => {
        console.error(`Failed to find element by content. Code: ${err.code}, message: ${err.message}`);
    });
}).catch((err: BusinessError) => {
  console.error(`Failed to get root in active window. Code: ${err.code}, message: ${err.message}`);
});
```

### findElementByFocusDirection<sup>20+</sup>

findElementByFocusDirection(condition: FocusDirection): Promise\<AccessibilityElement>

Searches for an element based on the focus direction. This API uses a promise to return the result.

Compared with [findElementsByCondition](#findelementsbycondition23), this method is mainly used to search for web components, while findElementsByCondition is mainly used to search for UI components.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| condition | [FocusDirection](js-apis-inner-application-accessibilityExtensionContext.md#focusdirection) | Yes | Focus direction, which specifies the search direction for finding elements. For example, 'forward' indicates forward search and 'backward' indicates backward search. |

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | ----------------------------- |
| Promise\<[AccessibilityElement](#accessibilityelement)> | Promise used to return the result. The element in the specified focus direction. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID    | Error Message                            |
| ----- | ---------------------------------------- |
| 201   | Permission verification failed. The application does not have the permission required to call the API. |
| 202   | Permission verification failed. A non-system application calls a system API. |
| 9300006 | The target application failed to connect to accessibility service. |

**Example**

```ts
// Page.ets
// Click TextInput to make it the accessibility focus element. The next focus element in the upward direction is Text#connect.
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)

    TextInput({ placeholder: 'please input...' })
        .id('text_input')
        .fontSize($r('app.float.page_text_font_size'))
// ...

// AccessibilityExtAbility.ets
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an instance of AccessibilityExtensionContext, which must be obtained through the context property of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
axContext.getAccessibilityFocusedElement().then((focus: AccessibilityElement) => {
    focus.findElementByFocusDirection('up').then((element: AccessibilityElement) => {
        console.info('findElementByFocusDirection UP componentId: ' + element.componentId);
    }).catch((err: BusinessError) => {
        console.error(`Failed to find element by focus direction. Code: ${err.code}, message: ${err.message}`);
    });
}).catch((err: BusinessError) => {
  console.error(`Failed to get accessibility focused element. Code: ${err.code}, message: ${err.message}`);
});
```

### findElementByFocusDirection

findElementByFocusDirection(condition: FocusDirection, type: FocusRuleType): Promise\<AccessibilityElement>

Searches for an element based on the focus direction and focus rule type. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| condition | [FocusDirection](js-apis-inner-application-accessibilityExtensionContext.md#focusdirection) | Yes | Focus direction. |
| type | [FocusRuleType](js-apis-accessibility-sys.md#focusruletype) | Yes | Focus rule type. |

**Return value**

| Type | Description |
| ---------------------------------------- | --------------------- |
| Promise\<[AccessibilityElement](#accessibilityelement)> | Promise used to return the element that matches the focus rule type in the specified focus direction. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300006 | The target application failed to connect to accessibility service. |

**Example**

```ts
// Page.ets
// Click "Secondary Heading 1" to make it the accessibility focus element. The next focus type is a heading focus element, which is "Secondary Heading 2".
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        
    SubHeader({
      secondaryTitle: 'Secondary Heading 1',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: 'Operation',
        action: () => {
          Prompt.showToast({ message: 'demo' });
        }
      }]
    })

    TextInput({ placeholder: 'please input...' })
        .id('text_input')
        .fontSize($r('app.float.page_text_font_size'))

    SubHeader({
      secondaryTitle: 'Secondary Heading 2',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: 'Operation',
        action: () => {
          Prompt.showToast({ message: 'demo' });
        }
      }]
    })
  }

// AccessibilityExtAbility.ets
import { AccessibilityElement, FocusRuleType } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

axContext.getAccessibilityFocusedElement().then((focus: AccessibilityElement) => {
    focus.findElementByFocusDirection('forward', FocusRuleType.FOCUS_BY_TITLE).then((element: AccessibilityElement) => {
        console.info(`findElementByFocusDirection forward componentId: ${element.componentId}`);
    }).catch((err: BusinessError) => {
        console.error(`Failed to findElementByFocusDirection forward. Code: ${err.code}, message: ${err.message}`);
    });
}).catch((err: BusinessError) => {
  console.error(`Failed to getAccessibilityFocusedElement. Code: ${err.code}, message: ${err.message}`);
});
```

### findElementsByAccessibilityHintText<sup>20+</sup>

findElementsByAccessibilityHintText(condition: string): Promise\<Array\<AccessibilityElement>>

Searches for elements by hint text, and returns all node elements whose accessibilityTextHint attribute matches the text. This API uses a promise to return the result.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| condition | string | Yes | Hint text of the element to find. |

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise\<Array\<[AccessibilityElement](#accessibilityelement)>> | Promise used to return the list of elements with the specified hint text. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300006 | The target application failed to connect to accessibility service. |

**Example**

```ts
// Page.ets
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)

    TextInput({ placeholder: 'please input...' })
        .id('text_input')
        .fontSize($r('app.float.page_text_font_size'))
        .accessibilityTextHint('location')
// ...

// AccessibilityExtAbility.ets
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let windowId: number = 10;

// axContext is an instance of AccessibilityExtensionContext. Obtain it through the context property of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
axContext.getRootInActiveWindow(windowId).then((root: AccessibilityElement) => {
    root.findElementsByAccessibilityHintText('location').then((elements: AccessibilityElement[]) => {
        console.info('findElementsByAccessibilityHintText size=' + elements.length);
    }).catch((err: BusinessError) => {
        console.error(`Failed to find elements by accessibility hint text. Code: ${err.code}, message: ${err.message}`);
    });
}).catch((err: BusinessError) => {
  console.error(`Failed to get root in active window. Code: ${err.code}, message: ${err.message}`);
});
```

### findElementById<sup>20+</sup>

findElementById(condition: number): Promise\<AccessibilityElement>

Searches for a node element in the active window by element ID. This API uses a promise to return the result.

This method is functionally equivalent to [findElement('elementId')](#findelementelementid) and is recommended for priority use.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| condition | number | Yes | ID of the node element to query. |

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise\<[AccessibilityElement](#accessibilityelement)> | Promise used to return the element with the specified ID. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.|
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300006 | The target application failed to connect to accessibility service. |

**Example**

```ts
// Page.ets
// Tap TextInput to make it the accessibility focus element.
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)

    TextInput({ placeholder: 'please input...' })
        .id('text_input')
        .fontSize($r('app.float.page_text_font_size'))
// ...

// AccessibilityExtAbility.ets
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an instance of AccessibilityExtensionContext, which must be obtained through the context attribute of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
axContext.getAccessibilityFocusedElement().then((focus: AccessibilityElement) => {
    focus.findElementById(0).then((element: AccessibilityElement) => {
        console.info('findElementById componentId: ' + element.componentId);
    }).catch((err: BusinessError) => {
        console.error(`Failed to find element by id. Code: ${err.code}, message: ${err.message}`);
    });
}).catch((err: BusinessError) => {
  console.error(`Failed to get accessibility focused element. Code: ${err.code}, message: ${err.message}`);
});
```

### findElementsByCondition<sup>23+</sup>

findElementsByCondition(rule: FocusRule, condition: FocusCondition): Promise\<FocusMoveResult>

Queries focusable nodes that meet the conditions. This API uses a promise to return the result.

Compared with [findElementByFocusDirection](#findelementbyfocusdirection20), this method is mainly used to find UI components, while findElementByFocusDirection is mainly used to find Web components.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| rule | [FocusRule](#focusrule23) | Yes | Rule for checking the current node and its child nodes. |
| condition | [FocusCondition](#focuscondition23) | Yes | Mode for querying focusable nodes. |

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise\<[FocusMoveResult](#focusmoveresult23)> | Promise used to return the result. The FocusMoveResult object contains the queried accessibility node list and the query result status code.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.|
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts

import { AccessibilityElement, FocusMoveResult } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an instance of AccessibilityExtensionContext. Obtain it through the context property of an AccessibilityExtensionAbility subclass instance. For details, see the usage instructions.
axContext.getAccessibilityFocusedElement().then((focus: AccessibilityElement) => {
    focus.findElementsByCondition('bypassSelf', 'forward').then((res: FocusMoveResult) => {
        console.info('findElementsByCondition result: ' + res.result);
    }).catch((err: BusinessError) => {
        console.error(`Failed to find elements by condition. Code: ${err.code}, message: ${err.message}`);
    });
}).catch((err: BusinessError) => {
  console.error(`Failed to get accessibility focused element. Code: ${err.code}, message: ${err.message}`);
});
```

### findElementsByCondition

findElementsByCondition(rule: FocusRule, condition: FocusCondition, type: FocusRuleType): Promise\<FocusMoveResult>

Searches for focusable nodes of the target type based on the rule and query condition. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| rule | [FocusRule](#focusrule23) | Yes | Rule for checking the current node and its child nodes. |
| condition | [FocusCondition](#focuscondition23) | Yes | Method for querying focusable nodes. |
| type | [FocusRuleType](js-apis-accessibility-sys.md#focusruletype) | Yes | Focus type. |

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise\<[FocusMoveResult](#focusmoveresult23)> | Promise used to return the query result object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
// Page.ets
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        
    SubHeader({
      secondaryTitle: 'Secondary Title 1',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: 'Operation',
        action: () => {
          Prompt.showToast({ message: 'demo' });
        }
      }]
    })

    TextInput({ placeholder: 'please input...' })
        .id('text_input')
        .fontSize($r('app.float.page_text_font_size'))

    SubHeader({
      secondaryTitle: 'Secondary Title 2',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: 'Operation',
        action: () => {
          Prompt.showToast({ message: 'demo' });
        }
      }]
    })
  }

// AccessibilityExtAbility.ets

import { AccessibilityElement, FocusRuleType } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

axContext.getAccessibilityFocusedElement().then((focus: AccessibilityElement) => {
    focus.findElementsByCondition("bypassSelf", "forward", FocusRuleType.FOCUS_BY_TITLE).then((res: FocusMoveResult) => {
        console.info(`findElementsByCondition result: ${res.result}`);
    }).catch((err: BusinessError) => {
        console.error(`Failed to findElementsByCondition. Code: ${err.code}, message: ${err.message}`);
    });
}).catch((err: BusinessError) => {
  console.error(`Failed to getAccessibilityFocusedElement. Code: ${err.code}, message: ${err.message}`);
});
```

## ElementAttributeValues

Provides attribute names and value types of a node element.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Attributes

| Name                   | Type                                                              | Read-Only | Optional | Description              |
|----------------------|--------------------------------------------------------------------|------|------|-------------------|
| accessibilityStateDescription<sup>23+</sup> | string                                      | No   | Yes   | Custom accessibility status announcement text information of the element.<br>**Model restriction:** This API can be used only in the stage model.|
| isEssential             | boolean              | No   | Yes   | Whether the element is essential to the user. The value **true** means the element is essential, and **false** means the opposite. The default value is **false**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| belongTreeId             | number              | No   | Yes   | ID of the component tree to which the element belongs. The default value is **-1**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| childrenTreeId             | number              | No   | Yes   | ID of the child component tree of the element. The default value is **-1**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| currentItem             | [AccessibilityGrid](#accessibilitygrid20)              | No   | Yes   | Current item in the component grid.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| span             | [AccessibilitySpan](#accessibilityspan20)[]              | No   | Yes   | Array of hyperlink text information of the element.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| childrenIds             |      Array&lt;number&gt;         | No   | Yes   | List of child component IDs of the element.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| parentId             | number              | No   | Yes   | ID of the parent component of the element. The default value is **-1**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| mainWindowId             | number              | No   | Yes   | ID of the main window of the element. The default value is **-1**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| accessibilityVisible             | boolean              | No   | Yes   | Whether the element is accessibility visible. The value **true** means the element is accessibility visible, and **false** means the opposite. The default value is **true**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| navDestinationId             | number              | No   | Yes   | ID of the navigation destination associated with the element. The default value is **-1**.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| customActions | Array\<string>                     | No   | Yes   | List of custom actions supported by the element.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|

## AccessibilityVirtualNode

Defines an accessibility virtual node.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Attributes

| Name                  | Type                                                             | Read-Only | Optional | Description             |
|----------------------|--------------------------------------------------------------------|------|------|-------------------|
| virtualNodeId | number | No | No | Custom virtual node ID of the element.|
| text | string  | No  | Yes  | Text content of the element.|
| accessibilityText | string | No | Yes | Accessibility text information of the element.|
| accessibilityGroup | boolean | No | Yes | Whether the element is an accessibility group. The value true indicates that the element is an accessibility group, and false indicates that the element is not an accessibility group.<br>Default value: true.|
| accessibilityLevel | string | No | Yes | Accessibility level of the component.<br>'auto': The accessibility grouping service and ArkUI jointly determine whether the component can be identified by accessibility.<br>'yes': The component can be identified by accessibility.<br>'no': The component cannot be identified by accessibility.<br>'no-hide-descendants': The component and all its child components cannot be identified by accessibility.|
| rect    | [Rect](js-apis-inner-application-accessibilityExtensionContext.md#rect)  | No  | Yes  | Area of the element (relative to the parent node).|
| checkable | boolean | No | Yes | Whether the element is checkable. The value true indicates that the element is checkable, and false indicates that the element is not checkable.<br>Default value: false.|
| checked | boolean | No | Yes | Whether the element is checked. The value true indicates that the element is checked, and false indicates that the element is not checked.<br>Default value: false.|
| clickable | boolean | No | Yes | Whether the element is clickable. The value true indicates that the element is clickable, and false indicates that the element is not clickable.<br>Default value: false.|
| enabled | boolean | No | Yes | Whether the element is enabled. The value true indicates that the element is enabled, and false indicates that the element is not enabled.<br>Corresponds to the isEnable attribute of AccessibilityElement. Default value: false.|
| selected | boolean | No  | Yes  | Whether the element is selected. The value true indicates that the element is selected, and false indicates that the element is not selected.<br>Default value: false.|
| customComponentType | string   | No  | Yes  | Custom component type.|
| touchPosition | [TouchPosition](#touchposition)   | No  | Yes  | Simulated touch position.|
| accessibilityFocused | boolean | No | Yes | Whether the element has gained focus for accessibility purposes. The value true indicates that the element has gained focus, and false indicates that the element has not gained focus.<br>Default value: false.|
| parentId | number  | No  | Yes  | Parent element ID of the component.|
| childNodeIds | Array\<number>  | No  | Yes  | List of child element IDs of the component.|
| elementId | number | No | Yes | ID of the component to which the element belongs.<br>Default value: -1.|
| supportedActionNames | Array&lt;string&gt; | No  | Yes  | Supported action names.|

## TouchPosition

Touch tap position.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Attributes

| Name                  | Type                                                             | Read-Only | Optional | Description             |
|----------------------|--------------------------------------------------------------------|------|------|-------------------|
| x | number | No | No | X-coordinate of the tap position, in px.|
| y | number  | No  | No  | Y-coordinate of the tap position, in px.|