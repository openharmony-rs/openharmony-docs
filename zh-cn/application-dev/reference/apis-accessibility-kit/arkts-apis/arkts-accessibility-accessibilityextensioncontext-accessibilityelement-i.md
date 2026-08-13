# AccessibilityElement

无障碍节点元素。在调用 **AccessibilityElement** 的 API 之前，应该调用 [AccessibilityExtensionContext.getAccessibilityFocusedElement()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getAccessibilityFocusedElement) 或 [AccessibilityExtensionContext.getRootInActiveWindow()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getRootInActiveWindow) 来获取一个 **AccessibilityElement** 实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface AccessibilityElement--><!--Device-unnamed-export declare interface AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## actionNames

```TypeScript
actionNames(callback: AsyncCallback<Array<string>>): void
```

获取节点元素支持的所有操作名称，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-actionNames(callback: AsyncCallback<Array<string>>): void--><!--Device-AccessibilityElement-actionNames(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回节点元素支持的所有操作名称。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
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

获取节点元素支持的所有操作名称，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-actionNames(): Promise<Array<string>>--><!--Device-AccessibilityElement-actionNames(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回节点元素支持的所有操作名称。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.actionNames().then((data: string[]) => {
  console.info(`succeeded in getting action names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get action names. Code: ${err.code}, message: ${err.message}`);
});
```

## attributeNames

```TypeScript
attributeNames<T extends keyof ElementAttributeValues>(callback: AsyncCallback<Array<T>>): void
```

获取节点元素的所有属性名称，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(callback: AsyncCallback<Array<T>>): void--><!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(callback: AsyncCallback<Array<T>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;T&gt;&gt; | 是 | 回调函数，返回节点元素的所有属性名称。 |

## 示例

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
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

获取节点元素的所有属性名称，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(): Promise<Array<T>>--><!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(): Promise<Array<T>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Promise对象，返回节点元素的所有属性名称。 |

## 示例

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.attributeNames().then((data: ElementAttributeKeys[]) => {
  console.info(`succeeded in getting attribute names, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get attribute names. Code: ${err.code}, message: ${err.message}`);
});
```

## attributeValue

```TypeScript
attributeValue<T extends keyof ElementAttributeValues>(
    attributeName: T,
    callback: AsyncCallback<ElementAttributeValues[T]>
  ): void
```

根据属性名称获取属性值。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-attributeValue<T extends keyof ElementAttributeValues>(    attributeName: T,    callback: AsyncCallback<ElementAttributeValues[T]>  ): void--><!--Device-AccessibilityElement-attributeValue<T extends keyof ElementAttributeValues>(    attributeName: T,    callback: AsyncCallback<ElementAttributeValues[T]>  ): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attributeName | T | 是 | 表示属性的名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ElementAttributeValues[T]&gt; | 是 | 回调函数，返回根据节点属性名称获取的属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300004](../errorcode-accessibility.md#9300004-属性不存在) | This property does not exist. |

## 示例

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let attributeName: ElementAttributeKeys = 'bundleName';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
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

根据属性名称获取属性值，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-attributeValue<T extends keyof ElementAttributeValues>(attributeName: T): Promise<ElementAttributeValues[T]>--><!--Device-AccessibilityElement-attributeValue<T extends keyof ElementAttributeValues>(attributeName: T): Promise<ElementAttributeValues[T]>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attributeName | T | 是 | 表示属性的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ElementAttributeValues[T]&gt; | Promise对象，返回根据节点属性名称获取的属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300004](../errorcode-accessibility.md#9300004-属性不存在) | This property does not exist. |

## 示例

```TypeScript
import { ElementAttributeKeys } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let attributeName: ElementAttributeKeys = 'bundleName';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.attributeValue(attributeName).then((data: string) => {
  console.info(`succeeded in getting attribute value by name, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get attribute value. Code: ${err.code}, message: ${err.message}`);
});
```

## findElement

```TypeScript
findElement(type: 'content', condition: string, callback: AsyncCallback<Array<AccessibilityElement>>): void
```

根据节点内容查询所有节点元素。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'content', condition: string, callback: AsyncCallback<Array<AccessibilityElement>>): void--><!--Device-AccessibilityElement-findElement(type: 'content', condition: string, callback: AsyncCallback<Array<AccessibilityElement>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'content' | 是 | 固定为'content',表示查找的类型为节点元素内容。 |
| condition | string | 是 | 表示查找的条件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | 是 | 回调函数，返回满足指定查询关键字的所有节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition = 'keyword';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.findElement('content', condition, (err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
});
```

## findElement

```TypeScript
findElement(type: 'content', condition: string): Promise<Array<AccessibilityElement>>
```

根据节点内容查询所有节点元素，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'content', condition: string): Promise<Array<AccessibilityElement>>--><!--Device-AccessibilityElement-findElement(type: 'content', condition: string): Promise<Array<AccessibilityElement>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'content' | 是 | 固定为'content', 表示查找的类型为节点元素内容。 |
| condition | string | 是 | 表示查找的条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise对象，返回满足指定查询关键字的所有节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition = 'keyword';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.findElement('content', condition).then((data: AccessibilityElement[]) => {
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

## findElement

```TypeScript
findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback<AccessibilityElement>): void
```

根据焦点元素类型查询节点元素，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityElement-findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusType' | 是 | 固定为'focusType'，表示查询的类型为节点的焦点元素类型。 |
| condition | [FocusType](arkts-accessibility-focustype-t.md) | 是 | 表示查询焦点元素的类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | 是 | 回调函数，返回满足指定查询焦点元素类型的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { FocusType, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusType = 'normal';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.findElement('focusType', condition, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
});
```

## findElement

```TypeScript
findElement(type: 'focusType', condition: FocusType): Promise<AccessibilityElement>
```

根据焦点元素类型查询节点元素，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'focusType', condition: FocusType): Promise<AccessibilityElement>--><!--Device-AccessibilityElement-findElement(type: 'focusType', condition: FocusType): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusType' | 是 | 固定为'focusType'，表示查询的类型为节点的焦点元素类型。 |
| condition | [FocusType](arkts-accessibility-focustype-t.md) | 是 | 表示查询焦点元素的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回满足指定查询焦点元素类型的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { FocusType, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusType = 'normal';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.findElement('focusType', condition).then((data: AccessibilityElement) => {
  console.info(`succeeded in finding element,${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

## findElement

```TypeScript
findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback<AccessibilityElement>): void
```

根据下一焦点元素方向查询节点元素，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityElement-findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusDirection' | 是 | 固定为'focusDirection', 表示查询的类型为节点的下一焦点元素方向。 |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | 是 | 表示下一查询焦点元素的方向。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | 是 | 回调函数，返回满足指定查询下一焦点元素方向的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { FocusDirection, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusDirection = 'up';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.findElement('focusDirection', condition, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
});
```

## findElement

```TypeScript
findElement(type: 'focusDirection', condition: FocusDirection): Promise<AccessibilityElement>
```

根据下一焦点元素方向查询节点元素，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'focusDirection', condition: FocusDirection): Promise<AccessibilityElement>--><!--Device-AccessibilityElement-findElement(type: 'focusDirection', condition: FocusDirection): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusDirection' | 是 | 固定为'focusDirection'，表示查询的类型为节点的下一焦点元素方向。 |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | 是 | 表示查询下一焦点元素的方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回满足指定查询下一焦点元素方向的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { FocusDirection, AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let condition: FocusDirection = 'up';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.findElement('focusDirection', condition).then((data: AccessibilityElement) => {
  console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
});
```

## performAction

```TypeScript
performAction(actionName: string, parameters: object, callback: AsyncCallback<void>): void
```

根据操作名称执行某个操作，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-performAction(actionName: string, parameters: object, callback: AsyncCallback<void>): void--><!--Device-AccessibilityElement-performAction(actionName: string, parameters: object, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionName | string | 是 | 表示属性的名称，取值参考[Action](arkts-accessibility-accessibility-action-t.md#Action)。 |
| parameters | object | 是 | 表示执行操作时所需要的参数；默认为空。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，表示执行指定操作的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let actionName = 'action';
let parameters: object = {};

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
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

根据操作名称执行某个操作，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-performAction(actionName: string, parameters?: object): Promise<void>--><!--Device-AccessibilityElement-performAction(actionName: string, parameters?: object): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionName | string | 是 | 表示属性的名称，取值参考[Action](arkts-accessibility-accessibility-action-t.md#Action)。 |
| parameters | object | 否 | 表示执行操作时所需要的参数；默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

## 示例

无参数Action。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
// Action描述中无明确要求的，均为无参数Action。
rootElement.performAction('click').then(() => {
  console.info(`succeeded in performing action.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
});
```

有参数Action（setSelection）。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
// setSelection示例代码。
rootElement.performAction('setSelection', {
  selectTextBegin: '0', // 表示选择起始位置。
  selectTextEnd: '8',   // 表示选择结束位置。
  selectTextInForWard: true   // true表示为前光标，false表示为后光标。
}).then(() => {
  console.info(`succeeded in performing action`);
}).catch((err: BusinessError) => {
  console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
});
```

有参数Action（setCursorPosition）。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
// setCursorPosition示例代码。
rootElement.performAction('setCursorPosition', {
  offset: '1'   // 表示光标的设置位置。
}).then(() => {
  console.info(`succeeded in performing action`);
}).catch((err: BusinessError) => {
  console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
});
```

## performAction

```TypeScript
performAction(actionName: string, callback: AsyncCallback<void>): void
```

根据操作名称执行某个操作，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityElement-performAction(actionName: string, callback: AsyncCallback<void>): void--><!--Device-AccessibilityElement-performAction(actionName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionName | string | 是 | 表示属性的名称，取值参考[Action](arkts-accessibility-accessibility-action-t.md#Action)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，表示执行指定操作的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let actionName = 'action';

// rootElement是AccessibilityElement的实例，通过getFocusElement()或getWindowRootElement()获取
rootElement.performAction(actionName, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to perform action. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in performing action, actionName is ${actionName}`);
});
```

