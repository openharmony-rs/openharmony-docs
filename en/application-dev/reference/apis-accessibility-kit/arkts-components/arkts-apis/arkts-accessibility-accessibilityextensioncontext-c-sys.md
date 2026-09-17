# AccessibilityExtensionContext

The **AccessibilityExtensionContext** module, inherited from **ExtensionContext**, provides context for **AccessibilityExtensionAbility**.

The Accessibility Extension Context module provides capabilities related to the accessibility extension, including configuring concerned information types, querying node information, and gesture injection.

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

**Inheritance/Implementation:** AccessibilityExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## addAccessibilityVirtualNodes

```TypeScript
addAccessibilityVirtualNodes(elementId: number, windowId: number, nodes: Array<AccessibilityVirtualNode>): Promise<OperateVirtualNodeResult>
```

Adds a virtual accessibility node tree. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementId | number | Yes | Parent node ID of the virtual node tree to add. |
| windowId | number | Yes | Parent window ID of the virtual node tree to add. |
| nodes | Array&lt;[AccessibilityVirtualNode](arkts-accessibility-accessibilityextensioncontext-accessibilityvirtualnode-i-sys.md)&gt; | Yes | Array of virtual nodes to add. The virtual nodes in the array are organized into a tree based on the parentId and childNodeIds parent-child relationships. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OperateVirtualNodeResult](arkts-accessibility-accessibility-operatevirtualnoderesult-e-sys.md)&gt; | Promise used to return the execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality.Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.IPC communication failed. <br>4.Failed to obtain the accessibility service proxy. <br>5.Timed out while waiting for the result of an asynchronous operation. |

**Examples**

```TypeScript
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

## getAccessibilityFocusedElement

```TypeScript
getAccessibilityFocusedElement(): Promise<AccessibilityElement>
```

Obtains the element that currently has the accessibility focus. This API uses a promise to return the result.

The accessibility focus refers to the node currently focused by the accessibility service, which is different from the input focus.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the element that currently has the focus. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |
| [9300006](../errorcode-accessibility.md#9300006-failed-to-connect-the-target-app-and-accessibility-service) | The target application failed to connect to accessibility service. |

**Examples**

```TypeScript
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

## getAccessibilityWindowsSync

```TypeScript
getAccessibilityWindowsSync(displayId?: number): Array<AccessibilityElement>
```

Obtains the list of all accessibility-accessible windows on the current display device.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | No | Display ID. If this parameter is not provided, the default displayId is used. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | List of windows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
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

## getDefaultFocusedElementIds

```TypeScript
getDefaultFocusedElementIds(windowId: number): Promise<Array<number>>
```

Queries the list of default focus element IDs customized by the app. This API uses a promise to return the result.

Default focus refers to the element that the accessibility service prioritizes for focusing when a window is opened.

**Since:** 18

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | ID of the window to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the list of custom default focus IDs in the current window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
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

## getElements

```TypeScript
getElements(windowId: number, elementId?: number): Promise<Array<AccessibilityElement>>
```

Queries all descendant accessibility nodes in a specified window or under a specified node in batches. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | ID of the window to query. |
| elementId | number | No | ID of the node to query. If this parameter is passed, all child nodes under this node (excluding the node itself) are queried. If this parameter is not passed or **-1** is passed, the complete node tree (including the root node) in the specified window is queried. The default value is **-1**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise used to return the list of all child nodes in the current window or under the current node. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
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

## getRootInActiveWindow

```TypeScript
getRootInActiveWindow(windowId?: number): Promise<AccessibilityElement>
```

Obtains the root element of the accessibility node tree of the active window. This API uses a promise to return the result.

The active window refers to the foreground app window that currently gains focus.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | No | ID of the window to query. If this parameter is not provided, the root element of the active window is queried by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the root element of the active window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |
| [9300006](../errorcode-accessibility.md#9300006-failed-to-connect-the-target-app-and-accessibility-service) | The target application failed to connect to accessibility service. |

**Examples**

```TypeScript
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

## holdRunningLockSync

```TypeScript
holdRunningLockSync(): void
```

Holds the RunningLock. After the lock is held, the screen will not automatically turn off. After this method is called, call [unholdRunningLockSync](#unholdrunninglocksync) to release the lock and restore the automatic screen-off mechanism when the screen no longer needs to stay on.

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

## notifyDisconnect

```TypeScript
notifyDisconnect(): void
```

Notifies the accessibility service that the accessibility extension service can be closed.

This function must be used together with the pre-disconnection registration API [on('preDisconnect')](#onpredisconnect). If the pre-disconnection registration function has not been called, calling this function directly has no effect.

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

## off('preDisconnect')

```TypeScript
off(type: 'preDisconnect', callback?: Callback<void>): void
```

Unregisters the pre-disconnect callback registered with the accessibility service. This callback must be registered via on('preDisconnect') before it can be unregistered. After unregistration, the callback will no longer be executed before the accessibility service closes this extension service.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preDisconnect' | Yes | Event name, which is fixed to 'preDisconnect', indicating that the accessibility extension service is about to be closed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback for the event that the accessibility extension service is about to be closed. It must be the same as the callback in [on('preDisconnect')](#onpredisconnect). If this parameter is not specified, all registered events are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## on('preDisconnect')

```TypeScript
on(type: 'preDisconnect', callback: Callback<void>): void
```

Registers a callback with the accessibility service, which is invoked before the accessibility service closes this Accessibility Extension Service. This API uses an asynchronous callback to return the result.

This registration function must be used together with [notifyDisconnect](#notifydisconnect). If [notifyDisconnect](#notifydisconnect) is not called, the Accessibility Extension Service is automatically closed after a default wait of 30 seconds.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preDisconnect' | Yes | Listening event name, which is fixed to 'preDisconnect', indicating the event that the Accessibility Extension Service is about to be closed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the Accessibility Extension Service is about to be closed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## removeAccessibilityVirtualNodes

```TypeScript
removeAccessibilityVirtualNodes(elementId: number, windowId: number): Promise<OperateVirtualNodeResult>
```

Deletes the added accessibility virtual node tree. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementId | number | Yes | ID of the node where the virtual node tree to be deleted is located. |
| windowId | number | Yes | ID of the window where the virtual node tree to be deleted is located. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OperateVirtualNodeResult](arkts-accessibility-accessibility-operatevirtualnoderesult-e-sys.md)&gt; | Promise used to return the execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality.Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.IPC communication failed. <br>4.Failed to obtain the accessibility service proxy. <br>5.Timed out while waiting for the result of an asynchronous operation. |

**Examples**

```TypeScript
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

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

Starts a foreground page. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want type parameter, which passes in the information about the ability to start, such as the ability name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
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

## unholdRunningLockSync

```TypeScript
unholdRunningLockSync(): void
```

Releases the RunningLock and restores automatic screen-off. Used in pair with [holdRunningLockSync](#holdrunninglocksync).

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

## updateAccessibilityElementProperty

```TypeScript
updateAccessibilityElementProperty(elementId: number, windowId: number, node: AccessibilityVirtualNode): Promise<OperateVirtualNodeResult>
```

Modifies the accessibility node property. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementId | number | Yes | ID of the accessibility node to modify. |
| windowId | number | Yes | ID of the window of the accessibility node to modify. |
| node | [AccessibilityVirtualNode](arkts-accessibility-accessibilityextensioncontext-accessibilityvirtualnode-i-sys.md) | Yes | Property values of the accessibility node to modify. The modifiable properties include:<br>accessibilityText, accessibilityGroup, accessibilityLevel, checkable, checked, selected, clickable, enabled, customComponentType. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OperateVirtualNodeResult](arkts-accessibility-accessibility-operatevirtualnoderesult-e-sys.md)&gt; | Promise used to return the execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality.Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.IPC communication failed. <br>4.Failed to obtain the accessibility service proxy. <br>5.Timed out while waiting for the result of an asynchronous operation. |

**Examples**

```TypeScript
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
