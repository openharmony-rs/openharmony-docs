# AccessibilityElement

无障碍节点元素。在调用 **AccessibilityElement** 的 API 之前，应该调用[AccessibilityExtensionContext.getAccessibilityFocusedElement()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getaccessibilityfocusedelement-1)或 [AccessibilityExtensionContext.getRootInActiveWindow()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getrootinactivewindow-1)来获取一个 **AccessibilityElement** 实例。

**起始版本：** 9

<!--Device-unnamed-export declare interface AccessibilityElement--><!--Device-unnamed-export declare interface AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## actionNames

```TypeScript
actionNames(callback: AsyncCallback<Array<string>>): void
```

获取节点元素支持的所有操作名称，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-actionNames(callback: AsyncCallback<Array<string>>): void--><!--Device-AccessibilityElement-actionNames(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<string>> | 是 | 回调函数，返回节点元素支持的所有操作名称。 |

## actionNames

```TypeScript
actionNames(): Promise<Array<string>>
```

获取节点元素支持的所有操作名称，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-actionNames(): Promise<Array<string>>--><!--Device-AccessibilityElement-actionNames(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<string>> | Promise对象，返回节点元素支持的所有操作名称。 |

## attributeNames

```TypeScript
attributeNames<T extends keyof ElementAttributeValues>(callback: AsyncCallback<Array<T>>): void
```

获取节点元素的所有属性名称，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(callback: AsyncCallback<Array<T>>): void--><!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(callback: AsyncCallback<Array<T>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<T>> | 是 | 回调函数，返回节点元素的所有属性名称。 |

## attributeNames

```TypeScript
attributeNames<T extends keyof ElementAttributeValues>(): Promise<Array<T>>
```

获取节点元素的所有属性名称，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(): Promise<Array<T>>--><!--Device-AccessibilityElement-attributeNames<T extends keyof ElementAttributeValues>(): Promise<Array<T>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<T>> | Promise对象，返回节点元素的所有属性名称。 |

## attributeValue

```TypeScript
attributeValue<T extends keyof ElementAttributeValues>(
    attributeName: T,
    callback: AsyncCallback<ElementAttributeValues[T]>
  ): void
```

根据属性名称获取属性值。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-attributeValue<T extends keyof ElementAttributeValues>(
    attributeName: T,
    callback: AsyncCallback<ElementAttributeValues[T]>
  ): void--><!--Device-AccessibilityElement-attributeValue<T extends keyof ElementAttributeValues>(
    attributeName: T,
    callback: AsyncCallback<ElementAttributeValues[T]>
  ): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attributeName | T | 是 | 表示属性的名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<ElementAttributeValues[T]> | 是 | 回调函数，返回根据节点属性名称获取的属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300004](../errorcode-accessibility.md#9300004-属性不存在) | This property does not exist. |

## attributeValue

```TypeScript
attributeValue<T extends keyof ElementAttributeValues>(attributeName: T): Promise<ElementAttributeValues[T]>
```

根据属性名称获取属性值，使用Promise异步回调。

**起始版本：** 9

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
| Promise<ElementAttributeValues[T]> | Promise对象，返回根据节点属性名称获取的属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300004](../errorcode-accessibility.md#9300004-属性不存在) | This property does not exist. |

## findElement

```TypeScript
findElement(type: 'content', condition: string, callback: AsyncCallback<Array<AccessibilityElement>>): void
```

根据节点内容查询所有节点元素。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'content', condition: string, callback: AsyncCallback<Array<AccessibilityElement>>): void--><!--Device-AccessibilityElement-findElement(type: 'content', condition: string, callback: AsyncCallback<Array<AccessibilityElement>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'content' | 是 | 固定为'content',表示查找的类型为节点元素内容。 |
| condition | string | 是 | 表示查找的条件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<AccessibilityElement>> | 是 | 回调函数，返回满足指定查询关键字的所有节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## findElement

```TypeScript
findElement(type: 'content', condition: string): Promise<Array<AccessibilityElement>>
```

根据节点内容查询所有节点元素，使用Promise异步回调。

**起始版本：** 9

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
| Promise<Array<AccessibilityElement>> | Promise对象，返回满足指定查询关键字的所有节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## findElement

```TypeScript
findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback<AccessibilityElement>): void
```

根据焦点元素类型查询节点元素，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityElement-findElement(type: 'focusType', condition: FocusType, callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusType' | 是 | 固定为'focusType'，表示查询的类型为节点的焦点元素类型。 |
| condition | [FocusType](arkts-accessibility-focustype-t.md) | 是 | 表示查询焦点元素的类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AccessibilityElement> | 是 | 回调函数，返回满足指定查询焦点元素类型的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## findElement

```TypeScript
findElement(type: 'focusType', condition: FocusType): Promise<AccessibilityElement>
```

根据焦点元素类型查询节点元素，使用Promise异步回调。

**起始版本：** 9

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
| Promise<AccessibilityElement> | Promise对象，返回满足指定查询焦点元素类型的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## findElement

```TypeScript
findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback<AccessibilityElement>): void
```

根据下一焦点元素方向查询节点元素，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityElement-findElement(type: 'focusDirection', condition: FocusDirection, callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusDirection' | 是 | 固定为'focusDirection', 表示查询的类型为节点的下一焦点元素方向。 |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | 是 | 表示下一查询焦点元素的方向。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AccessibilityElement> | 是 | 回调函数，返回满足指定查询下一焦点元素方向的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## findElement

```TypeScript
findElement(type: 'focusDirection', condition: FocusDirection): Promise<AccessibilityElement>
```

根据下一焦点元素方向查询节点元素，使用Promise异步回调。

**起始版本：** 9

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
| Promise<AccessibilityElement> | Promise对象，返回满足指定查询下一焦点元素方向的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## performAction

```TypeScript
performAction(actionName: string, parameters: object, callback: AsyncCallback<void>): void
```

根据操作名称执行某个操作，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-performAction(actionName: string, parameters: object, callback: AsyncCallback<void>): void--><!--Device-AccessibilityElement-performAction(actionName: string, parameters: object, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionName | string | 是 | 表示属性的名称，取值参考[Action](arkts-accessibility-accessibility-action-t.md)。 |
| parameters | object | 是 | 表示执行操作时所需要的参数；默认为空。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，表示执行指定操作的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

## performAction

```TypeScript
performAction(actionName: string, parameters?: object): Promise<void>
```

根据操作名称执行某个操作，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-performAction(actionName: string, parameters?: object): Promise<void>--><!--Device-AccessibilityElement-performAction(actionName: string, parameters?: object): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionName | string | 是 | 表示属性的名称，取值参考[Action](arkts-accessibility-accessibility-action-t.md)。 |
| parameters | object | 否 | 表示执行操作时所需要的参数；默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

## performAction

```TypeScript
performAction(actionName: string, callback: AsyncCallback<void>): void
```

根据操作名称执行某个操作，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 12

<!--Device-AccessibilityElement-performAction(actionName: string, callback: AsyncCallback<void>): void--><!--Device-AccessibilityElement-performAction(actionName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionName | string | 是 | 表示属性的名称，取值参考[Action](arkts-accessibility-accessibility-action-t.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，表示执行指定操作的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

