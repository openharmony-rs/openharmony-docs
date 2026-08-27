# AccessibilityElement

无障碍节点元素，提供查询父/子元素、按内容或焦点方向查找元素、执行无障碍操作等能力，适用于无障碍辅助应用需要与界面节点交互和操作的场景。调用AccessibilityElement的方法前，先通过 [AccessibilityExtensionContext.getAccessibilityFocusedElement()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getaccessibilityfocusedelement) 或[AccessibilityExtensionContext.getRootInActiveWindow()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getrootinactivewindow) 获取AccessibilityElement实例。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## enableScreenCurtain

```TypeScript
enableScreenCurtain(isEnable: boolean): void
```

开启或关闭幕帘屏。幕帘屏开启后，屏幕显示内容将被隐藏（屏幕变暗），但设备仍可正常响应操作。

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnable | boolean | 是 | true表示打开幕帘屏功能，false表示关闭幕帘屏功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

**示例**

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

根据action指定的操作类型和parameters，对无障碍节点元素执行相应操作。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md) | 是 | 无障碍节点可执行的操作。 |
| parameters | [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md) | 否 | 执行操作时设置的参数值。当执行需要额外参数配置的操作（如SET_SELECTION、SET_CURSOR_POSITION等）时传入此参数；执行无参数操作（如 CLICK等）时不需要传入。不传入时默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

**示例**

无参数Action。

```TypeScript
// 无参数Action示例：
import { AccessibilityAction } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，需通过AccessibilityExtensionContext.getAccessibilityFocusedElement()或getRootInActiveWindow()获取。
// Action描述中无明确要求的，均为无参数Action。
rootElement.executeAction(AccessibilityAction.CLICK).then(() => {
  console.info(`succeeded in performing action CLICK`);
}).catch((err: BusinessError) => {
  console.error(`Failed to perform action CLICK. Code: ${err?.code}, message: ${err?.message}`);
});
```

有参数Action（setSelection）。

```TypeScript
// 有参数Action示例：
import { AccessibilityAction, Parameter } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// selectTextBegin：表示选择起始位置。
// selectTextEnd：表示选择结束位置。
// selectTextInForWard：true表示为前光标，false表示为后光标。
let parameter : Parameter = { selectTextBegin: '0', selectTextEnd: '8', selectTextInForWard: true };
// rootElement是AccessibilityElement的实例，需通过AccessibilityExtensionContext.getAccessibilityFocusedElement()或getRootInActiveWindow()获取。
// setSelection示例代码。
rootElement.executeAction(AccessibilityAction.SET_SELECTION, parameter).then(() => {
  console.info(`succeeded in performing action SET_SELECTION`);
}).catch((err: BusinessError) => {
  console.error(`Failed to perform action SET_SELECTION. Code: ${err?.code}, message: ${err?.message}`);
});
```

有参数Action（setCursorPosition）。

```TypeScript
// 有参数Action示例：
import { AccessibilityAction, Parameter } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// offset：表示光标的设置位置。
let parameter : Parameter = { offset: '1' };
// rootElement是AccessibilityElement的实例，需通过AccessibilityExtensionContext.getAccessibilityFocusedElement()或getRootInActiveWindow()获取。
// setCursorPosition示例代码。
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

根据组件配置的accessibilityTextHint无障碍文本类型查询所有节点元素。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textType' | 是 | 固定为'textType'，表示根据文本类型查找节点元素。 |
| condition | string | 是 | 表示查找的无障碍文本类型条件，将返回accessibilityTextHint属性匹配该文本类型的所有节点元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise对象，返回满足指定无障碍文本类型的所有节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// condition的内容需要与目标组件accessibilityTextHint属性的type字段值保持一致。
let condition = 'location'; 

// rootElement是AccessibilityElement的实例，需通过AccessibilityExtensionContext.getAccessibilityFocusedElement()或getRootInActiveWindow()获取。
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

根据elementId查询当前活动窗口下的节点元素。使用Promise异步回调。与[findElementById](#findelementbyid)均根据元素ID查找节点元素，功能等价，推荐优先使用findElementById。

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'elementId' | 是 | 固定为'elementId'，表示根据elementId查询当前活动窗口下的节点元素。 |
| condition | number | 是 | 表示要查询的节点元素的elementId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回满足指定查询条件的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// elementId为10。
let condition = 10;

// rootElement是AccessibilityElement的实例，需通过AccessibilityExtensionContext.getAccessibilityFocusedElement()或getRootInActiveWindow()获取。
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

根据元素的内容文本查找节点元素，将返回包含指定文本的所有节点元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | 要查找的元素内容文本，设置后将返回包含该文本内容的所有节点元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise对象，返回包含指定内容的元素列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

**示例**

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

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

根据焦点方向查找元素。使用Promise异步回调。与 [findElementsByCondition](#findelementsbycondition) 相比，本方法主要用于查找Web组件；findElementsByCondition主要用于查找UI组件。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | 是 | 焦点方向，用于指定查找元素的搜索方向，如'forward'表示向前查找、'backward'表示向后查找等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回指定焦点方向的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

**示例**

```TypeScript
// Page.ets
// 点击TextInput使其成为无障碍焦点元素，向上方向的下一个焦点元素是Text#connect。
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

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

## findElementByFocusDirection

```TypeScript
findElementByFocusDirection(condition: FocusDirection, type: FocusRuleType): Promise<AccessibilityElement>
```

根据焦点方向和聚焦类型查找元素。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | 是 | 焦点方向。 |
| type | [FocusRuleType](arkts-accessibility-accessibility-focusruletype-e-sys.md) | 是 | 聚焦类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回指定焦点方向上符合聚焦类型的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

**示例**

```TypeScript
// Page.ets
// 点击“二级标题1”，使其成为无障碍焦点元素。下一个聚焦类型为标题焦点元素，是“二级标题2”。
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        
    SubHeader({
      secondaryTitle: '二级标题1',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: '操作',
        action: () => {
          Prompt.showToast({ message: 'demo' });
        }
      }]
    })

    TextInput({ placeholder: 'please input...' })
        .id('text_input')
        .fontSize($r('app.float.page_text_font_size'))

    SubHeader({
      secondaryTitle: '二级标题2',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: '操作',
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

根据元素ID查找当前活动窗口下的节点元素。使用Promise异步回调。与[findElement('elementId')](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md#findelementcontent)功能等价，推荐优先使用本 方法。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | number | 是 | 表示要查询的节点元素的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回指定ID的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

**示例**

```TypeScript
// Page.ets
// 点击TextInput使其成为无障碍焦点元素。
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

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

根据提示文本查找元素，将返回accessibilityTextHint属性匹配该文本的所有节点元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | 要查找的元素提示文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise对象，返回包含指定提示文本的元素列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

**示例**

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

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

查询满足条件的可聚焦节点。使用Promise异步回调。与[findElementByFocusDirection](#findelementbyfocusdirection)相 比，本方法主要用于查找UI组件；findElementByFocusDirection主要用于查找Web组件。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | [FocusRule](arkts-accessibility-focusrule-t-sys.md) | 是 | 检查当前节点及其子节点的规则。 |
| condition | [FocusCondition](arkts-accessibility-focuscondition-t-sys.md) | 是 | 表示查询可聚焦节点方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FocusMoveResult](arkts-accessibility-accessibilityextensioncontext-focusmoveresult-i-sys.md)&gt; | Promise对象，返回包含查询到的无障碍节点列表及查询结果状态码的FocusMoveResult对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityElement, FocusMoveResult } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

## findElementsByCondition

```TypeScript
findElementsByCondition(rule: FocusRule, condition: FocusCondition, type: FocusRuleType): Promise<FocusMoveResult>
```

根据规则和查询条件查找目标类型的可聚焦节点。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | [FocusRule](arkts-accessibility-focusrule-t-sys.md) | 是 | 检查当前节点及其子节点的规则。 |
| condition | [FocusCondition](arkts-accessibility-focuscondition-t-sys.md) | 是 | 表示查询可聚焦节点方式。 |
| type | [FocusRuleType](arkts-accessibility-accessibility-focusruletype-e-sys.md) | 是 | 聚焦类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FocusMoveResult](arkts-accessibility-accessibilityextensioncontext-focusmoveresult-i-sys.md)&gt; | Promise对象，返回查询结果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
// Page.ets
  build() {
    Text('Connect')
        .id('connect')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        
    SubHeader({
      secondaryTitle: '二级标题1',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: '操作',
        action: () => {
          Prompt.showToast({ message: 'demo' });
        }
      }]
    })

    TextInput({ placeholder: 'please input...' })
        .id('text_input')
        .fontSize($r('app.float.page_text_font_size'))

    SubHeader({
      secondaryTitle: '二级标题2',
      operationType: OperationType.BUTTON,
      operationItem: [{
        value: '操作',
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

获取元素的子元素列表。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise对象，返回当前元素的子元素列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

获取文本组件中光标位置。使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取光标位置成功，err为undefined，data为光标在文本中的位置索引；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，需通过AccessibilityExtensionContext.getAccessibilityFocusedElement()或getRootInActiveWindow()获取。
rootElement.getCursorPosition((err: BusinessError, data: number) => {
  if (err && err.code) {
    console.error(`Failed to get cursor position. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting cursor position, ${data}`);
});
```

## getCursorPosition

```TypeScript
getCursorPosition(): Promise<number>
```

获取文本组件中光标位置。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回当前光标所处位置。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，需通过AccessibilityExtensionContext.getAccessibilityFocusedElement()或getRootInActiveWindow()获取。
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

获取无障碍节点元素的父元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回当前元素的父元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

获取活动窗口中的根元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回活动窗口中的根元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext是AccessibilityExtensionContext的实例，需通过AccessibilityExtensionAbility子类实例的context属性获取，详见使用说明。
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

表示元素是否因无障碍目的获得焦点。true表示已获得焦点，false表示未获得焦点。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityGroup

```TypeScript
accessibilityGroup?: boolean
```

元素是否为无障碍组。true表示元素是无障碍组，false表示元素不是无障碍组。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

组件的无障碍级别。'auto'：当前组件由无障碍分组服务和ArkUI进行综合判断组件是否可被辅助功能识别。'yes'：当前组件可被辅助功能识别。'no'：当前组件不可被辅助功能识别。'no-hide-descendants'：当前组件及其所有子组件不可被辅助功能识别。默认值：'auto'。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId?: number
```

下一个要获得焦点的组件的ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityPreviousFocusId

```TypeScript
accessibilityPreviousFocusId?: number
```

上一个要获得焦点的组件的ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityScrollable

```TypeScript
accessibilityScrollable?: boolean
```

元素是否因无障碍目的而可滚动。优先级高于scrollable，即当accessibilityScrollable与scrollable取值冲突时以accessibilityScrollable为准。true表示元素可滚动，false表示元素不可滚动。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityStateDescription

```TypeScript
accessibilityStateDescription?: string
```

元素的自定义无障碍状态播报文本信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityText

```TypeScript
accessibilityText?: string
```

元素的无障碍文本信息。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityVisible

```TypeScript
accessibilityVisible?: boolean
```

组件是否无障碍可见。true表示可见，false表示不可见。默认值：true。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## belongTreeId

```TypeScript
belongTreeId?: number
```

表示元素所属的组件树ID。默认值为-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

包名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## checkable

```TypeScript
checkable?: boolean
```

元素是否可勾选。true表示可勾选，false表示不可勾选。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## checked

```TypeScript
checked?: boolean
```

元素是否已勾选。true表示已勾选，false表示未勾选。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## childrenIds

```TypeScript
childrenIds?: Array<number>
```

组件的子元素ID列表。默认值：空数组。

**类型：** Array&lt;number&gt;

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## childrenTreeId

```TypeScript
childrenTreeId?: number
```

表示元素的子组件树ID。默认值为-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## clickable

```TypeScript
clickable?: boolean
```

元素是否可点击。true表示可点击，false表示不可点击。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## clip

```TypeScript
clip?: boolean
```

组件是否需要裁剪。true表示需要裁剪，false表示不需要裁剪。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## componentId

```TypeScript
componentId?: number
```

元素所属组件的ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## componentType

```TypeScript
componentType?: string
```

元素所属组件的类型。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## contents

```TypeScript
contents?: Array<string>
```

元素显示内容。默认值：空数组。

**类型：** Array&lt;string&gt;

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## currentIndex

```TypeScript
currentIndex?: number
```

当前项的索引。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## currentItem

```TypeScript
currentItem?: AccessibilityGrid
```

组件网格中的当前项。

**类型：** [AccessibilityGrid](arkts-accessibility-accessibilityextensioncontext-accessibilitygrid-i-sys.md)

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customActions

```TypeScript
customActions?: Array<string>
```

元素支持的自定义操作列表。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customComponentType

```TypeScript
customComponentType?: string
```

自定义组件类型。与元素的[AccessibilityRoleType](../../apis-arkui/arkts-components/arkts-arkui-accessibilityroletype-e.md)类型所对应。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## description

```TypeScript
description?: string
```

元素的描述信息。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## editable

```TypeScript
editable?: boolean
```

元素是否可编辑。true表示可编辑，false表示不可编辑。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## endIndex

```TypeScript
endIndex?: number
```

屏幕上显示的最后一个列表项的索引。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## error

```TypeScript
error?: string
```

元素的错误状态。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo?: string
```

元素的额外信息。值为JSON字符串。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## focusable

```TypeScript
focusable?: boolean
```

元素是否可获得焦点（此处指无障碍焦点，与输入焦点不同）。true表示可获得焦点，false表示不可获得焦点。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## hintText

```TypeScript
hintText?: string
```

提示文本。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## hotArea

```TypeScript
hotArea?: Rect
```

元素的可触摸区域。

**类型：** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## inputType

```TypeScript
inputType?: number
```

输入文本的类型，不同数值对应不同的输入模式：0表示无特定类型；1表示文本；2表示邮箱；3表示日期；4表示时间；5表示数字；6表示密码；7表示电话号码；8表示用户名；9表示新密码。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## inspectorKey

```TypeScript
inspectorKey?: string
```

检查器键。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isActive

```TypeScript
isActive?: boolean
```

元素是否处于活动状态。true表示活动状态，false表示非活动状态。默认值：true。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isEnable

```TypeScript
isEnable?: boolean
```

元素是否启用。true表示启用，false表示未启用。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isEssential

```TypeScript
isEssential?: boolean
```

表示元素对用户是否是必需的。true表示元素是必需的，false表示元素不是必需的，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isFocused

```TypeScript
isFocused?: boolean
```

表示元素是否已获得焦点（此处指无障碍焦点，与输入焦点不同）。true表示已获得焦点，false表示未获得焦点。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isHint

```TypeScript
isHint?: boolean
```

元素是否为提示信息。true表示元素是提示信息，false表示非提示信息。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isPassword

```TypeScript
isPassword?: boolean
```

元素是否为密码。true表示元素是密码，false表示不是密码。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isVisible

```TypeScript
isVisible?: boolean
```

元素是否可见。true表示元素可见，false表示元素不可见。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## itemCount

```TypeScript
itemCount?: number
```

项目总数。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## lastContent

```TypeScript
lastContent?: string
```

最后一项内容。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## layer

```TypeScript
layer?: number
```

元素的显示层级。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## longClickable

```TypeScript
longClickable?: boolean
```

元素是否可长按。true表示可长按，false表示不可长按。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## mainWindowId

```TypeScript
mainWindowId?: number
```

组件的主窗口ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## navDestinationId

```TypeScript
navDestinationId?: number
```

组件的导航目标ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: number
```

内容区域相对于可滚动组件（如List和Grid）顶部坐标的像素偏移量，单位为像素（px）。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## pageId

```TypeScript
pageId?: number
```

页面ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## parentId

```TypeScript
parentId?: number
```

组件的父元素ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## pluralLineSupported

```TypeScript
pluralLineSupported?: boolean
```

表示元素是否支持多行文本。true表示支持，false表示不支持。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect?: Rect
```

元素的区域。

**类型：** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## resourceName

```TypeScript
resourceName?: string
```

元素的资源名称。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## screenRect

```TypeScript
screenRect?: Rect
```

元素的显示区域。

**类型：** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## scrollable

```TypeScript
scrollable?: boolean
```

元素是否可滚动。true表示元素可滚动，false表示不可滚动。当与accessibilityScrollable取值冲突时，以accessibilityScrollable为准。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selected

```TypeScript
selected?: boolean
```

元素是否已选中。true表示已选中，false表示未选中。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## sourceType

```TypeScript
sourceType?: AccessibilitySourceType
```

组件来源类型，用于区分默认组件和新增、修改的虚拟组件。

**类型：** [AccessibilitySourceType](arkts-accessibility-accessibility-accessibilitysourcetype-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## spans

```TypeScript
spans?: AccessibilitySpan[]
```

组件的辅助功能超链接文本信息数组。默认值：空数组。

**类型：** [AccessibilitySpan](arkts-accessibility-accessibilityextensioncontext-accessibilityspan-i-sys.md)[]

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## startIndex

```TypeScript
startIndex?: number
```

屏幕上第一个列表项的索引。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## supportedActionNames

```TypeScript
supportedActionNames?: Array<string>
```

支持的操作名称。默认值：空数组。

**类型：** Array&lt;string&gt;

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## text

```TypeScript
text?: string
```

元素的文本内容。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## textLengthLimit

```TypeScript
textLengthLimit?: number
```

元素的最大文本长度。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## textMoveUnit

```TypeScript
textMoveUnit?: accessibility.TextMoveUnit
```

文本朗读时的移动单位。默认值：char。

**类型：** accessibility.TextMoveUnit

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## textType

```TypeScript
textType?: string
```

元素的无障碍文本类型，由组件的accessibilityTextHint属性配置。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## triggerAction

```TypeScript
triggerAction?: AccessibilityAction
```

触发元素事件的操作。

**类型：** [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md)

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type?: WindowType
```

元素的窗口类型。

**类型：** [WindowType](arkts-accessibility-windowtype-t.md)

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## valueMax

```TypeScript
valueMax?: number
```

最大值。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## valueMin

```TypeScript
valueMin?: number
```

最小值。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## valueNow

```TypeScript
valueNow?: number
```

当前值。默认值：0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId?: number
```

窗口ID。默认值：-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。
