# AccessibilityExtensionContext (Accessibility Extension Context)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->

The **AccessibilityExtensionContext** module, inherited from **ExtensionContext**, provides context for **AccessibilityExtensionAbility**.

You can use the APIs of this module to configure the concerned information, obtain root information, and inject gestures.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Usage

Before using the **AccessibilityExtensionContext** module, you must define a child class that inherits from **AccessibilityExtensionAbility**.

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class EntryAbility extends AccessibilityExtensionAbility {
  onConnect(): void {
    let axContext = this.context; 
  } 
}
```

## ElementAttributeValues

Provides attribute names and value types of a node element.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

### Attributes

| Name                  | Type                                                             | Read-Only| Optional| Description             |
|----------------------|--------------------------------------------------------------------|------|------|-------------------|
| accessibilityFocused | boolean                                                            | No  | No  | Whether the element is focused for accessibility purposes. The value **true** indicates that the element is focused, and **false** indicates the opposite.<br>Default value: **false**.|
| accessibilityText<sup>12+</sup> | string                                                  | No  | No  | Accessibility text information of an element.|
| bundleName           | string                                                             | No  | No  | Bundle name.|
| checkable            | boolean                                                            | No  | No  | Whether the element is checkable. The value **true** indicates that the element is checkable, and **false** indicates the opposite.<br>Default value: **false**.|
| checked              | boolean                                                            | No  | No  | Whether the element is checked. The value **true** indicates that the element is checked, and **false** indicates the opposite.<br>Default value: **false**.|
| children             | Array&lt;[AccessibilityElement](#accessibilityelement9)&gt;        | No  | No  | All child elements.|
| clickable            | boolean                                                            | No  | No  | Whether the element is clickable. The value **true** indicates that the element is clickable, and **false** indicates the opposite.<br>Default value: **false**.|
| componentId          | number                                                             | No  | No  | ID of the component to which the element belongs. <br>Default value: **-1**.|
| componentType        | string                                                             | No  | No  | Type of the component to which the element belongs, for example, **Button** for the button component and **Image** for the image component.|
| contents             | Array&lt;string&gt;                                                | No  | No  | List of contents. Set this parameter based on site requirements. No special restrictions.|
| currentIndex         | number                                                             | No  | No  | Index of the current item. <br>Default value: **0**.|
| description          | string                                                             | No  | No  | Description of the element. Set this parameter based on site requirements. No special restrictions.|
| editable             | boolean                                                            | No  | No  | Whether the element is editable. The value **true** indicates that the element is editable, and **false** indicates the opposite.<br>Default value: **false**.|
| endIndex             | number                                                             | No  | No  | Index of the last list item displayed on the screen. <br>Default value: **0**.|
| error                | string                                                             | No  | No  | Error status.|
| focusable            | boolean                                                            | No  | No  | Whether the element is focusable. The value **true** indicates that the element is focusable, and **false** indicates the opposite.<br>Default value: **false**.|
| hintText             | string                                                             | No  | No  | Hint text.|
| inputType            | number                                                             | No  | No  | Type of the input text. <br>Default value: **0**.|
| inspectorKey         | string                                                             | No  | No  | Inspector key.|
| isActive             | boolean                                                            | No  | No  | Whether the element is active. The value **true** indicates that the element is active and **false** indicates the opposite.<br>Default value: **true**.|
| isEnable             | boolean                                                            | No  | No  | Whether the element is enabled. The value **true** indicates that the element is enabled, and **false** indicates the opposite.<br>Default value: **false**.|
| isHint               | boolean                                                            | No  | No  | Whether the element is a hint. The value **true** indicates that the element is a hint, and **false** indicates the opposite.<br>Default value: **false**.|
| isFocused            | boolean                                                            | No  | No  | Whether the element is focused. The value **true** indicates that the element is focused, and **false** indicates the opposite.<br>Default value: **false**.|
| isPassword           | boolean                                                            | No  | No  | Whether the element is a password. The value **true** indicates that the element is a password, and **false** indicates the opposite.<br>Default value: **false**.|
| isVisible            | boolean                                                            | No  | No  | Whether the element is visible. The value **true** indicates that the element is visible, and **false** indicates the opposite.<br>Default value: **false**.|
| itemCount            | number                                                             | No  | No  | Total number of items. <br>Default value: **0**.|
| lastContent          | string                                                             | No  | No  | Last content.|
| layer                | number                                                             | No  | No  | Display layer of the element.|
| longClickable        | boolean                                                            | No  | No  | Whether the element is long-clickable. The value **true** indicates that the element is long-clickable, and **false** indicates the opposite.<br>Default value: **false**.|
| pageId               | number                                                             | No  | No  | Page ID. <br>Default value: **-1**.|
| parent               | [AccessibilityElement](#accessibilityelement9)                     | No  | No  | Parent element of the element.|
| pluralLineSupported  | boolean                                                            | No  | No  | Whether the element supports multiple lines of text. The value **true** indicates that the element supports multiple lines of text, and **false** indicates the opposite.<br>Default value: **false**.|
| rect                 | [Rect](#rect)                                                      | No  | No  | Area of the element.|
| resourceName         | string                                                             | No  | No  | Resource name of the element.|
| rootElement          | [AccessibilityElement](#accessibilityelement9)                     | No  | No  | Root element of the window element.|
| screenRect           | [Rect](#rect)                                                      | No  | No  | Display area of the element.|
| scrollable           | boolean                                                            | No  | No  | Whether the element is scrollable. The value **true** indicates that the element is scrollable, and **false** indicates the opposite.<br>Default value: **false**.|
| selected             | boolean                                                            | No  | No  | Whether the element is selected. The value **true** indicates that the element is selected, and **false** indicates the opposite.<br>Default value: **false**.|
| startIndex           | number                                                             | No  | No  | Index of the first list item on the screen. <br>Default value: **0**.|
| text                 | string                                                             | No  | No  | Text of the element.|
| textLengthLimit      | number                                                             | No  | No  | Maximum text length of the element.|
| textMoveUnit         | [accessibility.TextMoveUnit](js-apis-accessibility.md#textmoveunit)| No  | No  | Unit of movement when the text is read.|
| triggerAction        | [accessibility.Action](js-apis-accessibility.md#action)            | No  | No  | Action that triggers the element event.|
| type                 | [WindowType](#windowtype)                                          | No  | No  | Window type of the element.|
| valueMax             | number                                                             | No  | No  | Maximum value. <br>Default value: **0**.|
| valueMin             | number                                                             | No  | No  | Minimum value. <br>Default value: **0**.|
| valueNow             | number                                                             | No  | No  | Current value. <br>Default value: **0**.|
| windowId             | number                                                             | No  | No  | Window ID. <br>Default value: **-1**.|
| textType<sup>12+</sup>             | string                                                             | No  | No  | Accessibility text type of an element, which is configured by the **accessibilityTextHint** attribute of the component.|
| offset<sup>12+</sup>             | number              | No  | No  | Pixel offset of the content area relative to the top coordinate of a scrollable component, such as **List** and **Grid**. <br>Default value: **0**.|
| hotArea<sup>12+</sup>             | [Rect](#rect)                                                              | No  | No  | Touchable area of an element.|
| customComponentType<sup>18+</sup>             | string                                                             | No  | Yes  | Custom component type.|
| accessibilityNextFocusId<sup>18+</sup>             | number                | No  | Yes  | ID of the next component to be focused on. You can use **findElement('elementId')** to obtain the value of this attribute set on the component from the **AccessibilityElementInfo** object. <br>Default value: **-1**.|
| accessibilityPreviousFocusId<sup>18+</sup>             | number                | No  | Yes  | ID of the previous component to be focused on. You can use **findElement('elementId')** to obtain the value of this attribute set on the component from the **AccessibilityElementInfo** object. <br>Default value: **-1**.|
| extraInfo<sup>18+</sup>             | string     | No | Yes  | Extended attributes, which are used to define the attributes of specific components, including:<br>- **CheckboxGroupSelectedStatus**: selection status of the **CheckboxGroup** component. The options are as follows:<br>**0**: selected<br>**1**: partially selected<br>**2**: not selected<br>- **Row**: row where a focused item is located in **Grid**.<br>- **Column**: column where a focused item is located in **Grid**.<br>- **ListItemIndex**: row where a focused item is located in **List**.<br>- **SideBarContainerStates**: expansion state of the expandable components (such as **SideBarContainer** and **Select**). The options are as follows:<br>**0**: collapsed<br>**1**: expanded<br>- **ToggleType**: type of the **Toggle** component. The options are as follows:<br>**0**: checkbox<br>**1**: switch<br>**2**: button<br>- **BindSheet**: position of the **BindSheet** component on the screen. The options are as follows:<br>**0**: high<br>**1**: middle<br>**2**: low<br>- **hasRegisteredHover**: whether the component has registered the **onAccessibilityHover** event callback. The value **1** indicates that the component has registered the event callback; otherwise, this field is not used.<br>- **direction**: layout direction of the **List** component. The value can be **vertical** or **horizontal**.<br>- **expandedState**: expanded state of list items in the **List** component. The value can be **expanded** or **collapsed**.<br>- **componentTypeDescription**: detailed information about the component type.|
| accessibilityScrollable<sup>18+</sup>             | boolean                 | No  | Yes  | Whether an element is scrollable for accessibility. This attribute has a higher priority than **scrollable**. <br>- **true** (default): the element is scrollable.<br>- **false**: the element is not scrollable.|

## FocusDirection

type FocusDirection = 'up' | 'down' | 'left' | 'right' | 'forward' | 'backward'

Enumerates the focus directions.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type      | Description     |
| -------- | ------- |
| 'up'       | Search for the next focusable item above the current item in focus.|
| 'down'     | Search for the next focusable item below the current item in focus.|
| 'left'     | Search for the next focusable item on the left of the current item in focus.|
| 'right'    | Search for the next focusable item on the right of the current item in focus.|
| 'forward'  | Search for the next focusable item before the current item in focus.|
| 'backward' | Search for the next focusable item after the current item in focus.|

## FocusType

type FocusType = 'accessibility' | 'normal'

Enumerates the focus types.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type           | Description         |
| ------------- | ----------- |
| 'accessibility' | Accessibility focus.|
| 'normal'        | Normal focus. |

## Rect

Defines a rectangle.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Name    | Type    | Read-Only  | Optional  | Description       |
| ------ | ------ | ---- | ---- | --------- |
| left   | number | No   | No   | Left boundary of the rectangle.|
| top    | number | No   | No   | Top boundary of the rectangle.|
| width  | number | No   | No   | Width of the rectangle. |
| height | number | No   | No   | Height of the rectangle. |

## WindowType

type WindowType = 'application' | 'system'

Enumerates the window types.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type         | Description       |
| ----------- | --------- |
| 'application' | Application window.|
| 'system'      | System window.|

## AccessibilityExtensionContext.setTargetBundleName<sup>(deprecated)</sup>

setTargetBundleName(targetNames: Array\<string>): Promise\<void>;

Sets the concerned target bundle. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                 | Mandatory  | Description      |
| ----------- | ------------------- | ---- | -------- |
| targetNames | Array&lt;string&gt; | Yes   | Bundle name of the concerned target application. The service receives accessibility events of the concerned application. By default, accessibility events of all applications are received. Pass in an empty array if there is no concerned application.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let targetNames = ['com.ohos.xyz'];
axContext.setTargetBundleName(targetNames).then(() => {
  console.info(`Succeeded in set target bundle names, targetNames is ${targetNames}`);
}).catch((err: BusinessError) => {
  console.error(`failed to set target bundle names, Code is ${err.code}, message is ${err.message}`);
})
```

## AccessibilityExtensionContext.setTargetBundleName<sup>(deprecated)</sup>

setTargetBundleName(targetNames: Array\<string>, callback: AsyncCallback\<void>): void;

Sets the concerned target bundle. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                       | Mandatory  | Description                                      |
| ----------- | ------------------------- | ---- | ---------------------------------------- |
| targetNames | Array&lt;string&gt;       | Yes   | Bundle name of the concerned target application. The service receives accessibility events of the concerned application. By default, accessibility events of all applications are received. Pass in an empty array if there is no concerned application.                                |
| callback    | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation fails, **err** that contains data is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let targetNames = ['com.ohos.xyz'];
try {
  axContext.setTargetBundleName(targetNames, (err: BusinessError) => {
    if (err && err.code) {
      console.error(`failed to set target bundle names, Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Succeeded in set target bundle names, targetNames is ${targetNames}`);
  });
} catch (error) {
  console.error(`failed to set target bundle names, Because ${JSON.stringify(error)}`);
}
```

## AccessibilityExtensionContext.getFocusElement<sup>(deprecated)</sup>

getFocusElement(isAccessibilityFocus?: boolean): Promise\<AccessibilityElement>;

Obtains the focus element. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name                 | Type     | Mandatory  | Description                 |
| -------------------- | ------- | ---- | ------------------- |
| isAccessibilityFocus | boolean | No   | Whether the obtained element is an accessibility focus. The value **true** indicates that the element is an accessibility focus, and **false** indicates the opposite.<br>Default value: **false**.|

**Return value**
| Type                                 | Description                    |
| ----------------------------------- | ---------------------- |
| Promise&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Promise used to return the current focus element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

axContext.getFocusElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.log(`Succeeded in get focus element,${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get focus element, Code is ${err.code}, message is ${err.message}`);
})
```

## AccessibilityExtensionContext.getFocusElement<sup>(deprecated)</sup>

getFocusElement(callback: AsyncCallback\<AccessibilityElement>): void;

Obtains the focus element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description               |
| -------- | ---------------------------------------- | ---- | ----------------- |
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Yes   | Callback used to return the current focus element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

axContext.getFocusElement((err: BusinessError, data: AccessibilityElement) => {
  if (err && err.code) {
    console.error(`failed to get focus element, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`Succeeded in get focus element, ${JSON.stringify(data)}`);
});
```

## AccessibilityExtensionContext.getFocusElement<sup>(deprecated)</sup>

getFocusElement(isAccessibilityFocus: boolean, callback: AsyncCallback\<AccessibilityElement>): void;

Obtains the focus element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name                 | Type                                      | Mandatory  | Description               |
| -------------------- | ---------------------------------------- | ---- | ----------------- |
| isAccessibilityFocus | boolean                                  | Yes   | Whether the obtained focus element is an accessibility focus. The value **True** means that the obtained focus element is an accessibility focus, and **False** means the opposite.   |
| callback             | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Yes   | Callback used to return the current focus element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let isAccessibilityFocus = true;
let rootElement: AccessibilityElement;

axContext.getFocusElement(isAccessibilityFocus, (err: BusinessError, data: AccessibilityElement)=> {
  if (err && err.code) {
    console.error(`failed to get focus element, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`Succeeded in get focus element, ${JSON.stringify(data)}`);
});
```

## AccessibilityExtensionContext.getWindowRootElement<sup>(deprecated)</sup>

getWindowRootElement(windowId?: number): Promise\<AccessibilityElement>;

Obtains the root element of a window. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                    |
| -------- | ------ | ---- | ---------------------- |
| windowId | number | No   | Window for which you want to obtain the root element. If this parameter is not specified, it indicates the current active window.|

**Return value**

| Type                                 | Description                    |
| ----------------------------------- | ---------------------- |
| Promise&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Promise used to return the root element of the specified window.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

axContext.getWindowRootElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.log(`Succeeded in get root element of the window, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get root element of the window, Code is ${err.code}, message is ${err.message}`);
});
```

## AccessibilityExtensionContext.getWindowRootElement<sup>(deprecated)</sup>

getWindowRootElement(callback: AsyncCallback\<AccessibilityElement>): void;

Obtains the root element of a window. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                |
| -------- | ---------------------------------------- | ---- | ------------------ |
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Yes   | Callback used to return the root element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

axContext.getWindowRootElement((err: BusinessError, data: AccessibilityElement) => {
  if (err && err.code) {
    console.error(`failed to get root element of the window, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`Succeeded in get root element of the window, ${JSON.stringify(data)}`);
});
```

## AccessibilityExtensionContext.getWindowRootElement<sup>(deprecated)</sup>

getWindowRootElement(windowId: number, callback: AsyncCallback\<AccessibilityElement>): void;

Obtains the root element of a window. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                    |
| -------- | ---------------------------------------- | ---- | ---------------------- |
| windowId | number                                   | Yes   | Window for which you want to obtain the root element. If this parameter is not specified, it indicates the current active window.|
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Yes   | Callback used to return the root element.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let windowId = 10;
let rootElement: AccessibilityElement;

axContext.getWindowRootElement(windowId, (err: BusinessError, data: AccessibilityElement) => {
  if (err && err.code) {
    console.error(`failed to get root element of the window, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`Succeeded in get root element of the window, ${JSON.stringify(data)}`);
});
```

## AccessibilityExtensionContext.getWindows<sup>(deprecated)</sup>

getWindows(displayId?: number): Promise\<Array\<AccessibilityElement>>;

Obtains the list of windows on a display. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type    | Mandatory  | Description                   |
| --------- | ------ | ---- | --------------------- |
| displayId | number | No   | ID of the display from which the window information is obtained. If this parameter is not specified, it indicates the default main display.|

**Return value**

| Type                                      | Description                    |
| ---------------------------------------- | ---------------------- |
| Promise&lt;Array&lt;[AccessibilityElement](#accessibilityelement9)&gt;&gt; | Promise used to return the window list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

axContext.getWindows().then((data: AccessibilityElement[]) => {
  console.log(`Succeeded in get windows, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get windows, Code is ${err.code}, message is ${err.message}`);
});
```

## AccessibilityExtensionContext.getWindows<sup>(deprecated)</sup>

getWindows(callback: AsyncCallback\<Array\<AccessibilityElement>>): void;

Obtains the list of windows on a display. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description               |
| -------- | ---------------------------------------- | ---- | ----------------- |
| callback | AsyncCallback&lt;Array&lt;[AccessibilityElement](#accessibilityelement9)&gt;&gt; | Yes   | Callback used to return the window list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

axContext.getWindows((err: BusinessError, data: AccessibilityElement[]) => {
  if (err && err.code) {
    console.error(`failed to get windows, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in get windows, ${JSON.stringify(data)}`);
});
```

## AccessibilityExtensionContext.getWindows<sup>(deprecated)</sup>

getWindows(displayId: number, callback: AsyncCallback\<Array\<AccessibilityElement>>): void;

Obtains the list of windows on a display. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                   |
| --------- | ---------------------------------------- | ---- | --------------------- |
| displayId | number                                   | Yes   | ID of the display from which the window information is obtained. If this parameter is not specified, it indicates the default main display.|
| callback  | AsyncCallback&lt;Array&lt;[AccessibilityElement](#accessibilityelement9)&gt;&gt; | Yes   | Callback used to return the window list.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let displayId = 10;
axContext.getWindows(displayId, (err: BusinessError, data: AccessibilityElement[]) => {
  if (err && err.code) {
    console.error(`failed to get windows, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in get windows, ${JSON.stringify(data)}`);
});
```

## AccessibilityExtensionContext.injectGesture<sup>(deprecated)</sup>

injectGesture(gesturePath: GesturePath): Promise\<void>;

> **NOTE**
>
> This API is deprecated since API version 10. Related capabilities are no longer available in the system.

Injects a gesture. This API uses a promise to return the result.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                                                | Mandatory  | Description        |
| ----------- |--------------------------------------------------------------------| ---- | ---------- |
| gesturePath | [GesturePath](js-apis-accessibility-GesturePath.md#gesturepath) | Yes   | Path of the gesture to inject.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let gesturePath: GesturePath = new GesturePath(100);

for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
axContext.injectGesture(gesturePath).then(() => {
  console.info(`Succeeded in inject gesture,gesturePath is ${gesturePath}`);
}).catch((err: BusinessError) => {
  console.error(`failed to inject gesture, Code is ${err.code}, message is ${err.message}`);
});
```
## AccessibilityExtensionContext.injectGesture<sup>(deprecated)</sup>

injectGesture(gesturePath: GesturePath, callback: AsyncCallback\<void>): void

> **NOTE**
>
> This API is deprecated since API version 10. Related capabilities are no longer available in the system.

Injects a gesture. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                                                | Mandatory  | Description                 |
| ----------- |--------------------------------------------------------------------| ---- | ------------------- |
| gesturePath | [GesturePath](js-apis-accessibility-GesturePath.md#gesturepath) | Yes   | Path of the gesture to inject.         |
| callback    | AsyncCallback&lt;void&gt;                                          | Yes   | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003 | No accessibility permission to perform the operation. |

**Example**

```ts
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let gesturePath: GesturePath = new GesturePath(100);
for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
axContext.injectGesture(gesturePath, (err: BusinessError) => {
  if (err) {
    console.error(`failed to inject gesture, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in inject gesture,gesturePath is ${gesturePath}`);
});
```
## AccessibilityExtensionContext.injectGestureSync<sup>(deprecated)</sup>

injectGestureSync(gesturePath: GesturePath): void

Injects a gesture.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                                                | Mandatory| Description                |
| ----------- |--------------------------------------------------------------------| ---- | -------------------- |
| gesturePath | [GesturePath](js-apis-accessibility-GesturePath.md#gesturepath) | Yes  | Path of the gesture to inject.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID| Error Message                                           |
| -------- | --------------------------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300003  | No accessibility permission to perform the operation. |

**Example**

```ts
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';

let gesturePath: GesturePath = new GesturePath(100);
for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
axContext.injectGestureSync(gesturePath);
```

## AccessibilityElement<sup>9+</sup>

Defines the **AccessibilityElement**. Before calling APIs of **AccessibilityElement**, you must call [AccessibilityExtensionContext.getFocusElement()](#accessibilityextensioncontextgetfocuselementdeprecated) or [AccessibilityExtensionContext.getWindowRootElement()](#accessibilityextensioncontextgetwindowrootelementdeprecated) to obtain an **AccessibilityElement** instance.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

### attributeNames<sup>(deprecated)</sup>

attributeNames\<T extends keyof ElementAttributeValues>() : Promise\<Array\<T>>;

Obtains all attribute names of this element. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                           | Description                      |
| ----------------------------- | ------------------------ |
| Promise&lt;Array&lt;T&gt;&gt; | Promise used to return all attribute names of the element.|

**Example**

```ts
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement.
rootElement.attributeNames().then((data: ElementAttributeKeys[]) => {
  console.log(`Succeeded in get attribute names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.log(`failed to get attribute names, Code is ${err.code}, message is ${err.message}`);
});
```

### attributeNames<sup>(deprecated)</sup>

attributeNames\<T extends keyof ElementAttributeValues>(callback: AsyncCallback\<Array\<T>>): void;

Obtains all attribute names of this element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                 | Mandatory  | Description                 |
| -------- | ----------------------------------- | ---- | ------------------- |
| callback | AsyncCallback&lt;Array&lt;T&gt;&gt; | Yes   | Callback used to return all attribute names of the element.|

**Example**

```ts
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement.
rootElement.attributeNames((err: BusinessError, data: ElementAttributeKeys[]) => {
  if (err && err.code) {
    console.error(`failed to get attribute names, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in get attribute names, ${JSON.stringify(data)}`);
});
```

### attributeValue<sup>(deprecated)</sup>

attributeValue\<T extends keyof ElementAttributeValues>(attributeName: T): Promise\<ElementAttributeValues[T]>;

Obtains the attribute value based on an attribute name. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core


**Parameters**

| Name          | Type  | Mandatory  | Description      |
| ------------- | ---- | ---- | -------- |
| attributeName | ElementAttributeKeys  | Yes   | Attribute name.|

**Return value**

| Type                                      | Description                         |
| ---------------------------------------- | --------------------------- |
| Promise&lt;ElementAttributeValues[T]&gt; | Promise used to return the attribute value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300004 | This property does not exist. |


**Example**

```ts
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let attributeName: ElementAttributeKeys = 'bundleName';

// rootElement is an instance of AccessibilityElement.
rootElement.attributeValue(attributeName).then((data: string) => {
  console.log(`Succeeded in get attribute value by name, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get attribute value, Code is ${err.code}, message is ${err.message}`);
});
```

### attributeValue<sup>(deprecated)</sup>

attributeValue\<T extends keyof ElementAttributeValues>(attributeName: T, 
    callback: AsyncCallback\<ElementAttributeValues[T]>): void;

Obtains the attribute value based on an attribute name. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name          | Type                                      | Mandatory  | Description                    |
| ------------- | ---------------------------------------- | ---- | ---------------------- |
| attributeName | ElementAttributeKeys                         | Yes   | Attribute name.              |
| callback      | AsyncCallback&lt;ElementAttributeValues[T]&gt; | Yes   | Callback used to return the attribute value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300004 | This property does not exist. |

**Example**

```ts
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let attributeName: ElementAttributeKeys = 'bundleName';

// rootElement is an instance of AccessibilityElement.
rootElement.attributeValue(attributeName, (err: BusinessError, data: string) => {
  if (err && err.code) {
    console.error(`failed to get attribute value, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in get attribute value, ${JSON.stringify(data)}`);
});
```

### actionNames<sup>(deprecated)</sup>

actionNames(): Promise\<Array\<string>>;

Obtains the names of all actions supported by this element. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                                | Description                        |
| ---------------------------------- | -------------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the names of all actions supported by the element.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement.
rootElement.actionNames().then((data: string[]) => {
  console.log(`Succeeded in get action names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get action names, Code is ${err.code}, message is ${err.message}`);
})
```

### actionNames<sup>(deprecated)</sup>

actionNames(callback: AsyncCallback\<Array\<string>>): void;

Obtains the names of all actions supported by this element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                   |
| -------- | ---------------------------------------- | ---- | --------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes   | Callback used to return the names of all actions supported by the element.|

**Example**

```ts
// rootElement is an instance of AccessibilityElement.
rootElement.actionNames((err: BusinessError, data: string[]) => {
  if (err && err.code) {
    console.error(`failed to get action names, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in get action names, ${JSON.stringify(data)}`);
})
```

### performAction<sup>(deprecated)</sup>

performAction(actionName: string, parameters?: object): Promise\<void>;

Performs an action based on the specified action name. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                    | Mandatory  | Description                                                      |
| ----------- | ---------------------------------------- | ---- |----------------------------------------------------------|
| actionName | string | Yes   | Action name. For details, see [Action](./js-apis-accessibility.md#action). |
| parameters | object | No   | Parameters required for performing the target action. Empty by default.                            |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300005 | This action is not supported. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let actionName = 'action';

// rootElement is an instance of AccessibilityElement.
rootElement.performAction(actionName).then(() => {
  console.info(`Succeeded in perform action,actionName is ${actionName}`);
}).catch((err: BusinessError) => {
  console.error(`failed to perform action, Code is ${err.code}, message is ${err.message}`);
});
```

**Example of an action without parameters:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement.
// An action that does not require any parameter setting is an action without parameters, as specified in the action description.
rootElement.performAction('click').then(() => {
  console.info(`Succeeded in perform action.`);
}).catch((err: BusinessError) => {
  console.error(`failed to perform action, Code is ${err.code}, message is ${err.message}`);
});
```

**Example of an action with parameters:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement.
// Sample code of setSelection
rootElement.performAction('setSelection', {
  selectTextBegin: '0', // Indicates the start position of selection.
  selectTextEnd: '8',   // Indicates the end position of selection.
  selectTextInForWard: true   // true indicates the insertion point, and false indicates the selection range.
}).then(() => {
  console.info(`Succeeded in perform action`);
}).catch((err: BusinessError) => {
  console.error(`failed to perform action, Code is ${err.code}, message is ${err.message}`);
});
```

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement.
// Sample code of setCursorPosition
rootElement.performAction('setCursorPosition', {
  offset: '1'   // Position of the cursor.
}).then(() => {
  console.info(`Succeeded in perform action`);
}).catch((err: BusinessError) => {
  console.error(`failed to perform action, Code is ${err.code}, message is ${err.message}`);
});
```

### performAction<sup>(deprecated)</sup>

performAction(actionName: string, callback: AsyncCallback\<void>): void;

Performs an action based on the specified action name. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                    | Mandatory  | Description            |
| ----------- | ---------------------------------------- | ---- | -------------- |
| actionName | string | Yes   | Action name. For details, see [Action](./js-apis-accessibility.md#action).
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300005 | This action is not supported. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let actionName = 'action';

// rootElement is an instance of AccessibilityElement.
rootElement.performAction(actionName, (err: BusinessError) => {
  if (err && err.code) {
    console.error(`failed to perform action, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in perform action, actionName is ${actionName}`);
});
```

### performAction<sup>(deprecated)</sup>

performAction(actionName: string, parameters: object, callback: AsyncCallback\<void>): void;

Performs an action based on the specified action name. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name       | Type                       | Mandatory  | Description                                                         |
| ---------- | ------------------------- | ---- |-------------------------------------------------------------|
| actionName | string                    | Yes   | Action name. For details, see [Action](./js-apis-accessibility.md#action).|
| parameters | object                    | Yes   | Parameters required for performing the target action. Empty by default.                               |
| callback   | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result.                                          |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300005 | This action is not supported. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let actionName = 'action';
let parameters: object = [];

// rootElement is an instance of AccessibilityElement.
rootElement.performAction(actionName, parameters, (err: BusinessError) => {
  if (err && err.code) {
    console.error(`failed to perform action, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in perform action,actionName is ${actionName}, parameters is ${parameters}`);
});
```

### findElement('content')<sup>(deprecated)</sup>

findElement(type: 'content', condition: string): Promise\<Array\<AccessibilityElement>>;

Finds an element based on the content type. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type    | Mandatory  | Description                           |
| --------- | ------ | ---- | ----------------------------- |
| type      | string | Yes   | Type of element finding. The value is fixed at **'content'**.|
| condition | string | Yes   | Search criteria.                     |

**Return value**

| Type                                      | Description                           |
| ---------------------------------------- | ----------------------------- |
| Promise&lt;Array&lt;[AccessibilityElement](#accessibilityelement9)&gt;&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let condition = 'keyword';

// rootElement is an instance of AccessibilityElement.
rootElement.findElement('content', condition).then((data: AccessibilityElement[]) => {
  console.log(`Succeeded in find element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to find element, Code is ${err.code}, message is ${err.message}`);
});
```

### findElement('content')<sup>(deprecated)</sup>

findElement(type: 'content', condition: string, callback: AsyncCallback\<Array\<AccessibilityElement>>): void;

Finds an element based on the content type. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                          |
| --------- | ---------------------------------------- | ---- | ---------------------------- |
| type      | string                                   | Yes   | Type of element finding. The value is fixed at **'content'**.|
| condition | string                                   | Yes   | Search criteria.                    |
| callback  | AsyncCallback&lt;Array&lt;[AccessibilityElement](#accessibilityelement9)&gt;&gt; | Yes   | Callback used to return the result.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let condition = 'keyword';

// rootElement is an instance of AccessibilityElement.
rootElement.findElement('content', condition, (err: BusinessError, data: AccessibilityElement[])=>{
  if (err && err.code) {
    console.error(`failed to find element, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in find element, ${JSON.stringify(data)}`);
});
```

### findElement('focusType')<sup>(deprecated)</sup>

findElement(type: 'focusType', condition: FocusType): Promise\<AccessibilityElement>;

Finds an element based on the focus type. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                     | Mandatory  | Description                                |
| --------- | ----------------------- | ---- | ---------------------------------- |
| type      | string                  | Yes   | Type of element finding. The value is fixed at **'focusType'**.|
| condition | [FocusType](#focustype) | Yes   | Focus type.                      |

**Return value**

| Type                                 | Description                            |
| ----------------------------------- | ------------------------------ |
| Promise&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusType } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusType = 'normal';

// rootElement is an instance of AccessibilityElement.
rootElement.findElement('focusType', condition).then((data: AccessibilityElement) => {
  console.log(`Succeeded in find element,${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to find element, Code is ${err.code}, message is ${err.message}`);
});
```

### findElement('focusType')<sup>(deprecated)</sup>

findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback\<AccessibilityElement>): void;

Finds an element based on the focus type. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                                |
| --------- | ---------------------------------------- | ---- | ---------------------------------- |
| type      | string                                   | Yes   | Type of element finding. The value is fixed at **'focusType'**.|
| condition | [FocusType](#focustype)                  | Yes   | Focus type.                      |
| callback  | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Yes   | Callback used to return the result.         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusType } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusType = 'normal';

// rootElement is an instance of AccessibilityElement.
rootElement.findElement('focusType', condition, (err: BusinessError, data: AccessibilityElement)=>{
  if (err && err.code) {
    console.error(`failed to find element, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in find element, ${JSON.stringify(data)}`);
});
```

### findElement('focusDirection')<sup>(deprecated)</sup>

findElement(type: 'focusDirection', condition: FocusDirection): Promise\<AccessibilityElement>;

Finds an element based on the focus direction. This API uses a promise to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                               | Mandatory  | Description                                      |
| --------- | --------------------------------- | ---- | ---------------------------------------- |
| type      | string                            | Yes   | Type of element finding. The value is fixed at **'focusDirection'**.|
| condition | [FocusDirection](#focusdirection) | Yes   | Focus direction.                          |

**Return value**

| Type                                 | Description                              |
| ----------------------------------- | -------------------------------- |
| Promise&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusDirection } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusDirection = 'up';

// rootElement is an instance of AccessibilityElement.
rootElement.findElement('focusDirection', condition).then((data: AccessibilityElement) => {
  console.log(`Succeeded in find element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to find element, Code is ${err.code}, message is ${err.message}`);
});
```

### findElement('focusDirection')<sup>(deprecated)</sup>

findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback\<AccessibilityElement>): void;

Finds an element based on the focus direction. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                                      |
| --------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type      | string                                   | Yes   | Type of element finding. The value is fixed at **'focusDirection'**.|
| condition | [FocusDirection](#focusdirection)        | Yes   | Direction of the next focus element.                          |
| callback  | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement9)&gt; | Yes   | Callback used to return the result.             |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusDirection } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusDirection = 'up';

// rootElement is an instance of AccessibilityElement.
rootElement.findElement('focusDirection', condition, (err: BusinessError, data: AccessibilityElement) =>{
  if (err && err.code) {
    console.error(`failed to find element, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in find element, ${JSON.stringify(data)}`);
});
```
