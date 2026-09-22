# AccessibilityElement

```TypeScript
export declare interface AccessibilityElement
```

An accessibility node element that provides capabilities such as querying parent/child elements, finding elements by content or focus direction, and performing accessibility actions. It is applicable to scenarios where an accessibility app needs to interact with and operate on UI nodes.

Before calling methods of AccessibilityElement, obtain an AccessibilityElement instance through [AccessibilityExtensionContext.getAccessibilityFocusedElement()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getaccessibilityfocusedelement) or [AccessibilityExtensionContext.getRootInActiveWindow()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getrootinactivewindow).

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## enableScreenCurtain

```TypeScript
enableScreenCurtain(isEnable: boolean): void
```

Enables or disables the screen curtain. When the screen curtain is enabled, the screen content is hidden (the screen dims), but the device still responds to operations normally.

**Since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnable | boolean | Yes | Whether to enable the screen curtain. The value `true` means to enable the screen curtain, and `false` means to disable it. |

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

## executeAction

```TypeScript
executeAction(action: AccessibilityAction, parameters?: Parameter): Promise<void>
```

Performs an action on an accessibility node element based on the action type and parameters specified. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md) | Yes | Action that can be performed on the accessibility node. |
| parameters | [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md) | No | Parameter value set when performing the action. This parameter is passed when performing actions that require additional parameter configuration (such as SET_SELECTION, SET_CURSOR_POSITION, etc.); it is not required when performing parameterless actions (such as CLICK, etc.). Defaults to empty if not passed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300005](../errorcode-accessibility.md#9300005-operation-not-supported) | This action is not supported. |

**Examples**

Action without parameters.

```TypeScript
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

Action with parameters (setSelection).

```TypeScript
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

Action with parameters (setCursorPosition).

```TypeScript
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

## findElement('textType')

```TypeScript
findElement(type: 'textType', condition: string): Promise<Array<AccessibilityElement>>
```

Searches for all node elements based on the accessibility text type configured in the component's accessibilityTextHint attribute. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'textType' | Yes | Fixed to 'textType', indicating that elements are searched by text type. |
| condition | string | Yes | Accessibility text type condition for the search. All node elements whose accessibilityTextHint attribute matches this text type will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise used to return all node elements that match the specified accessibility text type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
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

## findElement('elementId')

```TypeScript
findElement(type: 'elementId', condition: number): Promise<AccessibilityElement>
```

Queries the node element in the current active window based on the element ID. This API uses a promise to return the result.

This method and [findElementById](#findelementbyid) both find a node element by element ID. They are functionally equivalent. It is recommended to use findElementById.

**Since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'elementId' | Yes | Fixed value **'elementId'**, indicating that the node element in the current active window is queried by element ID. |
| condition | number | Yes | Element ID of the node element to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the result, which is the node element that meets the specified query condition. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
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

## findElementByContent

```TypeScript
findElementByContent(condition: string): Promise<Array<AccessibilityElement>>
```

Searches for node elements by their content text, and returns all node elements that contain the specified text. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | string | Yes | Content text of the element to find. After this parameter is set, all node elements that contain this text content are returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise used to return the result. The value is a list of elements that contain the specified content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-failed-to-connect-the-target-app-and-accessibility-service) | The target application failed to connect to accessibility service. |

**Examples**

```TypeScript
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

## findElementByFocusDirection

```TypeScript
findElementByFocusDirection(condition: FocusDirection): Promise<AccessibilityElement>
```

Searches for an element based on the focus direction. This API uses a promise to return the result.

Compared with [findElementsByCondition](#findelementsbycondition), this method is mainly used to search for web components, while findElementsByCondition is mainly used to search for UI components.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | Yes | Focus direction, which specifies the search direction for finding elements. For example, 'forward' indicates forward search and 'backward' indicates backward search. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the result. The element in the specified focus direction. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-failed-to-connect-the-target-app-and-accessibility-service) | The target application failed to connect to accessibility service. |

**Examples**

```TypeScript
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

<a id="findelementbyfocusdirection-1"></a>

## findElementByFocusDirection

```TypeScript
findElementByFocusDirection(condition: FocusDirection, type: FocusRuleType): Promise<AccessibilityElement>
```

Searches for an element based on the focus direction and focus rule type. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | Yes | Focus direction. |
| type | [FocusRuleType](arkts-accessibility-accessibility-focusruletype-e-sys.md) | Yes | Focus rule type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the element that matches the focus rule type in the specified focus direction. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-failed-to-connect-the-target-app-and-accessibility-service) | The target application failed to connect to accessibility service. |

**Examples**

```TypeScript
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

## findElementById

```TypeScript
findElementById(condition: number): Promise<AccessibilityElement>
```

Searches for a node element in the active window by element ID. This API uses a promise to return the result.

This method is functionally equivalent to [findElement('elementId')](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md#findelementcontent) and is recommended for priority use.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | number | Yes | ID of the node element to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the element with the specified ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-failed-to-connect-the-target-app-and-accessibility-service) | The target application failed to connect to accessibility service. |

**Examples**

```TypeScript
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

## findElementsByAccessibilityHintText

```TypeScript
findElementsByAccessibilityHintText(condition: string): Promise<Array<AccessibilityElement>>
```

Searches for elements by hint text, and returns all node elements whose accessibilityTextHint attribute matches the text. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | string | Yes | Hint text of the element to find. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise used to return the list of elements with the specified hint text. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-failed-to-connect-the-target-app-and-accessibility-service) | The target application failed to connect to accessibility service. |

**Examples**

```TypeScript
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

## findElementsByCondition

```TypeScript
findElementsByCondition(rule: FocusRule, condition: FocusCondition): Promise<FocusMoveResult>
```

Queries focusable nodes that meet the conditions. This API uses a promise to return the result.

Compared with [findElementByFocusDirection](#findelementbyfocusdirection), this method is mainly used to find UI components, while findElementByFocusDirection is mainly used to find Web components.

**Since:** 23

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | [FocusRule](arkts-accessibility-focusrule-t-sys.md) | Yes | Rule for checking the current node and its child nodes. |
| condition | [FocusCondition](arkts-accessibility-focuscondition-t-sys.md) | Yes | Mode for querying focusable nodes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FocusMoveResult](arkts-accessibility-accessibilityextensioncontext-focusmoveresult-i-sys.md)&gt; | Promise used to return the result. The FocusMoveResult object contains the queried accessibility node list and the query result status code. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
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

<a id="findelementsbycondition-1"></a>

## findElementsByCondition

```TypeScript
findElementsByCondition(rule: FocusRule, condition: FocusCondition, type: FocusRuleType): Promise<FocusMoveResult>
```

Searches for focusable nodes of the target type based on the rule and query condition. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | [FocusRule](arkts-accessibility-focusrule-t-sys.md) | Yes | Rule for checking the current node and its child nodes. |
| condition | [FocusCondition](arkts-accessibility-focuscondition-t-sys.md) | Yes | Method for querying focusable nodes. |
| type | [FocusRuleType](arkts-accessibility-accessibility-focusruletype-e-sys.md) | Yes | Focus type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FocusMoveResult](arkts-accessibility-accessibilityextensioncontext-focusmoveresult-i-sys.md)&gt; | Promise used to return the query result object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
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

## getChildren

```TypeScript
getChildren(): Promise<Array<AccessibilityElement>>
```

Obtains the list of child elements of this element. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise used to return the list of child elements of the current element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
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

## getCursorPosition

```TypeScript
getCursorPosition(callback: AsyncCallback<number>): void
```

Obtains the cursor position in a text component. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the cursor position is obtained successfully, **err** is undefined and **data** is the position index of the cursor in the text; otherwise, **err** is an error object. |

**Examples**

```TypeScript
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

<a id="getcursorposition-1"></a>

## getCursorPosition

```TypeScript
getCursorPosition(): Promise<number>
```

Obtains the cursor position in a text component. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the current cursor position. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement is an instance of AccessibilityElement. Obtain it through AccessibilityExtensionContext.getAccessibilityFocusedElement() or getRootInActiveWindow().
rootElement.getCursorPosition().then((data: number) => {
  console.info(`succeeded in getting cursor position, ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get cursor position. Code: ${err.code}, message: ${err.message}`);
});
```

## getParent

```TypeScript
getParent(): Promise<AccessibilityElement>
```

Obtains the parent element of an accessibility node. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the parent element of the current element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
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

## getRoot

```TypeScript
getRoot(): Promise<AccessibilityElement>
```

Obtains the root element of the active window. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise used to return the root element of the active window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
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

## accessibilityFocused

```TypeScript
accessibilityFocused?: boolean
```

Whether the element gains focus for accessibility purposes. The value **true** indicates that the element has gained focus, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityGroup

```TypeScript
accessibilityGroup?: boolean
```

Whether the element is an accessibility group. The value **true** indicates that the element is an accessibility group, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the component.

**'auto'**: The accessibility grouping service and ArkUI jointly determine whether the component can be recognized by accessibility.

**'yes'**: The component can be recognized by accessibility.

**'no'**: The component cannot be recognized by accessibility.

**'no-hide-descendants'**: The component and all its child components cannot be recognized by accessibility. Default value: **'auto'**.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId?: number
```

ID of the next component to gain focus.

Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityPreviousFocusId

```TypeScript
accessibilityPreviousFocusId?: number
```

ID of the previous component to gain focus.

Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityScrollable

```TypeScript
accessibilityScrollable?: boolean
```

Whether the element is scrollable for accessibility purposes. This attribute has a higher priority than scrollable. That is, when the value of accessibilityScrollable conflicts with that of scrollable, the value of accessibilityScrollable prevails.

The value **true** indicates that the element is scrollable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityStateDescription

```TypeScript
accessibilityStateDescription?: string
```

Custom accessibility state announcement text of the element.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityText

```TypeScript
accessibilityText?: string
```

Accessibility text information of the element.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityVisible

```TypeScript
accessibilityVisible?: boolean
```

Whether the component is visible for accessibility. The value **true** indicates that the component is visible, and **false** indicates the opposite. Default value: **true**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## belongTreeId

```TypeScript
belongTreeId?: number
```

ID of the component tree to which the element belongs. Default value: **-1**.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName?: string
```

Bundle name.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## checkable

```TypeScript
checkable?: boolean
```

Whether the element is checkable. The value **true** indicates that the element is checkable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## checked

```TypeScript
checked?: boolean
```

Whether the element is checked. The value **true** indicates that the element is checked, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## childrenIds

```TypeScript
childrenIds?: Array<number>
```

List of child element IDs of the component. Default value: empty array.

**Type:** Array&lt;number&gt;

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## childrenTreeId

```TypeScript
childrenTreeId?: number
```

ID of the child component tree of the element. Default value: **-1**.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## clickable

```TypeScript
clickable?: boolean
```

Whether the element is clickable. The value **true** indicates that the element is clickable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## clip

```TypeScript
clip?: boolean
```

Whether the component needs clipping. The value **true** indicates that clipping is needed, and **false** indicates the opposite. Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## componentId

```TypeScript
componentId?: number
```

ID of the component to which the element belongs.

Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## componentType

```TypeScript
componentType?: string
```

Type of the component to which the element belongs.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## contents

```TypeScript
contents?: Array<string>
```

Content displayed by the element. Default value: empty array.

**Type:** Array&lt;string&gt;

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## currentIndex

```TypeScript
currentIndex?: number
```

Index of the current item.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## currentItem

```TypeScript
currentItem?: AccessibilityGrid
```

Current item in the component grid.

**Type:** [AccessibilityGrid](arkts-accessibility-accessibilityextensioncontext-accessibilitygrid-i-sys.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## customActions

```TypeScript
customActions?: Array<string>
```

List of custom actions supported by the element.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## customComponentType

```TypeScript
customComponentType?: string
```

Custom component type. Corresponds to the [AccessibilityRoleType](../../apis-arkui/arkts-components/arkts-arkui-common-comp-accessibilityroletype-e.md) type of the element.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## description

```TypeScript
description?: string
```

Description of the element.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## editable

```TypeScript
editable?: boolean
```

Whether the element is editable. The value **true** indicates that the element is editable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## endIndex

```TypeScript
endIndex?: number
```

Index of the last list item displayed on the screen.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## error

```TypeScript
error?: string
```

Error state of the element.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## extraInfo

```TypeScript
extraInfo?: string
```

Extra information of the element. The value is a JSON string.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## focusable

```TypeScript
focusable?: boolean
```

Whether the element can gain focus (here it refers to accessibility focus, which is different from input focus). The value **true** indicates that the element can gain focus, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## hintText

```TypeScript
hintText?: string
```

Hint text.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## hotArea

```TypeScript
hotArea?: Rect
```

Touchable area of the element.

**Type:** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## inputType

```TypeScript
inputType?: number
```

Type of the input text. Different values correspond to different input modes: **0** indicates no specific type; **1** indicates text; **2** indicates email; **3** indicates date; **4** indicates time; **5** indicates number; **6** indicates password; **7** indicates phone number; **8** indicates username; **9** indicates new password.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## inspectorKey

```TypeScript
inspectorKey?: string
```

Inspector key.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## isActive

```TypeScript
isActive?: boolean
```

Whether the element is active. The value **true** indicates that the element is active, and **false** indicates the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## isEnable

```TypeScript
isEnable?: boolean
```

Whether the element is enabled. The value **true** indicates that the element is enabled, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## isEssential

```TypeScript
isEssential?: boolean
```

Whether the element is essential to the user. The value **true** indicates that the element is essential, and **false** indicates the opposite. Default value: **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## isFocused

```TypeScript
isFocused?: boolean
```

Whether the element has gained focus (here it refers to accessibility focus, which is different from input focus). The value **true** indicates that the element has gained focus, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## isHint

```TypeScript
isHint?: boolean
```

Whether the element is a hint. The value **true** indicates that the element is a hint, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## isPassword

```TypeScript
isPassword?: boolean
```

Whether the element is a password. The value **true** indicates that the element is a password, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## isVisible

```TypeScript
isVisible?: boolean
```

Whether the element is visible. The value **true** indicates that the element is visible, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## itemCount

```TypeScript
itemCount?: number
```

Total number of items.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## lastContent

```TypeScript
lastContent?: string
```

Content of the last item.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## layer

```TypeScript
layer?: number
```

Display layer of the element.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## longClickable

```TypeScript
longClickable?: boolean
```

Whether the element is long-clickable. The value **true** indicates that the element is long-clickable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## mainWindowId

```TypeScript
mainWindowId?: number
```

Main window ID of the component. Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## navDestinationId

```TypeScript
navDestinationId?: number
```

Navigation destination ID of the component. Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## offset

```TypeScript
offset?: number
```

Pixel offset of the content area relative to the top coordinate of the scrollable component (such as List and Grid), in pixels (px).

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## pageId

```TypeScript
pageId?: number
```

Page ID.

Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## parentId

```TypeScript
parentId?: number
```

Parent element ID of the component. Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## pluralLineSupported

```TypeScript
pluralLineSupported?: boolean
```

Whether the element supports multi-line text. The value **true** indicates that the element supports multi-line text, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## rect

```TypeScript
rect?: Rect
```

Area of the element.

**Type:** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## resourceName

```TypeScript
resourceName?: string
```

Resource name of the element.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## screenRect

```TypeScript
screenRect?: Rect
```

Display area of the element.

**Type:** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## scrollable

```TypeScript
scrollable?: boolean
```

Whether the element is scrollable. The value **true** indicates that the element is scrollable, and **false** indicates the opposite. When the value conflicts with that of accessibilityScrollable, the value of accessibilityScrollable prevails.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## selected

```TypeScript
selected?: boolean
```

Whether the element is selected. The value **true** indicates that the element is selected, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## sourceType

```TypeScript
sourceType?: AccessibilitySourceType
```

Source type of the component, used to distinguish default components from newly added or modified virtual components.

**Type:** [AccessibilitySourceType](arkts-accessibility-accessibility-accessibilitysourcetype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## spans

```TypeScript
spans?: AccessibilitySpan[]
```

Array of accessibility hyperlink text information of the component. Default value: empty array.

**Type:** [AccessibilitySpan](arkts-accessibility-accessibilityextensioncontext-accessibilityspan-i-sys.md)[]

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## startIndex

```TypeScript
startIndex?: number
```

Index of the first list item on the screen.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## supportedActionNames

```TypeScript
supportedActionNames?: Array<string>
```

Supported action names. Default value: empty array.

**Type:** Array&lt;string&gt;

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## text

```TypeScript
text?: string
```

Text content of the element.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## textLengthLimit

```TypeScript
textLengthLimit?: number
```

Maximum text length of the element. Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## textMoveUnit

```TypeScript
textMoveUnit?: accessibility.TextMoveUnit
```

Movement unit for text reading.

Default value: **char**.

**Type:** [accessibility.TextMoveUnit](arkts-accessibility-accessibility-textmoveunit-t.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## textType

```TypeScript
textType?: string
```

Accessibility text type of the element, configured by the accessibilityTextHint attribute of the component.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## triggerAction

```TypeScript
triggerAction?: AccessibilityAction
```

Action that triggers the element event.

**Type:** [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## type

```TypeScript
type?: WindowType
```

Window type of the element.

**Type:** [WindowType](arkts-accessibility-windowtype-t.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## valueMax

```TypeScript
valueMax?: number
```

Maximum value.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## valueMin

```TypeScript
valueMin?: number
```

Minimum value.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## valueNow

```TypeScript
valueNow?: number
```

Current value.

Default value: **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## windowId

```TypeScript
windowId?: number
```

Window ID.

Default value: **-1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
