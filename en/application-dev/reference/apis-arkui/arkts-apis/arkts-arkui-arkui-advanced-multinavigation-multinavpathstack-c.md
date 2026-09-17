# MultiNavPathStack

Implements a navigation stack of the **MultiNavigation** component. Currently, this stack can be created only by the user and cannot be obtained through callbacks. Do not use events or APIs such as **onReady** of **NavDestination** to obtain the navigation stack and perform stack operations, as this may lead to unpredictable issues.

**Inheritance/Implementation:** MultiNavPathStack extends [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md)

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SplitPolicy, MultiNavigation, MultiNavPathStack } from '@kit.ArkUI';
```

## clear

```TypeScript
clear(animated?: boolean): void
```

Clears the navigation stack.

> **NOTE:** 

> If [keepBottomPage](#keepbottompage) is called with **true**, the bottom page of the
> navigation stack is retained.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

## constructor

```TypeScript
constructor()
```

Creates an instance of MultiNavPathStack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableAnimation

```TypeScript
disableAnimation(disable: boolean): void
```

Disables or enables the transition animation in the **MultiNavigation** component.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| disable | boolean | Yes | Whether to disable the transition animation.<br>Default value: **false**.<br>**true**: The transition animation is disabled.<br>**false**: The transition animation is not disabled. |

## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

Obtains the names of all navigation destination pages in the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Names of all navigation destination pages in the navigation stack. |

## getIndexByName

```TypeScript
getIndexByName(name: string): Array<number>
```

Obtains the indexes of all the navigation destination pages that match **name**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Indexes of all the matching navigation destination pages.<br>Value range of the number type: [0, +∞). |

## getParamByIndex

```TypeScript
getParamByIndex(index: number): Object | undefined
```

Obtains the parameter information of the navigation destination page specified by **index**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page.<br>Value range: [0, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| unknown &#124; undefined | **Object**: parameter information of the matching navigation destination page.<br>**undefined**: returned when an invalid index is provided. |

## getParamByName

```TypeScript
getParamByName(name: string): Array<Object>
```

Obtains the parameter information of all the navigation destination pages that match **name**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Object&gt; | Parameter information of all the matching navigation destination pages. |

## keepBottomPage

```TypeScript
keepBottomPage(keepBottom: boolean): void
```

Sets whether to retain the bottom page when the **pop** or **clear** APIs is called.

> **NOTE:** 

> **MultiNavigation** treats the home page as a navigation destination page in the stack. By default, calling
> **pop** or **clear** will also remove the bottom page.
> 
> If this API is called with **TRUE**, **MultiNavigation** will retain the bottom page when the **pop** or
> **clear** API is called.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keepBottom | boolean | Yes | Whether to retain the bottom page.<br>Default value: **false**.<br>**true**: The bottom page is retained.<br>**false**: The bottom page is not retained. |

## moveIndexToTop

```TypeScript
moveIndexToTop(index: number, animated?: boolean): void
```

Moves the navigation destination page specified by **index** to the top of the navigation stack.

> **NOTE:** 

> Depending on the type of page found, **MultiNavigation** performs different actions:

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page.<br>Value range: [0, +∞). |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

Moves the first navigation destination page that matches **name** from the bottom of the navigation stack to the top of the stack.

> **NOTE:** 

> Depending on the type of page found, **MultiNavigation** performs different actions:

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found. |

## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

Pops the top element out of the navigation stack.

> **NOTE:** 

> If [keepBottomPage](#keepbottompage) is called with **true**, the bottom page of the
> navigation stack is retained.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) &#124; undefined | Information about the navigation destination page at the top of the stack. |

## pop

```TypeScript
pop(result?: Object, animated?: boolean): NavPathInfo | undefined
```

Pops the top element out of the navigation stack and invokes the **onPop** callback to pass the page processing result.

> **NOTE:** 

> If [keepBottomPage](#keepbottompage) is called with **true**, the bottom page of the
> navigation stack is retained.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | Object | No | Custom processing result on the page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) &#124; undefined | Information about the navigation destination page at the top of the stack. |

## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

Returns the navigation stack to the page specified by **index**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page.<br>Value range: [0, +∞). |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

Returns the navigation stack to the page specified by **index** and invokes the **onPop** callback to pass the page processing result.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page.<br>Value range: [0, +∞). |
| result | Object | Yes | Custom processing result on the page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

Pops pages until the first navigation destination page that matches **name** from the bottom of the navigation stack is at the top of the stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found.<br>Value range: [-1, +∞). |

## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

Pops pages until the first navigation destination page that matches **name** from the bottom of the navigation stack is at the top of the stack. This API uses the **onPop** callback to pass in the page processing result.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| result | Object | Yes | Custom processing result on the page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found.<br>Value range: [-1, +∞). |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void
```

Pushes the specified navigation destination page to the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page being pushed. Default value: **DETAIL_PAGE**. |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void
```

Pushes the specified navigation destination page to the navigation stack, with stack operation settings through **NavigationOptions**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | No | Stack operation settings. Only the **animated** field is supported. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page being pushed. Default value: **DETAIL_PAGE**. |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void
```

Pushes the navigation destination page specified by **name** to the navigation stack, passing the data specified by **param**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | Detailed parameters of the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page being pushed. Default value: **DETAIL_PAGE**. |

## pushPathByName

```TypeScript
pushPathByName(
    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void
```

Pushes the navigation destination page specified by **name** to the navigation stack, passing the data specified by **param**. This API uses the **onPop** callback to handle the result returned when the page is popped out of the stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | Detailed parameters of the navigation destination page. |
| onPop | [base.Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PopInfo](../arkts-components/arkts-arkui-popinfo-i.md)&gt; | No | Callback used to handle the return result. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page being pushed. Default value: **DETAIL_PAGE**. |

## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

Removes the navigation destination pages specified by **indexes** from the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indexes | Array&lt;number&gt; | Yes | Array of indexes of the navigation destination pages to remove.<br>Value range of the number type: [0, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of the navigation destination pages removed. |

## removeByName

```TypeScript
removeByName(name: string): number
```

Removes the navigation destination page specified by **name** from the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page to be removed. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of the navigation destination pages removed. |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

Replaces the current top page on the stack with the specified navigation destination page. The new page inherits the split policy of the original top page.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

Replaces the current top page on the stack with the specified navigation destination page, with stack operation settings through **NavigationOptions**. The new page inherits the split policy of the original top page.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | No | Stack operation settings. Only the **animated** field is supported. |

## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

Replaces the current top page on the stack with the navigation destination page specified by **name**. The new page inherits the split policy of the original top page.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | Detailed parameters of the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br> **true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

## setHomeWidthRange

```TypeScript
setHomeWidthRange(minPercent: number, maxPercent: number): void
```

Sets the draggable range for the home page width. If not set, the width defaults to 50% and is not draggable.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minPercent | number | Yes | Minimum width percentage of the home page.<br>Value range: [0, 100] |
| maxPercent | number | Yes | Maximum width percentage of the home page.<br>Value range: [0, 100] |

## setPlaceholderPage

```TypeScript
setPlaceholderPage(info: NavPathInfo): void
```

Sets a placeholder page.

> **NOTE:** 

> The placeholder page is a special page type. When set, it forms a default split-screen effect with the home page
> on some large-screen devices, that is, the left side is the home page, and the right side is the placeholder
> page.

> In scenarios where the application's drawable area is less than 600 vp, or when a foldable screen switches from
> the expanded state to the folded state, or when a tablet switches from landscape to portrait mode, the
> placeholder page will be automatically removed, resulting in only the home page being shown.
> 
> Conversely, when the application's drawable area is greater than or equal to 600 vp, or when a foldable screen
> switches from the folded state to the expanded state, or when a tablet switches from portrait to landscape mode,
> the placeholder page will be automatically added to form a split-screen.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the placeholder page. |

## size

```TypeScript
size(): number
```

Obtains the stack size.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Stack size.<br>Value range: [0, +∞). |

## switchFullScreenState

```TypeScript
switchFullScreenState(isFullScreen?: boolean): boolean
```

Switches the display mode of the current top detail page in the stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFullScreen | boolean | No | Whether to enable full-screen mode. The default value is **false**. The value **true** means to enable full-screen mode, and **false** means to enable split-screen mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the switching is successful.<br>**true**: The switching is successful. <br>**false**: The switching failed. |
