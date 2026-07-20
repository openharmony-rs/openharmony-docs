# AccessibilityElement

无障碍节点元素。在调用 **AccessibilityElement** 的 API 之前，应该调用[AccessibilityExtensionContext.getAccessibilityFocusedElement()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getaccessibilityfocusedelement-1)或 [AccessibilityExtensionContext.getRootInActiveWindow()](arkts-accessibility-accessibilityextensioncontext-c-sys.md#getrootinactivewindow-1)来获取一个 **AccessibilityElement** 实例。

**起始版本：** 9

<!--Device-unnamed-export declare interface AccessibilityElement--><!--Device-unnamed-export declare interface AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

<a id="enablescreencurtain"></a>
## enableScreenCurtain

```TypeScript
enableScreenCurtain(isEnable: boolean): void
```

提供开启/关闭幕帘屏的能力。

**起始版本：** 12

<!--Device-AccessibilityElement-enableScreenCurtain(isEnable: boolean): void--><!--Device-AccessibilityElement-enableScreenCurtain(isEnable: boolean): void-End-->

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
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

<a id="executeaction"></a>
## executeAction

```TypeScript
executeAction(action: AccessibilityAction, parameters?: Parameter): Promise<void>
```

根据action指定的操作类型和parameters传入的参数，执行特定操作。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-executeAction(action: AccessibilityAction, parameters?: Parameter): Promise<void>--><!--Device-AccessibilityElement-executeAction(action: AccessibilityAction, parameters?: Parameter): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [AccessibilityAction](../../apis-arkui/arkts-components/arkts-arkui-accessibilityaction-e.md) | 是 | 无障碍节点可执行的操作。 |
| parameters | [Parameter](arkts-accessibility-parameter-t-sys.md) | 否 | 执行操作时设置的参数值，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300005](../errorcode-accessibility.md#9300005-不支持该操作) | This action is not supported. |

<a id="findelement"></a>
## findElement

```TypeScript
findElement(type: 'textType', condition: string): Promise<Array<AccessibilityElement>>
```

根据节点配置的accessibilityTextHint无障碍文本类型查询所有节点元素，使用Promise异步回调。

**起始版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'textType', condition: string): Promise<Array<AccessibilityElement>>--><!--Device-AccessibilityElement-findElement(type: 'textType', condition: string): Promise<Array<AccessibilityElement>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textType' | 是 | 固定为'textType', 表示根据文本类型查找节点元素。 |
| condition | string | 是 | 表示查找的条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AccessibilityElement&gt;&gt; | Promise对象，返回满足指定查询关键字的所有节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

<a id="findelement-1"></a>
## findElement

```TypeScript
findElement(type: 'elementId', condition: number): Promise<AccessibilityElement>
```

根据elementId查询当前活动窗口下的节点元素。使用Promise异步回调。

**起始版本：** 12

<!--Device-AccessibilityElement-findElement(type: 'elementId', condition: long): Promise<AccessibilityElement>--><!--Device-AccessibilityElement-findElement(type: 'elementId', condition: long): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'elementId' | 是 | 固定为'elementId', 表示根据elementId查询当前活动窗口下的节点元素。 |
| condition | number | 是 | 表示要查询的节点元素的elementId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AccessibilityElement&gt; | Promise对象，返回满足指定查询条件的节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

<a id="findelementbycontent"></a>
## findElementByContent

```TypeScript
findElementByContent(condition: string): Promise<Array<AccessibilityElement>>
```

根据内容查找元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-findElementByContent(condition: string): Promise<Array<AccessibilityElement>>--><!--Device-AccessibilityElement-findElementByContent(condition: string): Promise<Array<AccessibilityElement>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | 内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AccessibilityElement&gt;&gt; | Promise对象，返回包含指定内容的元素列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

<a id="findelementbyfocusdirection"></a>
## findElementByFocusDirection

```TypeScript
findElementByFocusDirection(condition: FocusDirection): Promise<AccessibilityElement>
```

根据焦点方向查找元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-findElementByFocusDirection(condition: FocusDirection): Promise<AccessibilityElement>--><!--Device-AccessibilityElement-findElementByFocusDirection(condition: FocusDirection): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | [FocusDirection](arkts-accessibility-focusdirection-t.md) | 是 | 焦点方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AccessibilityElement&gt; | Promise对象，返回指定焦点方向的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

<a id="findelementbyid"></a>
## findElementById

```TypeScript
findElementById(condition: number): Promise<AccessibilityElement>
```

根据元素 ID 查找元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-findElementById(condition: long): Promise<AccessibilityElement>--><!--Device-AccessibilityElement-findElementById(condition: long): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | number | 是 | 元素 ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AccessibilityElement&gt; | Promise对象，返回指定 ID 的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

<a id="findelementsbyaccessibilityhinttext"></a>
## findElementsByAccessibilityHintText

```TypeScript
findElementsByAccessibilityHintText(condition: string): Promise<Array<AccessibilityElement>>
```

根据提示文本查找元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-findElementsByAccessibilityHintText(condition: string): Promise<Array<AccessibilityElement>>--><!--Device-AccessibilityElement-findElementsByAccessibilityHintText(condition: string): Promise<Array<AccessibilityElement>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | 提示文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AccessibilityElement&gt;&gt; | Promise对象，返回包含指定提示文本的元素列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |

<a id="findelementsbycondition"></a>
## findElementsByCondition

```TypeScript
findElementsByCondition(rule: FocusRule, condition: FocusCondition): Promise<FocusMoveResult>
```

查询满足条件的可聚焦节点。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-findElementsByCondition(rule: FocusRule, condition: FocusCondition): Promise<FocusMoveResult>--><!--Device-AccessibilityElement-findElementsByCondition(rule: FocusRule, condition: FocusCondition): Promise<FocusMoveResult>-End-->

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
| Promise&lt;FocusMoveResult&gt; | Promise对象，返回查询结果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

<a id="getchildren"></a>
## getChildren

```TypeScript
getChildren(): Promise<Array<AccessibilityElement>>
```

获取元素的子元素列表。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-getChildren(): Promise<Array<AccessibilityElement>>--><!--Device-AccessibilityElement-getChildren(): Promise<Array<AccessibilityElement>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AccessibilityElement&gt;&gt; | Promise对象，返回当前元素的子元素列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

<a id="getcursorposition"></a>
## getCursorPosition

```TypeScript
getCursorPosition(callback: AsyncCallback<number>): void
```

获取文本组件中光标位置，使用callback异步回调。

**起始版本：** 12

<!--Device-AccessibilityElement-getCursorPosition(callback: AsyncCallback<int>): void--><!--Device-AccessibilityElement-getCursorPosition(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，表示文本组件中光标位置。 |

<a id="getcursorposition-1"></a>
## getCursorPosition

```TypeScript
getCursorPosition(): Promise<number>
```

获取文本组件中光标位置，使用Promise异步回调。

**起始版本：** 12

<!--Device-AccessibilityElement-getCursorPosition(): Promise<int>--><!--Device-AccessibilityElement-getCursorPosition(): Promise<int>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回当前光标所处位置。 |

<a id="getparent"></a>
## getParent

```TypeScript
getParent(): Promise<AccessibilityElement>
```

获取无障碍节点元素的父元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-getParent(): Promise<AccessibilityElement>--><!--Device-AccessibilityElement-getParent(): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AccessibilityElement&gt; | Promise对象，返回当前元素的父元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

<a id="getroot"></a>
## getRoot

```TypeScript
getRoot(): Promise<AccessibilityElement>
```

获取活动窗口中的根元素。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityElement-getRoot(): Promise<AccessibilityElement>--><!--Device-AccessibilityElement-getRoot(): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AccessibilityElement&gt; | Promise对象，返回活动窗口中的根元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## accessibilityFocused

```TypeScript
accessibilityFocused?: boolean
```

表示元素是否因无障碍目的获得焦点。true表示已获得焦点，false表示未获得焦点。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityFocused?: boolean--><!--Device-AccessibilityElement-accessibilityFocused?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityGroup

```TypeScript
accessibilityGroup?: boolean
```

元素是否为无障碍组。true表示元素是无障碍组，false表示元素不是无障碍组。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityGroup?: boolean--><!--Device-AccessibilityElement-accessibilityGroup?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

组件的无障碍级别。

'auto'：当前组件由无障碍分组服务和ArkUI进行综合判断组件是否可被辅助功能识别。

'yes'：当前组件可被辅助功能识别。

'no'：当前组件不可被辅助功能识别。

'no-hide-descendants'：当前组件及其所有子组件不可被辅助功能识别。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityLevel?: string--><!--Device-AccessibilityElement-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId?: number
```

下一个要获得焦点的组件的ID。

默认值：-1。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityNextFocusId?: long--><!--Device-AccessibilityElement-accessibilityNextFocusId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityPreviousFocusId

```TypeScript
accessibilityPreviousFocusId?: number
```

上一个要获得焦点的组件的ID。

默认值：-1。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityPreviousFocusId?: long--><!--Device-AccessibilityElement-accessibilityPreviousFocusId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityScrollable

```TypeScript
accessibilityScrollable?: boolean
```

元素是否因无障碍目的而可滚动。此属性优先级高于scrollable。

true表示元素可滚动，false表示元素不可滚动。

默认值：true。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityScrollable?: boolean--><!--Device-AccessibilityElement-accessibilityScrollable?: boolean-End-->

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

<!--Device-AccessibilityElement-accessibilityStateDescription?: string--><!--Device-AccessibilityElement-accessibilityStateDescription?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityText

```TypeScript
accessibilityText?: string
```

元素的无障碍文本信息。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityText?: string--><!--Device-AccessibilityElement-accessibilityText?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityVisible

```TypeScript
accessibilityVisible?: boolean
```

组件是否无障碍可见。true表示可见，false表示不可见。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-accessibilityVisible?: boolean--><!--Device-AccessibilityElement-accessibilityVisible?: boolean-End-->

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

<!--Device-AccessibilityElement-belongTreeId?: int--><!--Device-AccessibilityElement-belongTreeId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

包名。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-bundleName?: string--><!--Device-AccessibilityElement-bundleName?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## checkable

```TypeScript
checkable?: boolean
```

元素是否可勾选。true表示可勾选，false表示不可勾选。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-checkable?: boolean--><!--Device-AccessibilityElement-checkable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## checked

```TypeScript
checked?: boolean
```

元素是否已勾选。true表示已勾选，false表示未勾选。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-checked?: boolean--><!--Device-AccessibilityElement-checked?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## childrenIds

```TypeScript
childrenIds?: Array<number>
```

组件的子元素ID列表。

**类型：** Array&lt;number&gt;

**起始版本：** 20

<!--Device-AccessibilityElement-childrenIds?: Array<long>--><!--Device-AccessibilityElement-childrenIds?: Array<long>-End-->

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

<!--Device-AccessibilityElement-childrenTreeId?: int--><!--Device-AccessibilityElement-childrenTreeId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## clickable

```TypeScript
clickable?: boolean
```

元素是否可点击。true表示可点击，false表示不可点击。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-clickable?: boolean--><!--Device-AccessibilityElement-clickable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## clip

```TypeScript
clip?: boolean
```

组件是否需要裁剪。true表示需要裁剪，false表示不需要裁剪。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-clip?: boolean--><!--Device-AccessibilityElement-clip?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## componentId

```TypeScript
componentId?: number
```

元素所属组件的ID。

默认值：-1。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-componentId?: long--><!--Device-AccessibilityElement-componentId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## componentType

```TypeScript
componentType?: string
```

元素所属组件的类型。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-componentType?: string--><!--Device-AccessibilityElement-componentType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## contents

```TypeScript
contents?: Array<string>
```

元素显示内容。

**类型：** Array&lt;string&gt;

**起始版本：** 20

<!--Device-AccessibilityElement-contents?: Array<string>--><!--Device-AccessibilityElement-contents?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## currentIndex

```TypeScript
currentIndex?: number
```

当前项的索引。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-currentIndex?: int--><!--Device-AccessibilityElement-currentIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## currentItem

```TypeScript
currentItem?: AccessibilityGrid
```

组件网格中的当前项。

**类型：** AccessibilityGrid

**起始版本：** 20

<!--Device-AccessibilityElement-currentItem?: AccessibilityGrid--><!--Device-AccessibilityElement-currentItem?: AccessibilityGrid-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customActions

```TypeScript
customActions?: Array<string>
```

Indicates the custom actions supported by the component.

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityElement-customActions?: Array<string>--><!--Device-AccessibilityElement-customActions?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customComponentType

```TypeScript
customComponentType?: string
```

自定义组件类型。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-customComponentType?: string--><!--Device-AccessibilityElement-customComponentType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## description

```TypeScript
description?: string
```

元素的描述信息。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-description?: string--><!--Device-AccessibilityElement-description?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## editable

```TypeScript
editable?: boolean
```

元素是否可编辑。true表示可编辑，false表示不可编辑。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-editable?: boolean--><!--Device-AccessibilityElement-editable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## endIndex

```TypeScript
endIndex?: number
```

屏幕上显示的最后一个列表项的索引。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-endIndex?: int--><!--Device-AccessibilityElement-endIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## error

```TypeScript
error?: string
```

元素的错误状态。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-error?: string--><!--Device-AccessibilityElement-error?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo?: string
```

元素的额外信息。值为JSON字符串。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-extraInfo?: string--><!--Device-AccessibilityElement-extraInfo?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## focusable

```TypeScript
focusable?: boolean
```

元素是否可获得焦点。true表示可获得焦点，false表示不可获得焦点。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-focusable?: boolean--><!--Device-AccessibilityElement-focusable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## hintText

```TypeScript
hintText?: string
```

提示文本。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-hintText?: string--><!--Device-AccessibilityElement-hintText?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## hotArea

```TypeScript
hotArea?: Rect
```

元素的可触摸区域。

**类型：** Rect

**起始版本：** 20

<!--Device-AccessibilityElement-hotArea?: Rect--><!--Device-AccessibilityElement-hotArea?: Rect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## inputType

```TypeScript
inputType?: number
```

输入文本的类型。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-inputType?: int--><!--Device-AccessibilityElement-inputType?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## inspectorKey

```TypeScript
inspectorKey?: string
```

检查器键。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-inspectorKey?: string--><!--Device-AccessibilityElement-inspectorKey?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isActive

```TypeScript
isActive?: boolean
```

元素是否处于活动状态。true表示活动状态，false表示非活动状态。

默认值：true。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-isActive?: boolean--><!--Device-AccessibilityElement-isActive?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isEnable

```TypeScript
isEnable?: boolean
```

元素是否启用。true表示启用，false表示未启用。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-isEnable?: boolean--><!--Device-AccessibilityElement-isEnable?: boolean-End-->

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

<!--Device-AccessibilityElement-isEssential?: boolean--><!--Device-AccessibilityElement-isEssential?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isFocused

```TypeScript
isFocused?: boolean
```

表示元素是否已获得焦点。true表示已获得焦点，false表示未获得焦点。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-isFocused?: boolean--><!--Device-AccessibilityElement-isFocused?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isHint

```TypeScript
isHint?: boolean
```

元素是否为提示信息。true表示元素是提示信息，false表示非提示信息。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-isHint?: boolean--><!--Device-AccessibilityElement-isHint?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isPassword

```TypeScript
isPassword?: boolean
```

元素是否为密码。true表示元素是密码，false表示不是密码。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-isPassword?: boolean--><!--Device-AccessibilityElement-isPassword?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isVisible

```TypeScript
isVisible?: boolean
```

元素是否可见。true表示元素可见，false表示元素不可见。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-isVisible?: boolean--><!--Device-AccessibilityElement-isVisible?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## itemCount

```TypeScript
itemCount?: number
```

项目总数。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-itemCount?: int--><!--Device-AccessibilityElement-itemCount?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## lastContent

```TypeScript
lastContent?: string
```

最后一项内容。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-lastContent?: string--><!--Device-AccessibilityElement-lastContent?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## layer

```TypeScript
layer?: number
```

元素的显示层级。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-layer?: int--><!--Device-AccessibilityElement-layer?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## longClickable

```TypeScript
longClickable?: boolean
```

元素是否可长按。true表示可长按，false表示不可长按。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-longClickable?: boolean--><!--Device-AccessibilityElement-longClickable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## mainWindowId

```TypeScript
mainWindowId?: number
```

组件的主窗口ID。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-mainWindowId?: int--><!--Device-AccessibilityElement-mainWindowId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## navDestinationId

```TypeScript
navDestinationId?: number
```

组件的导航目标ID。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-navDestinationId?: long--><!--Device-AccessibilityElement-navDestinationId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: number
```

内容区域相对于可滚动组件（如List和Grid）顶部坐标的像素偏移量，单位为像素（px）。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-offset?: double--><!--Device-AccessibilityElement-offset?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## pageId

```TypeScript
pageId?: number
```

页面ID。

默认值：-1。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-pageId?: int--><!--Device-AccessibilityElement-pageId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## parentId

```TypeScript
parentId?: number
```

组件的父元素ID。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-parentId?: long--><!--Device-AccessibilityElement-parentId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## pluralLineSupported

```TypeScript
pluralLineSupported?: boolean
```

表示元素是否支持多行文本。true表示支持，false表示不支持。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-pluralLineSupported?: boolean--><!--Device-AccessibilityElement-pluralLineSupported?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect?: Rect
```

元素的区域。

**类型：** Rect

**起始版本：** 20

<!--Device-AccessibilityElement-rect?: Rect--><!--Device-AccessibilityElement-rect?: Rect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## resourceName

```TypeScript
resourceName?: string
```

元素的资源名称。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-resourceName?: string--><!--Device-AccessibilityElement-resourceName?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## screenRect

```TypeScript
screenRect?: Rect
```

元素的显示区域。

**类型：** Rect

**起始版本：** 20

<!--Device-AccessibilityElement-screenRect?: Rect--><!--Device-AccessibilityElement-screenRect?: Rect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## scrollable

```TypeScript
scrollable?: boolean
```

元素是否可滚动。true表示元素可滚动，false表示不可滚动。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-scrollable?: boolean--><!--Device-AccessibilityElement-scrollable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selected

```TypeScript
selected?: boolean
```

元素是否已选中。true表示已选中，false表示未选中。

默认值：false。

**类型：** boolean

**起始版本：** 20

<!--Device-AccessibilityElement-selected?: boolean--><!--Device-AccessibilityElement-selected?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## spans

```TypeScript
spans?: AccessibilitySpan[]
```

组件的跨度数组。

**类型：** AccessibilitySpan[]

**起始版本：** 20

<!--Device-AccessibilityElement-spans?: AccessibilitySpan[]--><!--Device-AccessibilityElement-spans?: AccessibilitySpan[]-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## startIndex

```TypeScript
startIndex?: number
```

屏幕上第一个列表项的索引。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-startIndex?: int--><!--Device-AccessibilityElement-startIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## supportedActionNames

```TypeScript
supportedActionNames?: Array<string>
```

支持的操作名称。

**类型：** Array&lt;string&gt;

**起始版本：** 20

<!--Device-AccessibilityElement-supportedActionNames?: Array<string>--><!--Device-AccessibilityElement-supportedActionNames?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## text

```TypeScript
text?: string
```

元素的文本内容。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-text?: string--><!--Device-AccessibilityElement-text?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## textLengthLimit

```TypeScript
textLengthLimit?: number
```

元素的最大文本长度。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-textLengthLimit?: int--><!--Device-AccessibilityElement-textLengthLimit?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## textMoveUnit

```TypeScript
textMoveUnit?: accessibility.TextMoveUnit
```

文本朗读时的移动单位。

默认值：0。

**类型：** accessibility.TextMoveUnit

**起始版本：** 20

<!--Device-AccessibilityElement-textMoveUnit?: accessibility.TextMoveUnit--><!--Device-AccessibilityElement-textMoveUnit?: accessibility.TextMoveUnit-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## textType

```TypeScript
textType?: string
```

元素的无障碍文本类型，由组件的accessibilityTextHint属性配置。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityElement-textType?: string--><!--Device-AccessibilityElement-textType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## triggerAction

```TypeScript
triggerAction?: AccessibilityAction
```

触发元素事件的操作。

**类型：** AccessibilityAction

**起始版本：** 20

<!--Device-AccessibilityElement-triggerAction?: AccessibilityAction--><!--Device-AccessibilityElement-triggerAction?: AccessibilityAction-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type?: WindowType
```

元素的窗口类型。

**类型：** WindowType

**起始版本：** 20

<!--Device-AccessibilityElement-type?: WindowType--><!--Device-AccessibilityElement-type?: WindowType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## valueMax

```TypeScript
valueMax?: number
```

最大值。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-valueMax?: double--><!--Device-AccessibilityElement-valueMax?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## valueMin

```TypeScript
valueMin?: number
```

最小值。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-valueMin?: double--><!--Device-AccessibilityElement-valueMin?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## valueNow

```TypeScript
valueNow?: number
```

当前值。

默认值：0。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-valueNow?: double--><!--Device-AccessibilityElement-valueNow?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId?: number
```

窗口ID。

默认值：-1。

**类型：** number

**起始版本：** 20

<!--Device-AccessibilityElement-windowId?: int--><!--Device-AccessibilityElement-windowId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

