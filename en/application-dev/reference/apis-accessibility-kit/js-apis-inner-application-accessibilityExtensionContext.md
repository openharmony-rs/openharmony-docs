# AccessibilityExtensionContext

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=16a51cad246d07c6caba5c76444e9d073c5d43d6 translatedAt=2026-08-03T09:50:10.910Z pushedAt=2026-08-07T10:46:05.722Z -->

The **AccessibilityExtensionContext** module, inherited from **ExtensionContext**, provides context for **AccessibilityExtensionAbility**.

The Accessibility Extension Context module provides capabilities related to the accessibility extension, including configuring concerned information types, querying node information, and gesture injection.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

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

## ElementAttributeValues

Provides attribute names and value types of a node element.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Attributes

| Name                  | Type                                                             | Read-Only| Optional| Description             |
|----------------------|--------------------------------------------------------------------|------|------|-------------------|
| accessibilityFocused | boolean | No | No | Whether the element is in the accessibility focus state. The value **true** indicates that the element is in the accessibility focus state, and **false** indicates the opposite. The default value is **false**. |
| accessibilityText<sup>12+</sup> | string                                                  | No  | No  | Accessibility text information of an element.|
| bundleName           | string                                                             | No  | No  | Bundle name.|
| checkable | boolean | No | No | Whether the element is checkable. The value **true** indicates that the element is checkable, and **false** indicates the opposite. The default value is **false**. |
| checked | boolean | No | No | Whether the element is checked. The value **true** indicates that the element is checked, and **false** indicates the opposite. The default value is **false**. |
| children             | Array&lt;[AccessibilityElement](#accessibilityelement)&gt;        | No  | No  | All child elements.|
| clickable            | boolean                                                            | No  | No  | Whether the element is clickable. The value **true** indicates that the element is clickable, and **false** indicates the opposite.<br>Default value: **false**.|
| componentId          | number                                                             | No  | No  | ID of the component to which the element belongs. <br>Default value: **-1**.|
| componentType | string | No | No | Component type of the element, for example, 'Button' for the Button component and 'Image' for the Image component. |
| contents             | Array&lt;string&gt;                                                | No  | No  | List of contents. Set this parameter based on site requirements. No special restrictions.|
| currentIndex | number | No | No | Index of the current item. The value range is greater than or equal to 0. The default value is **0**. |
| description          | string                                                             | No  | No  | Description of the element. Set this parameter based on site requirements. No special restrictions.|
| editable             | boolean                                                            | No  | No  | Whether the element is editable. The value **true** indicates that the element is editable, and **false** indicates the opposite.<br>Default value: **false**.|
| endIndex | number | No | No | List index of the last displayed item on the screen. The value range is greater than or equal to 0. The default value is **0**. |
| error                | string                                                             | No  | No  | Error status.|
| focusable            | boolean                                                            | No  | No  | Whether the element is focusable. The value **true** indicates that the element is focusable, and **false** indicates the opposite.<br>Default value: **false**.|
| hintText             | string                                                             | No  | No  | Hint text.|
| inputType | number | No | No | Type of the input text. Different values correspond to different input modes: **0** indicates no specific type; **1** indicates text; **2** indicates email; **3** indicates date; **4** indicates time; **5** indicates number; **6** indicates password; **7** indicates phone number; **8** indicates username; **9** indicates new password. The default value is **0**. |
| inspectorKey         | string                                                             | No  | No  | Alias of the element.|
| isActive             | boolean                                                            | No  | No  | Whether the element is active. The value **true** indicates that the element is active and **false** indicates the opposite.<br>Default value: **true**.|
| isEnable             | boolean                                                            | No  | No  | Whether the element is enabled. The value **true** indicates that the element is enabled, and **false** indicates the opposite.<br>Default value: **false**.|
| isHint               | boolean                                                            | No  | No  | Whether the element is a hint. The value **true** indicates that the element is a hint, and **false** indicates the opposite.<br>Default value: **false**.|
| isFocused            | boolean                                                            | No  | No  | Whether the element is focused. The value **true** indicates that the element is focused, and **false** indicates the opposite.<br>Default value: **false**.|
| isPassword           | boolean                                                            | No  | No  | Whether the element is a password. The value **true** indicates that the element is a password, and **false** indicates the opposite.<br>Default value: **false**.|
| isVisible            | boolean                                                            | No  | No  | Whether the element is visible. The value **true** indicates that the element is visible, and **false** indicates the opposite.<br>Default value: **false**.|
| itemCount | number | No | No | Total number of items. The value range is greater than or equal to 0. The default value is **0**. |
| lastContent | string | No | No | Content of the last item in a list or scrollable control. |
| layer | number | No | No | Display layer of the element. The value range is greater than or equal to 0. The default value is **0**. |
| longClickable | boolean | No | No | Whether the element is long-clickable. The value **true** indicates that the element is long-clickable, and **false** indicates the opposite. The default value is **false**. |
| pageId | number | No | No | Page ID. The default value is **-1**. |
| parent               | [AccessibilityElement](#accessibilityelement)                     | No  | No  | Parent element of the element.|
| pluralLineSupported  | boolean                                                            | No  | No  | Whether the element supports multiple lines of text. The value **true** indicates that the element supports multiple lines of text, and **false** indicates the opposite.<br>Default value: **false**.|
| rect | [Rect](#rect) | No | No | Rectangular area of the element, including position and size information. |
| resourceName         | string                                                             | No  | No  | Resource name of the element.|
| rootElement | [AccessibilityElement](#accessibilityelement) | No | No | Root node element of the window element. |
| screenRect           | [Rect](#rect)                                                      | No  | No  | Display area of the element.|
| scrollable | boolean | No | No | Whether the element is scrollable. The value **true** indicates that the element is scrollable, and **false** indicates the opposite. The default value is **false**. In accessibility mode, when the values of accessibilityScrollable and scrollable conflict, the accessibilityScrollable attribute takes precedence. |
| selected             | boolean                                                            | No  | No  | Whether the element is selected. The value **true** indicates that the element is selected, and **false** indicates the opposite.<br>Default value: **false**.|
| startIndex | number | No | No | List index of the first item on the screen. The value range is greater than or equal to 0. The default value is **0**. |
| text                 | string                                                             | No  | No  | Text of the element.|
| textLengthLimit | number | No | No | Maximum length limit of the element text. The value range is greater than or equal to 0. The default value is **0**. |
| textMoveUnit         | [accessibility.TextMoveUnit](js-apis-accessibility.md#textmoveunit)| No  | No  | Granularity of movement when the text is read.|
| triggerAction        | [accessibility.Action](js-apis-accessibility.md#action)            | No  | No  | Action that triggers the element event.|
| type                 | [WindowType](#windowtype)                                          | No  | No  | Window type of the element.|
| valueMax             | number                                                             | No  | No  | Maximum value. <br>Default value: **0**.|
| valueMin             | number                                                             | No  | No  | Minimum value. <br>Default value: **0**.|
| valueNow             | number                                                             | No  | No  | Current value. <br>Default value: **0**.|
| windowId             | number                                                             | No  | No  | Window ID. <br>Default value: **-1**.|
| textType<sup>12+</sup>             | string                                                             | No  | No  | Accessibility text type of an element, which is configured by the **accessibilityTextHint** attribute of the component.|
| offset<sup>12+</sup>             | number              | No  | No  | For scrollable components such as **List** and **Grid**, this attribute indicates the pixel offset of the content area relative to the top coordinate of the component. The unit is pixel (px). <br>Default value: **0**.|
| hotArea<sup>12+</sup>             | [Rect](#rect)                                                              | No  | No  | Touchable area of an element.|
| customComponentType<sup>18+</sup> | string | No | Yes | Custom component type. Corresponds to the [AccessibilityRoleType](../apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityroletype18) of the element. The default value is an empty string. |
| accessibilityNextFocusId<sup>18+</sup> | number | No | Yes | ID of the next component to be focused. This attribute value set by the user on the control can be obtained from the AccessibilityElement object queried through findElement('elementId'). The default value is **-1**. |
| accessibilityPreviousFocusId<sup>18+</sup> | number | No | Yes | ID of the previously focused component. This attribute value set by the user on the control can be obtained from the AccessibilityElement object queried through findElement('elementId'). The default value is **-1**. |
| extraInfo<sup>18+</sup> | string | No | Yes | Extended attribute used to define properties of specific components. The default value is an empty string. It includes:<br>- CheckboxGroupSelectedStatus: indicates the selection state of the CheckboxGroup component, where **0** indicates selected, **1** indicates partially selected, and **2** indicates unselected.<br>- Row: row information of the focused item in the Grid component, indicating the row number of the item.<br>- Column: column information of the focused item in the Grid component, indicating the column number of the item.<br>- ListItemIndex: row information of the focused item in the List component, indicating the row number of the current item.<br>- SideBarContainerStates: indicates the expanded state of expandable components (SideBarContainer, Select), where **0** indicates collapsed and **1** indicates expanded.<br>- ToggleType: indicates the specific type of the Toggle component, where **0** indicates Checkbox, **1** indicates Switch, and **2** indicates Button.<br>- BindSheet: indicates the display height state of the BindSheet half-modal dialog box component, where **0** indicates large height display state, **1** indicates medium height display state, and **2** indicates small height display state.<br>- hasRegisteredHover: indicates whether the component has registered the onAccessibilityHover event callback. The value **1** indicates that the component has registered the event callback. This field is not used if the callback is not registered.<br>- direction: indicates the layout direction of the List component, where "vertical" indicates vertical and "horizontal" indicates horizontal.<br>- expandedState: indicates the expanded state of a ListItem in the List component, where "expanded" indicates expanded and "collapsed" indicates collapsed.<br>- componentTypeDescription: detailed information about the component type, serving as a supplementary description for componentType. |
| accessibilityScrollable<sup>18+</sup> | boolean | No | Yes | Whether the element is scrollable in accessibility mode. This attribute takes precedence over scrollable, meaning the accessibilityScrollable attribute value prevails. The value **true** indicates scrollable, and **false** indicates not scrollable. The default value is **true**. |

## FocusDirection

type FocusDirection = 'up' | 'down' | 'left' | 'right' | 'forward' | 'backward'

Enumerates the focus directions.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

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

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type           | Description         |
| ------------- | ----------- |
| 'accessibility' | Accessibility focus.|
| 'normal'        | Normal focus. |

## Rect

Defines a rectangle.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name    | Type    | Read-Only  | Optional  | Description       |
| ------ | ------ | ---- | ---- | --------- |
| left   | number | No   | No   | Left boundary of the rectangle, in pixels.|
| top    | number | No   | No   | Top boundary of the rectangle, in pixels.|
| width  | number | No   | No   | Width of the rectangle, in pixels. |
| height | number | No   | No   | Height of the rectangle, in pixels. |

## WindowType

type WindowType = 'application' | 'system'

Enumerates the window types.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type         | Description       |
| ----------- | --------- |
| 'application' | Application window.|
| 'system'      | System window.|

## AccessibilityExtensionContext

Context for the accessibility extension. Obtain an AccessibilityExtensionContext instance through an AccessibilityExtensionAbility subclass instance.

### setTargetBundleName<sup>(deprecated)</sup>

setTargetBundleName(targetNames: Array\<string>): Promise\<void>

Sets the bundle name of the concerned app. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                 | Mandatory  | Description      |
| ----------- | ------------------- | ---- | -------- |
| targetNames | Array&lt;string&gt; | Yes | Sets the package names of the apps of interest. After setting, the service receives only accessibility events of the apps of interest. If not set, the service receives accessibility events of all apps by default. To cancel the focus on apps, pass an empty array. |

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
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.setTargetBundleName(targetNames).then(() => {
  console.info(`succeeded in setting target bundle names, targetNames is ${targetNames}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set target bundle names. Code: ${err.code}, message: ${err.message}`);
});
```

### setTargetBundleName<sup>(deprecated)</sup>

setTargetBundleName(targetNames: Array\<string>, callback: AsyncCallback\<void>): void

Sets the bundle name of the concerned app. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                       | Mandatory  | Description                                      |
| ----------- | ------------------------- | ---- | ---------------------------------------- |
| targetNames | Array&lt;string&gt; | Yes | Package name of the app to focus on. After setting, the service receives accessibility events only from the focused app. If not set, accessibility events from all apps are received by default. To cancel the focus on an app, pass an empty array. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the target package name is set successfully, **err** is **undefined**; otherwise, it is an error object. |

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

### getFocusElement<sup>(deprecated)</sup>

getFocusElement(isAccessibilityFocus?: boolean): Promise\<AccessibilityElement>

Obtains the focus element. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name                 | Type     | Mandatory  | Description                 |
| -------------------- | ------- | ---- | ------------------- |
| isAccessibilityFocus | boolean | No | Whether to obtain the accessibility focus element. The value **true** indicates that it is an accessibility focus element, and **false** indicates that it is not an accessibility focus element. Default value: **false**. |

**Return value**

| Type                                 | Description                    |
| ----------------------------------- | ---------------------- |
| Promise&lt;[AccessibilityElement](#accessibilityelement)&gt; | Promise used to return the current focus element.|

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

// axContext is an instance of AccessibilityExtensionContext, obtained through this.context of an AccessibilityExtensionAbility subclass. See the usage instructions for details.
axContext.getFocusElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.info(`succeeded in getting focus element,${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get focus element. Code: ${err.code}, message: ${err.message}`);
});
```

### getFocusElement<sup>(deprecated)</sup>

getFocusElement(callback: AsyncCallback\<AccessibilityElement>): void

Obtains the focus element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description               |
| -------- | ---------------------------------------- | ---- | ----------------- |
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement)&gt; | Yes | Callback used to return the focus element. If the operation is successful, **err** is **undefined** and **data** is the current focus element; otherwise, **err** is an error object. |

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

### getFocusElement<sup>(deprecated)</sup>

getFocusElement(isAccessibilityFocus: boolean, callback: AsyncCallback\<AccessibilityElement>): void

Obtains the focus element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name                 | Type                                      | Mandatory  | Description               |
| -------------------- | ---------------------------------------- | ---- | ----------------- |
| isAccessibilityFocus | boolean | Yes | Whether the element obtained is an accessibility focus element. The value **true** indicates that it is an accessibility focus element, and **false** indicates the opposite. |
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement)&gt; | Yes | Callback invoked to return the result. If the focus element is obtained successfully, **err** is **undefined** and **data** is the corresponding focus element; otherwise, **err** is an error object. |

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

### getWindowRootElement<sup>(deprecated)</sup>

getWindowRootElement(windowId?: number): Promise\<AccessibilityElement>

Obtains the root element of the specified window. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                    |
| -------- | ------ | ---- | ---------------------- |
| windowId | number | No   | ID of the window whose root element is to be obtained. If this parameter is not specified, it indicates the current active window.|

**Return value**

| Type                                 | Description                    |
| ----------------------------------- | ---------------------- |
| Promise&lt;[AccessibilityElement](#accessibilityelement)&gt; | Promise used to return the root element of the specified window.|

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

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. See the usage instructions for details.
axContext.getWindowRootElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.info(`succeeded in getting root element of the window, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get root element of the window. Code: ${err.code}, message: ${err.message}`);
});
```

### getWindowRootElement<sup>(deprecated)</sup>

getWindowRootElement(callback: AsyncCallback\<AccessibilityElement>): void

Obtains the root element of the currently active window. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                |
| -------- | ---------------------------------------- | ---- | ------------------ |
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement)&gt; | Yes | Callback invoked to return the result. If the root node element is obtained successfully, err is undefined and data is the root node element of the currently active window; otherwise, err is an error object. |

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

### getWindowRootElement<sup>(deprecated)</sup>

getWindowRootElement(windowId: number, callback: AsyncCallback\<AccessibilityElement>): void

Obtains the root element of the specified window. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                    |
| -------- | ---------------------------------------- | ---- | ---------------------- |
| windowId | number                                   | Yes    | Number of the specified window. |
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement)&gt; | Yes    | Callback used to return the result. If the root node element is obtained successfully, **err** is **undefined** and **data** is the root node element of the specified window; otherwise, **err** is an error object.     |

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

### getWindows<sup>(deprecated)</sup>

getWindows(displayId?: number): Promise\<Array\<AccessibilityElement>>

Obtains all windows on the specified display. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type    | Mandatory  | Description                   |
| --------- | ------ | ---- | --------------------- |
| displayId | number | No   | ID of the display from which the window information is obtained. If this parameter is not specified, it indicates the default main display.|

**Return value**

| Type                                      | Description                    |
| ---------------------------------------- | ---------------------- |
| Promise&lt;Array&lt;[AccessibilityElement](#accessibilityelement)&gt;&gt; | Promise used to return the window list.|

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

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.getWindows().then((data: AccessibilityElement[]) => {
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
});
```

### getWindows<sup>(deprecated)</sup>

getWindows(callback: AsyncCallback\<Array\<AccessibilityElement>>): void

Obtains all windows on the default main display. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description               |
| -------- | ---------------------------------------- | ---- | ----------------- |
| callback | AsyncCallback&lt;Array&lt;[AccessibilityElement](#accessibilityelement)&gt;&gt; | Yes | Callback invoked to return the result. If the window is obtained successfully, **err** is **undefined** and **data** is all windows of the default home screen; otherwise, it is an error object. |

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

// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. See usage instructions for details.
axContext.getWindows((err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
});
```

### getWindows<sup>(deprecated)</sup>

getWindows(displayId: number, callback: AsyncCallback\<Array\<AccessibilityElement>>): void

Obtains all windows on the specified display. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                   |
| --------- | ---------------------------------------- | ---- | --------------------- |
| displayId | number | Yes | ID of the specified screen, used to identify the screen for which to obtain windows. |
| callback | AsyncCallback&lt;Array&lt;[AccessibilityElement](#accessibilityelement)&gt;&gt; | Yes | Callback used to return the result. If the windows are obtained successfully, **err** is **undefined** and **data** is all windows on the specified screen; otherwise, **err** is an error object. |

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
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.getWindows(displayId, (err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
});
```

### injectGesture<sup>(deprecated)</sup>

injectGesture(gesturePath: GesturePath): Promise\<void>

Injects a gesture, applicable to scenarios where an accessibility app performs touch interactions on behalf of the user, such as tap and swipe operations. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [injectGestureSync](#injectgesturesyncdeprecated) instead, but this alternative API has also been deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

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
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.injectGesture(gesturePath).then(() => {
  console.info(`Succeeded in injecting gesture,gesturePath is ${gesturePath}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to inject gesture. Code: ${err.code}, message: ${err.message}`);
});
```

### injectGesture<sup>(deprecated)</sup>

injectGesture(gesturePath: GesturePath, callback: AsyncCallback\<void>): void

Injects a gesture, applicable to scenarios where an accessibility app performs touch interactions on behalf of the user, such as tap and swipe operations. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [injectGestureSync](#injectgesturesyncdeprecated) instead, but this alternative API has also been deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                                                | Mandatory  | Description                 |
| ----------- |--------------------------------------------------------------------| ---- | ------------------- |
| gesturePath | [GesturePath](js-apis-accessibility-GesturePath.md#gesturepath) | Yes   | Path of the gesture to inject.         |
| callback    | AsyncCallback&lt;void&gt;                                          | Yes    | Callback used to return the result. If the gesture injection is successful, **err** is **undefined**; otherwise, it is an error object. |

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
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage guide.
axContext.injectGesture(gesturePath, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to inject gesture. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in injecting gesture,gesturePath is ${gesturePath}`);
});
```

### injectGestureSync<sup>(deprecated)</sup>

injectGestureSync(gesturePath: GesturePath): void

Injects a gesture, applicable to scenarios where an accessibility app performs touch interactions on behalf of the user, such as tap and swipe operations.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

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
// axContext is an AccessibilityExtensionContext instance, obtained through this.context of an AccessibilityExtensionAbility subclass. For details, see the usage instructions.
axContext.injectGestureSync(gesturePath);
```

## AccessibilityElement

An accessibility node element that provides capabilities such as querying parent/child elements, finding elements by content or focus direction, and performing accessibility actions. It is applicable to scenarios where an accessibility app needs to interact with and operate on UI nodes.

Before calling methods of AccessibilityElement, obtain an AccessibilityElement instance through [AccessibilityExtensionContext.getFocusElement()](#getfocuselementdeprecated) or [AccessibilityExtensionContext.getWindowRootElement()](#getwindowrootelementdeprecated).

### attributeNames<sup>(deprecated)</sup>

attributeNames\<T extends keyof ElementAttributeValues>() : Promise\<Array\<T>>

Obtains all attribute names of the node element. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                           | Description                      |
| ----------------------------- | ------------------------ |
| Promise&lt;Array&lt;T&gt;&gt; | Promise used to return all attribute names of the element.|

**Example**

```ts
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.attributeNames().then((data: ElementAttributeKeys[]) => {
  console.info(`succeeded in getting attribute names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get attribute names. Code: ${err.code}, message: ${err.message}`);
});
```

### attributeNames<sup>(deprecated)</sup>

attributeNames\<T extends keyof ElementAttributeValues>(callback: AsyncCallback\<Array\<T>>): void

Obtains all attribute names of the node element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                 | Mandatory  | Description                 |
| -------- | ----------------------------------- | ---- | ------------------- |
| callback | AsyncCallback&lt;Array&lt;T&gt;&gt; | Yes | Callback invoked to return the result. If the attribute names are obtained successfully, **err** is undefined and **data** contains all attribute names of the node element; otherwise, **err** is an error object. |

**Example**

```ts
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

### attributeValue<sup>(deprecated)</sup>

attributeValue\<T extends keyof ElementAttributeValues>(attributeName: T): Promise\<ElementAttributeValues[T]>

Obtains the attribute value based on the attribute name. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

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

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.attributeValue(attributeName).then((data: string) => {
  console.info(`succeeded in getting attribute value by name, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get attribute value. Code: ${err.code}, message: ${err.message}`);
});
```

### attributeValue<sup>(deprecated)</sup>

attributeValue\<T extends keyof ElementAttributeValues>(attributeName: T, callback: AsyncCallback\<ElementAttributeValues[T]>): void

Obtains the attribute value based on an attribute name. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name          | Type                                      | Mandatory  | Description                    |
| ------------- | ---------------------------------------- | ---- | ---------------------- |
| attributeName | ElementAttributeKeys                         | Yes   | Attribute name.              |
| callback      | AsyncCallback&lt;[ElementAttributeValues](#elementattributevalues)[T]&gt; | Yes    | Callback used to return the result. If the attribute value is obtained successfully, err is undefined and data is the value of the corresponding attribute; otherwise, the value is an error object. |

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

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.attributeValue(attributeName, (err: BusinessError, data: string) => {
  if (err) {
    console.error(`Failed to get attribute value. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting attribute value, ${JSON.stringify(data)}`);
});
```

### actionNames<sup>(deprecated)</sup>

actionNames(): Promise\<Array\<string>>

Obtains the names of all actions supported by the node element. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                                | Description                        |
| ---------------------------------- | -------------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the names of all actions supported by the element.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.actionNames().then((data: string[]) => {
  console.info(`succeeded in getting action names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get action names. Code: ${err.code}, message: ${err.message}`);
});
```

### actionNames<sup>(deprecated)</sup>

actionNames(callback: AsyncCallback\<Array\<string>>): void

Obtains the names of all actions supported by the node element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                   |
| -------- | ---------------------------------------- | ---- | --------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. If the action names are obtained successfully, **err** is **undefined** and **data** contains all action names supported by the node element; otherwise, **err** is an error object. |

**Example**

```ts
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

### performAction<sup>(deprecated)</sup>

performAction(actionName: string, parameters?: object): Promise\<void>

Performs the specified action on the accessibility node element. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                    | Mandatory  | Description                                                      |
| ----------- | ---------------------------------------- | ---- |----------------------------------------------------------|
| actionName | string | Yes | Name of the action. For the value range, see [Action](js-apis-accessibility.md#action). |
| parameters | object | No | Parameters required for executing the action. Different actions require different parameter key names and value types. For details about the value principles, see the definition of each Action. For example, setSelection requires the selectTextBegin, selectTextEnd, and selectTextInForWard parameters, and setCursorPosition requires the offset parameter. If not passed, this parameter is empty by default. |

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

- Action without parameters.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
  // If no specific requirement is stated in the action description, the action has no parameters.
  rootElement.performAction('click').then(() => {
    console.info(`succeeded in performing action.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
  });
  ```

- Action with parameters (setSelection).

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
  // Example code for setSelection.
  rootElement.performAction('setSelection', {
    selectTextBegin: '0', // Indicates the start position of the selection.
    selectTextEnd: '8',   // Indicates the end position of the selection.
    selectTextInForWard: true   // The value true indicates the front cursor, and false indicates the rear cursor.
  }).then(() => {
    console.info(`succeeded in performing action`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
  });
  ```

- Action with parameters (setCursorPosition).

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
  // Example code for setCursorPosition.
  rootElement.performAction('setCursorPosition', {
    offset: '1'   // Indicates the cursor position to set.
  }).then(() => {
    console.info(`succeeded in performing action`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
  });
  ```

### performAction<sup>(deprecated)</sup>

performAction(actionName: string, callback: AsyncCallback\<void>): void

Performs the specified action on the accessibility node element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                    | Mandatory  | Description            |
| ----------- | ---------------------------------------- | ---- | -------------- |
| actionName | string | Yes | Name of the action. For the value range, see [Action](js-apis-accessibility.md#action). |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked when the operation is executed. If the operation succeeds, **err** is **undefined**; otherwise, **err** is an error object. |

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

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.performAction(actionName, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in performing action, actionName is ${actionName}`);
});
```

### performAction<sup>(deprecated)</sup>

performAction(actionName: string, parameters: object, callback: AsyncCallback\<void>): void

Performs the specified action on the accessibility node element. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name       | Type                       | Mandatory  | Description                                                         |
| ---------- | ------------------------- | ---- |-------------------------------------------------------------|
| actionName | string | Yes | Name of the action. For the value range, see [Action](js-apis-accessibility.md#action). |
| parameters | object | Yes | Parameters required for executing the action. Different action types require different parameter structures. For details about the parameter format, see the description of each Action. For example, setSelection requires the selectTextBegin, selectTextEnd, and selectTextInForWard parameters, and setCursorPosition requires the offset parameter. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the action is executed successfully, err is undefined; otherwise, err is an error object. |

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

### findElement('content')<sup>(deprecated)</sup>

findElement(type: 'content', condition: string): Promise\<Array\<AccessibilityElement>>

Finds all node elements based on the node content. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type    | Mandatory  | Description                           |
| --------- | ------ | ---- | ----------------------------- |
| type | string | Yes | The value is fixed at 'content', indicating that the search type is node element content. |
| condition | string | Yes | Keyword condition for the search, used to match the text content of the node element. |

**Return value**

| Type                                      | Description                           |
| ---------------------------------------- | ----------------------------- |
| Promise&lt;Array&lt;[AccessibilityElement](#accessibilityelement)&gt;&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition = 'keyword';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.findElement('content', condition).then((data: AccessibilityElement[]) => {
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

### findElement('content')<sup>(deprecated)</sup>

findElement(type: 'content', condition: string, callback: AsyncCallback\<Array\<AccessibilityElement>>): void

Finds an element based on the content type. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                          |
| --------- | ---------------------------------------- | ---- | ---------------------------- |
| type      | string                                   | Yes    | Fixed to 'content', which means the search type is node element content. |
| condition | string                                   | Yes    | Keyword condition for searching, used to match the text content of node elements. |
| callback  | AsyncCallback&lt;Array&lt;[AccessibilityElement](#accessibilityelement)&gt;&gt; | Yes    | Callback used to return the result. If the node elements are found successfully, **err** is **undefined** and **data** is all node elements that meet the specified search keyword; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition = 'keyword';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.findElement('content', condition, (err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
});
```

### findElement('focusType')<sup>(deprecated)</sup>

findElement(type: 'focusType', condition: FocusType): Promise\<AccessibilityElement>

Finds a node element based on the focus element type. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                     | Mandatory  | Description                                |
| --------- | ----------------------- | ---- | ---------------------------------- |
| type      | string                  | Yes   | Type of element finding. The value is fixed at **'focusType'**.|
| condition | [FocusType](#focustype) | Yes   | Focus type.                      |

**Return value**

| Type                                 | Description                            |
| ----------------------------------- | ------------------------------ |
| Promise&lt;[AccessibilityElement](#accessibilityelement)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusType, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusType = 'normal';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.findElement('focusType', condition).then((data: AccessibilityElement) => {
  console.info(`succeeded in finding element,${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

### findElement('focusType')<sup>(deprecated)</sup>

findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback\<AccessibilityElement>): void

Finds a node element based on the focus element type. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                                |
| --------- | ---------------------------------------- | ---- | ---------------------------------- |
| type      | string                                   | Yes   | Type of element finding. The value is fixed at **'focusType'**.|
| condition | [FocusType](#focustype)                  | Yes   | Focus type.                      |
| callback | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement)&gt; | Yes | Callback invoked to return the result. If the node element is found, **err** is **undefined** and **data** is the node element that matches the specified query focus element type; otherwise, an error object is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusType, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusType = 'normal';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.findElement('focusType', condition, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
});
```

### findElement('focusDirection')<sup>(deprecated)</sup>

findElement(type: 'focusDirection', condition: FocusDirection): Promise\<AccessibilityElement>

Finds a node element based on the next focus element direction. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                               | Mandatory  | Description                                      |
| --------- | --------------------------------- | ---- | ---------------------------------------- |
| type      | string                            | Yes   | Type of element finding. The value is fixed at **'focusDirection'**.|
| condition | [FocusDirection](#focusdirection) | Yes   | Focus direction.                          |

**Return value**

| Type                                 | Description                              |
| ----------------------------------- | -------------------------------- |
| Promise&lt;[AccessibilityElement](#accessibilityelement)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusDirection, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusDirection = 'up';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.findElement('focusDirection', condition).then((data: AccessibilityElement) => {
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

### findElement('focusDirection')<sup>(deprecated)</sup>

findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback\<AccessibilityElement>): void

Finds a node element based on the next focus element direction. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                                      |
| --------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type      | string                                   | Yes    | Fixed value **'focusDirection'**, representing the query type as the direction of the next focus element of the node. |
| condition | [FocusDirection](#focusdirection)        | Yes    | Direction for querying the next focus element. |
| callback  | AsyncCallback&lt;[AccessibilityElement](#accessibilityelement)&gt; | Yes    | Callback invoked to return the result. If the node element is found successfully, **err** is **undefined** and **data** is the node element that meets the specified direction for querying the next focus element; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                         |
| ------- | ----------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { FocusDirection, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusDirection = 'up';

// rootElement is an instance of AccessibilityElement, obtained through getFocusElement() or getWindowRootElement().
rootElement.findElement('focusDirection', condition, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
});
```