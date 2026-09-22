# AccessibilityExtensionContext

```TypeScript
declare class AccessibilityExtensionContext extends ExtensionContext
```

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

## getFocusElement

```TypeScript
getFocusElement(isAccessibilityFocus: boolean, callback: AsyncCallback<AccessibilityElement>): void
```

Obtains the focus element. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAccessibilityFocus | boolean | Yes | Whether the element obtained is an accessibility focus element. The value **true** indicates that it is an accessibility focus element, and **false** indicates the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Yes | Callback invoked to return the result. If the focus element is obtained successfully, **err** is **undefined** and **data** is the corresponding focus element; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let isAccessibilityFocus = true;
let rootElement: AccessibilityElement;

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.getFocusElement(isAccessibilityFocus, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get focus element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting focus element, ${JSON.stringify(data)}`);
});
```

<a id="getfocuselement-1"></a>

## getFocusElement

```TypeScript
getFocusElement(isAccessibilityFocus?: boolean): Promise<AccessibilityElement>
```

Obtains the focus element. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAccessibilityFocus | boolean | No | Whether to obtain the accessibility focus element. The value **true** indicates that it is an accessibility focus element, and **false** indicates that it is not an accessibility focus element. Default value: **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the current focus element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext is an instance of AccessibilityExtensionContext, obtained through this.context of an AccessibilityExtensionAbility subclass. See the usage instructions for details.
axContext.getFocusElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.info(`succeeded in getting focus element,${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get focus element. Code: ${err.code}, message: ${err.message}`);
});
```

<a id="getfocuselement-2"></a>

## getFocusElement

```TypeScript
getFocusElement(callback: AsyncCallback<AccessibilityElement>): void
```

Obtains the focus element. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Yes | Callback used to return the focus element. If the operation is successful, **err** is **undefined** and **data** is the current focus element; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.getFocusElement((err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get focus element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting focus element, ${JSON.stringify(data)}`);
});
```

## getWindowRootElement

```TypeScript
getWindowRootElement(windowId: number, callback: AsyncCallback<AccessibilityElement>): void
```

Obtains the root element of the specified window. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | Number of the specified window. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Yes | Callback used to return the result. If the root node element is obtained successfully, **err** is **undefined** and **data** is the root node element of the specified window; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let windowId = 10;
let rootElement: AccessibilityElement;

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.getWindowRootElement(windowId, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get root element of the window. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting root element of the window, ${JSON.stringify(data)}`);
});
```

<a id="getwindowrootelement-1"></a>

## getWindowRootElement

```TypeScript
getWindowRootElement(windowId?: number): Promise<AccessibilityElement>
```

Obtains the root element of the specified window. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | No | ID of the window whose root element is to be obtained. If this parameter is not specified, it indicates the current active window. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the root element of the specified window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. See the usage instructions for details.
axContext.getWindowRootElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.info(`succeeded in getting root element of the window, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get root element of the window. Code: ${err.code}, message: ${err.message}`);
});
```

<a id="getwindowrootelement-2"></a>

## getWindowRootElement

```TypeScript
getWindowRootElement(callback: AsyncCallback<AccessibilityElement>): void
```

Obtains the root element of the currently active window. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Yes | Callback invoked to return the result. If the root node element is obtained successfully, err is undefined and data is the root node element of the currently active window; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage guide.
axContext.getWindowRootElement((err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get root element of the window. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting root element of the window, ${JSON.stringify(data)}`);
});
```

## getWindows

```TypeScript
getWindows(displayId: number, callback: AsyncCallback<Array<AccessibilityElement>>): void
```

Obtains all windows on the specified display. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | ID of the specified screen, used to identify the screen for which to obtain windows. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Yes | Callback used to return the result. If the windows are obtained successfully, **err** is **undefined** and **data** is all windows on the specified screen; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let displayId = 10;
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.getWindows(displayId, (err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
});
```

<a id="getwindows-1"></a>

## getWindows

```TypeScript
getWindows(displayId?: number): Promise<Array<AccessibilityElement>>
```

Obtains all windows on the specified display. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | No | ID of the display from which the window information is obtained. If this parameter is not specified, it indicates the default main display. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise used to return the window list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.getWindows().then((data: AccessibilityElement[]) => {
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
});
```

<a id="getwindows-2"></a>

## getWindows

```TypeScript
getWindows(callback: AsyncCallback<Array<AccessibilityElement>>): void
```

Obtains all windows on the default main display. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Yes | Callback invoked to return the result. If the window is obtained successfully, **err** is **undefined** and **data** is all windows of the default home screen; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. See usage instructions for details.
axContext.getWindows((err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
});
```

## injectGesture

```TypeScript
injectGesture(gesturePath: GesturePath, callback: AsyncCallback<void>): void
```

Injects a gesture, applicable to scenarios where an accessibility app performs touch interactions on behalf of the user, such as tap and swipe operations. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [injectGestureSync](#injectgesturesync)

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesturePath | [GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md) | Yes | Path of the gesture to inject. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the gesture injection is successful, **err** is **undefined**; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let gesturePath: GesturePath = new GesturePath(100);
for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage guide.
axContext.injectGesture(gesturePath, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to inject gesture. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in injecting gesture,gesturePath is ${gesturePath}`);
});
```

<a id="injectgesture-1"></a>

## injectGesture

```TypeScript
injectGesture(gesturePath: GesturePath): Promise<void>
```

Injects a gesture, applicable to scenarios where an accessibility app performs touch interactions on behalf of the user, such as tap and swipe operations. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [injectGestureSync](#injectgesturesync)

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesturePath | [GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md) | Yes | Path of the gesture to inject. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let gesturePath: GesturePath = new GesturePath(100);

for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.injectGesture(gesturePath).then(() => {
  console.info(`Succeeded in injecting gesture,gesturePath is ${gesturePath}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to inject gesture. Code: ${err.code}, message: ${err.message}`);
});
```

## injectGestureSync

```TypeScript
injectGestureSync(gesturePath: GesturePath): void
```

Injects a gesture, applicable to scenarios where an accessibility app performs touch interactions on behalf of the user, such as tap and swipe operations.

**Since:** 10

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesturePath | [GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md) | Yes | Path of the gesture to inject. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-no-accessibility-permission-to-perform-the-operation) | No accessibility permission to perform the operation. |

**Examples**

```TypeScript
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';

let gesturePath: GesturePath = new GesturePath(100);
for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.injectGestureSync(gesturePath);
```

## setTargetBundleName

```TypeScript
setTargetBundleName(targetNames: Array<string>, callback: AsyncCallback<void>): void
```

Sets the bundle name of the concerned app. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetNames | Array&lt;string&gt; | Yes | Package name of the app to focus on. After setting, the service receives accessibility events only from the focused app. If not set, accessibility events from all apps are received by default. To cancel the focus on an app, pass an empty array. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the target package name is set successfully, **err** is **undefined**; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNames = ['com.ohos.xyz'];
try {
  // axContext is an AccessibilityExtensionContext instance, obtained through this.context of the AccessibilityExtensionAbility subclass. For details, see the usage instructions.
  axContext.setTargetBundleName(targetNames, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set target bundle names. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`succeeded in setting target bundle names, targetNames is ${targetNames}`);
  });
} catch (error) {
  console.error(`Failed to set target bundle names. Code: ${error.code}, message: ${error.message}`);
}
```

<a id="settargetbundlename-1"></a>

## setTargetBundleName

```TypeScript
setTargetBundleName(targetNames: Array<string>): Promise<void>
```

Sets the bundle name of the concerned app. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetNames | Array&lt;string&gt; | Yes | Sets the package names of the apps of interest. After setting, the service receives only accessibility events of the apps of interest. If not set, the service receives accessibility events of all apps by default. To cancel the focus on apps, pass an empty array. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNames = ['com.ohos.xyz'];
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.setTargetBundleName(targetNames).then(() => {
  console.info(`succeeded in setting target bundle names, targetNames is ${targetNames}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set target bundle names. Code: ${err.code}, message: ${err.message}`);
});
```
