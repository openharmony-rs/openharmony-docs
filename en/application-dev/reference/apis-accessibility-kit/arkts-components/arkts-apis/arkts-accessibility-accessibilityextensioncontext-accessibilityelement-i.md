# AccessibilityElement

An accessibility node element that provides capabilities such as querying parent/child elements, finding elements by content or focus direction, and performing accessibility actions. It is applicable to scenarios where an accessibility app needs to interact with and operate on UI nodes.

Before calling methods of AccessibilityElement, obtain an AccessibilityElement instance through [AccessibilityExtensionContext.getAccessibilityFocusedElement()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getaccessibilityfocusedelement) or [AccessibilityExtensionContext.getRootInActiveWindow()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getrootinactivewindow).

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## actionNames

```TypeScript
actionNames(callback: AsyncCallback<Array<string>>): void
```

Obtains the names of all actions supported by the node element. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. If the action names are obtained successfully, **err** is **undefined** and **data** contains all action names supported by the node element; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.actionNames().then((data: string[]) => {
  console.info(`succeeded in getting action names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get action names. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.actionNames((err: BusinessError, data: string[]) => {
  if (err) {
    console.error(`Failed to get action names. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting action names, ${JSON.stringify(data)}`);
});
```

## actionNames

```TypeScript
actionNames(): Promise<Array<string>>
```

Obtains the names of all actions supported by the node element. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the names of all actions supported by the element. |

**Examples**

See [actionNames](#actionnames)

## attributeNames

```TypeScript
attributeNames<T extends keyof ElementAttributeValues>(callback: AsyncCallback<Array<T>>): void
```

Obtains all attribute names of the node element. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;T&gt;&gt; | Yes | Callback invoked to return the result. If the attribute names are obtained successfully, **err** is undefined and **data** contains all attribute names of the node element; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.attributeNames().then((data: ElementAttributeKeys[]) => {
  console.info(`succeeded in getting attribute names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get attribute names. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.attributeNames((err: BusinessError, data: ElementAttributeKeys[]) => {
  if (err) {
    console.error(`Failed to get attribute names. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting attribute names, ${JSON.stringify(data)}`);
});
```

## attributeNames

```TypeScript
attributeNames<T extends keyof ElementAttributeValues>(): Promise<Array<T>>
```

Obtains all attribute names of the node element. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Promise used to return all attribute names of the element. |

**Examples**

See [attributeNames](#attributenames)

## attributeValue

```TypeScript
attributeValue<T extends keyof ElementAttributeValues>(
    attributeName: T,
    callback: AsyncCallback<ElementAttributeValues[T]>
  ): void
```

Obtains the attribute value based on an attribute name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attributeName | T | Yes | Attribute name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ElementAttributeValues[T]&gt; | Yes | Callback used to return the result. If the attribute value is obtained successfully, err is undefined and data is the value of the corresponding attribute; otherwise, the value is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300004](../errorcode-accessibility.md#9300004-attribute-does-not-exist) | This property does not exist. |

**Examples**

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let attributeName: ElementAttributeKeys = 'bundleName';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.attributeValue(attributeName).then((data: string) => {
  console.info(`succeeded in getting attribute value by name, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get attribute value. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let attributeName: ElementAttributeKeys = 'bundleName';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.attributeValue(attributeName, (err: BusinessError, data: string) => {
  if (err) {
    console.error(`Failed to get attribute value. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting attribute value, ${JSON.stringify(data)}`);
});
```

## attributeValue

```TypeScript
attributeValue<T extends keyof ElementAttributeValues>(attributeName: T): Promise<ElementAttributeValues[T]>
```

Obtains the attribute value based on the attribute name. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attributeName | T | Yes | Attribute name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ElementAttributeValues[T]&gt; | Promise used to return the attribute value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300004](../errorcode-accessibility.md#9300004-attribute-does-not-exist) | This property does not exist. |

**Examples**

See [attributeValue](#attributevalue)

## findElement('content')

```TypeScript
findElement(type: 'content', condition: string, callback: AsyncCallback<Array<AccessibilityElement>>): void
```

Finds an element based on the content type. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'content' | Yes | Fixed to 'content', which means the search type is node element content. |
| condition | string | Yes | Keyword condition for searching, used to match the text content of node elements. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Yes | Callback used to return the result. If the node elements are found successfully, **err** is **undefined** and **data** is all node elements that meet the specified search keyword; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## findElement('content')

```TypeScript
findElement(type: 'content', condition: string): Promise<Array<AccessibilityElement>>
```

Finds all node elements based on the node content. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'content' | Yes | The value is fixed at 'content', indicating that the search type is node element content. |
| condition | string | Yes | Keyword condition for the search, used to match the text content of the node element. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## findElement('focusType')

```TypeScript
findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback<AccessibilityElement>): void
```

Finds a node element based on the focus element type. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusType' | Yes | Type of element finding. The value is fixed at **'focusType'**. |
| condition | [FocusType](arkts-accessibility-focustype-t.md) | Yes | Focus type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Yes | Callback invoked to return the result. If the node element is found, **err** is **undefined** and **data** is the node element that matches the specified query focus element type; otherwise, an error object is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## findElement('focusType')

```TypeScript
findElement(type: 'focusType', condition: FocusType): Promise<AccessibilityElement>
```

Finds a node element based on the focus element type. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusType' | Yes | Type of element finding. The value is fixed at **'focusType'**. |
| condition | [FocusType](arkts-accessibility-focustype-t.md) | Yes | Focus type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## findElement('focusDirection')

```TypeScript
findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback<AccessibilityElement>): void
```

Finds a node element based on the next focus element direction. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusDirection' | Yes | Fixed value **'focusDirection'**, representing the query type as the direction of the next focus element of the node. |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | Yes | Direction for querying the next focus element. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Yes | Callback invoked to return the result. If the node element is found successfully, **err** is **undefined** and **data** is the node element that meets the specified direction for querying the next focus element; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## findElement('focusDirection')

```TypeScript
findElement(type: 'focusDirection', condition: FocusDirection): Promise<AccessibilityElement>
```

Finds a node element based on the next focus element direction. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusDirection' | Yes | Type of element finding. The value is fixed at **'focusDirection'**. |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | Yes | Focus direction. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## performAction

```TypeScript
performAction(actionName: string, parameters: object, callback: AsyncCallback<void>): void
```

Performs the specified action on the accessibility node element. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| actionName | string | Yes | Name of the action. For the value range, see [Action](arkts-accessibility-accessibility-action-t.md). |
| parameters | object | Yes | Parameters required for executing the action. Different action types require different parameter structures. For details about the parameter format, see the description of each Action. For example, setSelection requires the selectTextBegin, selectTextEnd, and selectTextInForWard parameters, and setCursorPosition requires the offset parameter. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked to return the result. If the action is executed successfully, err is undefined; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-operation-not-supported) | This action is not supported. |

**Examples**

```TypeScript
Action without parameters.
```

```TypeScript
Action with parameters (setSelection).
```

```TypeScript
Action with parameters (setCursorPosition).
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let actionName = 'action';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.performAction(actionName, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in performing action, actionName is ${actionName}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let actionName = 'action';
let parameters: object = {};

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.performAction(actionName, parameters, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in performing action,actionName is ${actionName}, parameters is ${parameters}`);
});
```

## performAction

```TypeScript
performAction(actionName: string, parameters?: object): Promise<void>
```

Performs the specified action on the accessibility node element. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| actionName | string | Yes | Name of the action. For the value range, see [Action](arkts-accessibility-accessibility-action-t.md). |
| parameters | object | No | Parameters required for executing the action. Different actions require different parameter key names and value types. For details about the value principles, see the definition of each Action. For example, setSelection requires the selectTextBegin, selectTextEnd, and selectTextInForWard parameters, and setCursorPosition requires the offset parameter. If not passed, this parameter is empty by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-operation-not-supported) | This action is not supported. |

**Examples**

See [performAction](#performaction)

## performAction

```TypeScript
performAction(actionName: string, callback: AsyncCallback<void>): void
```

Performs the specified action on the accessibility node element. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| actionName | string | Yes | Name of the action. For the value range, see [Action](arkts-accessibility-accessibility-action-t.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the operation is executed. If the operation succeeds, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-operation-not-supported) | This action is not supported. |

**Examples**

See [performAction](#performaction)
