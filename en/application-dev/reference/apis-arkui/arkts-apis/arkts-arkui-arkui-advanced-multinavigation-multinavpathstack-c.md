# MultiNavPathStack

```TypeScript
export declare class MultiNavPathStack extends NavPathStack
```

The route stack of **MultiNavigation** can only be created by the user and cannot be obtained through callbacks. Do not use events or APIs such as [onReady](../arkts-components/arkts-arkui-navdestination-comp-attribute.md#onready) of [NavDestination](../arkts-components/arkts-arkui-navdestination-comp.md) to obtain **NavPathStack** and perform stack operations, as this may cause unpredictable issues.

**Inheritance/Implementation:** MultiNavPathStack extends [NavPathStack](../arkts-components/arkts-arkui-navigation-comp-navpathstack-c.md)

**Since:** 14

<!--Device-unnamed-export declare class MultiNavPathStack extends NavPathStack--><!--Device-unnamed-export declare class MultiNavPathStack extends NavPathStack-End-->

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
> 
> If [keepBottomPage](#keepbottompage) is called with **true**, the bottom page of the
> navigation stack is retained.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-clear(animated?: boolean): void--><!--Device-MultiNavPathStack-clear(animated?: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

## constructor

```TypeScript
constructor()
```

Creates a **MultiNavPathStack** route stack instance.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-constructor()--><!--Device-MultiNavPathStack-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableAnimation

```TypeScript
disableAnimation(disable: boolean): void
```

Disables (**true**) or enables (**false**) all transition animations in the current **MultiNavigation**. This is suitable for scenarios where page switching performance needs to be improved or custom transition effects need to be implemented.

> **NOTE:** 
> 
> This configuration affects the animation effects of the following stack operation methods: **pushPath**,
> **pushPathByName**, **replacePath**, **replacePathByName**, **pop**, **popToName**, **popToIndex**,
> **moveToTop**, **moveIndexToTop**, and **clear**. The configuration takes effect immediately and remains
> effective throughout the lifecycle of **MultiNavigation**. It is recommended to call **disableAnimation(true)**
> to disable animations before batch stack operations to improve performance, and call **disableAnimation(false)**
> to restore animations after the operations are complete.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-disableAnimation(disable: boolean): void--><!--Device-MultiNavPathStack-disableAnimation(disable: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| disable | boolean | Yes | Whether to disable the transition animation.<br>Default value: **false**. <br>**true**:The transition animation is disabled. <br>**false**: The transition animation is not disabled. |

## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

Obtains the names of all navigation destination pages in the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-getAllPathName(): Array<string>--><!--Device-MultiNavPathStack-getAllPathName(): Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Returns the names of all **NavDestination** pages in the stack. The array elements are arranged from the bottom to the top of the stack. |

## getIndexByName

```TypeScript
getIndexByName(name: string): Array<number>
```

Obtains the indexes of all the navigation destination pages that match **name**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-getIndexByName(name: string): Array<number>--><!--Device-MultiNavPathStack-getIndexByName(name: string): Array<number>-End-->

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

<!--Device-MultiNavPathStack-getParamByIndex(index: number): Object | undefined--><!--Device-MultiNavPathStack-getParamByIndex(index: number): Object | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page.<br>Value range: [0, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| unknown &#124; undefined | **Object**: Returns the parameter information of the corresponding **NavDestination** page. The specific fields are determined by the **param** passed in **pushPath** or **pushPathByName**.<br>**undefined**: Returns **undefined** when the passed **index** is invalid. |

## getParamByName

```TypeScript
getParamByName(name: string): Array<Object>
```

Obtains the parameter information of all the navigation destination pages that match **name**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-getParamByName(name: string): Array<Object>--><!--Device-MultiNavPathStack-getParamByName(name: string): Array<Object>-End-->

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
> 
> **MultiNavigation** also pushes the home page onto the stack as a **NavDestination** page, so calling the **pop**
> or **clear** API will also pop the bottom page of the stack.
> 
> When an app calls this API and sets it to **true**, **MultiNavigation** retains the bottom page of the stack when
> the **pop** and **clear** APIs are called.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-keepBottomPage(keepBottom: boolean): void--><!--Device-MultiNavPathStack-keepBottomPage(keepBottom: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keepBottom | boolean | Yes | Whether to retain the bottom page.<br>Default value: **false**. <br>**true**: The bottom page is retained. <br>**false**: The bottom page is not retained. |

## moveIndexToTop

```TypeScript
moveIndexToTop(index: number, animated?: boolean): void
```

Moves the navigation destination page specified by **index** to the top of the navigation stack.

> **NOTE:** 
> 
> Depending on the page found at the specified index, **MultiNavigation** performs different processing:
> 
> 1) If the specified index points to the topmost home page or full-screen page, no processing is performed.
> 
> 2) If the specified index points to a detail page corresponding to the topmost home page, the corresponding
> detail page is moved to the top of the stack.
> 
> 3) If the specified index points to a non-topmost home page, the home page and all its corresponding detail pages
> are moved to the top of the stack, with the relative stack relationship of the detail pages unchanged.
> 
> 4) If the specified index points to a non-topmost detail page, the home page and all its corresponding detail
> pages are moved to the top of the stack, and the target detail page is moved to the top of all its corresponding
> detail pages.
> 
> 5) If the specified index points to a non-topmost full-screen page, the full-screen page is moved to the top of
> the stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-moveIndexToTop(index: number, animated?: boolean): void--><!--Device-MultiNavPathStack-moveIndexToTop(index: number, animated?: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the **NavDestination** page.<br>Value range: [0, +∞). The operation does not take effect if the value is out of range. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

Moves the first navigation destination page that matches **name** from the bottom of the navigation stack to the top of the stack.

> **NOTE:** 
> 
> Depending on the first page found with the specified name, **MultiNavigation** performs different processing:
> 
> 1) If the found page is the topmost home page or full-screen page, no processing is performed.
> 
> 2) If the found page is a detail page corresponding to the topmost home page, the corresponding detail page is
> moved to the top of the stack.
> 
> 3) If the found page is a non-topmost home page, the home page and all its corresponding detail pages are moved
> to the top of the stack, with the relative stack relationship of the detail pages unchanged.
> 
> 4) If the found page is a non-topmost detail page, the home page and all its corresponding detail pages are moved
> to the top of the stack, and the target detail page is moved to the top of all its corresponding detail pages.
> 
> 5) If the found page is a non-topmost full-screen page, the full-screen page is moved to the top of the stack.
> 
> **Scenario summary:** When the page is already at the top of the stack, no operation is performed. When a detail
> page is at the top of the stack, only that detail page is moved. When a non-topmost home page or detail page is
> moved, its associated detail page group is also moved. When a non-topmost full-screen page is moved, only itself
> is moved.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-moveToTop(name: string, animated?: boolean): number--><!--Device-MultiNavPathStack-moveToTop(name: string, animated?: boolean): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found. |

<a id="pop1"></a>

## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

Pops the top element out of the navigation stack.

> **NOTE:** 
> 
> If [keepBottomPage](#keepbottompage) is called with **true**, the bottom page of the
> navigation stack is retained.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-pop(animated?: boolean): NavPathInfo | undefined--><!--Device-MultiNavPathStack-pop(animated?: boolean): NavPathInfo | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navigation-comp-navpathinfo-c.md) &#124; undefined | Information about the **NavDestination** page at the top of the stack. If the stack is empty, **undefined** is returned. |

<a id="pop2"></a>

## pop

```TypeScript
pop(result?: Object, animated?: boolean): NavPathInfo | undefined
```

Pops the top element out of the navigation stack and invokes the **onPop** callback to pass the page processing result.

> **NOTE:** 
> 
> If [keepBottomPage](#keepbottompage) is called with **true**, the bottom page of the
> navigation stack is retained.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-pop(result?: Object, animated?: boolean): NavPathInfo | undefined--><!--Device-MultiNavPathStack-pop(result?: Object, animated?: boolean): NavPathInfo | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | Object | No | Custom page processing result. The specific content is defined by the developer. It is recommended to include a clear business identifier and processing result data. This result will be passed to the **onPop** callback function set when pushing to the stack. If omitted, no result data is passed. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navigation-comp-navpathinfo-c.md) &#124; undefined | Information about the **NavDestination** page at the top of the stack. If the stack is empty, **undefined** is returned. |

<a id="poptoindex1"></a>

## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

Pops the route stack back to the **NavDestination** page specified by **index**. If **index** is invalid (out of range), no pop operation is performed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-popToIndex(index: number, animated?: boolean): void--><!--Device-MultiNavPathStack-popToIndex(index: number, animated?: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the **NavDestination** page.<br>Value range: [0, +∞). The operation does not take effect when the value is out of range. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

<a id="poptoindex2"></a>

## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

Pops the route stack back to the **NavDestination** page specified by **index**, and triggers the **onPop** callback to return the page processing result. If **index** is invalid (out of range), no pop operation is performed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-popToIndex(index: number, result: Object, animated?: boolean): void--><!--Device-MultiNavPathStack-popToIndex(index: number, result: Object, animated?: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page.<br>Value range: [0, +∞). |
| result | Object | Yes | Custom page processing result. The specific content is defined by the developer. It is recommended to include an explicit business identifier and processing result data. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

<a id="poptoname1"></a>

## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

Pops pages until the first navigation destination page that matches **name** from the bottom of the navigation stack is at the top of the stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-popToName(name: string, animated?: boolean): number--><!--Device-MultiNavPathStack-popToName(name: string, animated?: boolean): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found.<br>Value range: [-1, +∞). |

<a id="poptoname2"></a>

## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

Pops pages until the first navigation destination page that matches **name** from the bottom of the navigation stack is at the top of the stack. This API uses the **onPop** callback to pass in the page processing result.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-popToName(name: string, result: Object, animated?: boolean): number--><!--Device-MultiNavPathStack-popToName(name: string, result: Object, animated?: boolean): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| result | Object | Yes | Custom page processing result. The specific content is defined by the developer. It is recommended to include a clear business identifier and processing result data. This result will be passed to the **onPop** callback function set when the page is pushed onto the stack. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found.<br>Value range: [-1, +∞). |

<a id="pushpath1"></a>

## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void
```

Pushes the specified navigation destination page to the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page pushed to the stack.<br>Default value: **DETAIL_PAGE** |

<a id="pushpath2"></a>

## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void
```

Pushes the specified navigation destination page to the navigation stack, with stack operation settings through **NavigationOptions**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigation-comp-navigationoptions-i.md) | No | Page stack operation options. Only the **animated** field is supported; other fields are ignored. The default animation configuration is used when this parameter is omitted. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page pushed to the stack.<br>Default value: **DETAIL_PAGE** |

<a id="pushpathbyname1"></a>

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void
```

Pushes the navigation destination page specified by **name** to the navigation stack, passing the data specified by **param**.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | **NavDestination** page name, which must be consistent with the page name registered in **NavDestinationBuildFunction**. |
| param | Object | Yes | Detailed parameters of the **NavDestination** page, used to pass custom data to the target page. For details about the field specifications, see the **NavDestination** documentation. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page pushed to the stack.<br>Default value: **DETAIL_PAGE** |

<a id="pushpathbyname2"></a>

## pushPathByName

```TypeScript
pushPathByName(
    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void
```

Pushes the navigation destination page specified by **name** to the navigation stack, passing the data specified by **param**. This API uses the **onPop** callback to handle the result returned when the page is popped out of the stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-pushPathByName(    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPathByName(    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the **NavDestination** page. It must be consistent with the page name registered in **NavDestinationBuildFunction**. |
| param | Object | Yes | Detailed parameters of the **NavDestination** page, used to pass custom data to the target page. For details about the field specifications, see the **NavDestination** documentation. |
| onPop | [base.Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PopInfo](../arkts-components/arkts-arkui-navigation-comp-popinfo-i.md)&gt; | No | Callback invoked when the page is popped from the stack to process the return result. If this parameter is omitted, the callback is not triggered. Data can be passed to this callback through the result parameter of the **pop**, **popToName**, and **popToIndex** methods. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | No | Policy for the current page pushed to the stack.<br>Default value: **DETAIL_PAGE** |

## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

Removes the navigation destination pages specified by **indexes** from the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-removeByIndexes(indexes: Array<number>): number--><!--Device-MultiNavPathStack-removeByIndexes(indexes: Array<number>): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indexes | Array&lt;number&gt; | Yes | Array of index values of the **NavDestination** pages to be deleted.<br>Value range of the number type: [0, +∞). The operation does not take effect if the value is out of range. |

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

<!--Device-MultiNavPathStack-removeByName(name: string): number--><!--Device-MultiNavPathStack-removeByName(name: string): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the **NavDestination** page to be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of the navigation destination pages removed. |

<a id="replacepath1"></a>

## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

Replaces the current top page on the stack with the specified navigation destination page. The new page inherits the split policy of the original top page.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void--><!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

<a id="replacepath2"></a>

## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

Replaces the current top page on the stack with the specified navigation destination page, with stack operation settings through **NavigationOptions**. The new page inherits the split policy of the original top page.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void--><!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigation-comp-navigationoptions-i.md) | No | Page stack operation options. Only the **animated** field is supported. Other fields are ignored. If this parameter is omitted, the default animation configuration is used. |

## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

Replaces the current top page on the stack with the navigation destination page specified by **name**. The new page inherits the split policy of the original top page.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void--><!--Device-MultiNavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | **NavDestination** page detailed parameters, used to pass custom data to the target page. For specific field specifications, see the **NavDestination** documentation. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

## setHomeWidthRange

```TypeScript
setHomeWidthRange(minPercent: number, maxPercent: number): void
```

Sets the draggable range for the home page width. If not set, the width defaults to 50% and is not draggable.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-setHomeWidthRange(minPercent: number, maxPercent: number): void--><!--Device-MultiNavPathStack-setHomeWidthRange(minPercent: number, maxPercent: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minPercent | number | Yes | Minimum main page width percentage.<br>Value range: [0, 100], and must be less than or equal to **maxPercent**. |
| maxPercent | number | Yes | Maximum main page width percentage.<br>Value range: [0, 100], and must be greater than or equal to **minPercent**. |

## setPlaceholderPage

```TypeScript
setPlaceholderPage(info: NavPathInfo): void
```

Sets a placeholder page.

> **NOTE:** 
> 
> The placeholder page is a special page type. After being set by the app, it forms a left-right multi-column
> layout with the home page by default on large-screen devices that support multi-column display, that is, the home
> page on the left and the placeholder page on the right.
> 
> When the app drawable area is less than 600 vp, a foldable switches from the expanded state to the folded state,
> or a tablet switches from landscape to portrait orientation, the placeholder page is automatically popped from
> the stack, and only the home page is displayed.
> 
> When the app drawable area is greater than or equal to 600 vp, a foldable switches from the folded state to the
> expanded state, or a tablet switches from portrait to landscape orientation, the placeholder page is
> automatically added to form a multi-column layout.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-setPlaceholderPage(info: NavPathInfo): void--><!--Device-MultiNavPathStack-setPlaceholderPage(info: NavPathInfo): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Page information of the placeholder page, used to set the placeholder page. On a large-screen device, the placeholder page and the main page form a left-right column layout. |

## size

```TypeScript
size(): number
```

Obtains the stack size.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-size(): number--><!--Device-MultiNavPathStack-size(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Stack size.<br>Value range: [0, +∞). |

## switchFullScreenState

```TypeScript
switchFullScreenState(isFullScreen?: boolean): boolean
```

Switches the display mode of the detail page at the top of the current stack. This is suitable for scenarios such as video playback and image browsing that require full-screen display.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavPathStack-switchFullScreenState(isFullScreen?: boolean): boolean--><!--Device-MultiNavPathStack-switchFullScreenState(isFullScreen?: boolean): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFullScreen | boolean | No | Whether to switch to full-screen mode.<br>Default value: false<br>**true**: full-screen mode; **false**: split-screen mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the switching is successful.<br>**true**: The switching is successful. <br>**false**: The switching failed. |
