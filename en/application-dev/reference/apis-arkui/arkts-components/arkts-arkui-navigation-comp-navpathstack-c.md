# NavPathStack

```TypeScript
declare class NavPathStack
```

A navigation controller that manages all child pages in the **Navigation** component with a stack data structure and provides stack operation methods for controlling page transitions.

Starting from API version 12, **NavPathStack** is inheritable. Objects of a derived class can replace those of the base class. For details, see [Example 10](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-10-defining-a-derived-class-of-navpathstack).

> **NOTE:** 
> 
> 1. When multiple navigation controller operations are triggered in succession, the intermediate states are bypassed, and only the final result of the operations is rendered.

> For example, if a Page1 is popped and then immediately pushed back, the system considers that the states before and after these operations are identical, leading to no actual change in the stack. To ensure that a new instance of Page1 is pushed onto the stack despite the consecutive operations, use the **NEW_INSTANCE** mode.
> 
> 2. Avoid relying on lifecycle event listeners as a means to manage the navigation controller.
> 
> 3. When the application is in the background, calling stack operation APIs of **NavPathStack** will trigger a refresh upon the application's return to the foreground.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clear

```TypeScript
clear(animated?: boolean): void
```

Clears the routing stack.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true**<br>**Since:** 11 |

## constructor

```TypeScript
constructor()
```

Creates a **NavPathStack** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableAnimation

```TypeScript
disableAnimation(value: boolean): void
```

Disables or enables the transition animation in the **Navigation** component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to disable the transition animation.<br>Default value: **false**<br>**true**: Disable the transition animation.<br>**false**: Enable the transition animation. |

## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

Obtains the names of all navigation destination pages in the routing stack.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Names of all navigation destination pages in the routing stack. |

## getIndexByName

```TypeScript
getIndexByName(name: string): Array<number>
```

Obtains the indexes of all the navigation destination pages that match **name**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Indexes of all the matching navigation destination pages. If no pages with the specified name exist in the routing stack, an empty array is returned. The index range is [0, routing stack size - 1]. |

## getParamByIndex

```TypeScript
getParamByIndex(index: number): unknown | undefined
```

Obtains the parameter information of the navigation destination page specified by **index**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page. The index is zero-based. |

**Return value:**

| Type | Description |
| --- | --- |
| unknown &#124; undefined | **unknown**: parameter information of the corresponding navigation destination page. **unknown** can represent a user-defined type.<br>**undefined**: an invalid index is provided. |

## getParamByName

```TypeScript
getParamByName(name: string): Array<unknown>
```

Obtains the parameter information of all **NavDestination** pages with the specified name, and sorts the information in ascending order by page index.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;unknown&gt; | Parameter information of all **NavDestination** pages with the specified name. **unknown** can represent a user-defined type. |

## getParent

```TypeScript
getParent(): NavPathStack | null
```

Obtains the parent navigation path stack.

When a **Navigation** component is nested (directly or indirectly) inside another **Navigation** component, the **NavPathStack** of the inner component can obtain the **NavPathStack** of the outer component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [NavPathStack](arkts-arkui-navigation-comp-navpathstack-c.md) &#124; null | Navigation path stack of the outer **Navigation** component in which the current **Navigation** component is nested. If there is no outer **Navigation** component., **null** is returned. |

## getPathStack

```TypeScript
getPathStack(): Array<NavPathInfo>
```

Obtains the array of route page information from this routing stack.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md)&gt; | Array of route page information in the current routing stack. |

## moveIndexToTop

```TypeScript
moveIndexToTop(index: number, animated?: boolean): void
```

Moves to the top of the routing stack the navigation destination page specified by **index**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page. The index is zero-based. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true**<br>**Since:** 11 |

## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

Moves the first navigation destination page that matches **name** from the bottom of the routing stack to the top of the stack.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true**<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the routing stack; returns **-1** if such a page does not exist. |

## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

Pops the top element out of the routing stack.

> **NOTE:** 
> 
> When multiple navigation controller methods are called consecutively, any pages popped during the sequence are
> cached. If a page with the same name is later pushed, the system reuses the cached instance instead of
> instantiating a new page.

> Example:

> pathStack: NavPathStack = new NavPathStack()

> //The initial page stack is [A].

> pathStack.pop()

> pathStack.pushPath(A)

> pathStack.pushPath(B)

> // The page stack after the operation is [A B].

> In this case, page A is reused, and the new creation process is not performed.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true**<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) &#124; undefined | **NavPathInfo**: information about the navigation destination page at the top of the stack.<br>**undefined**: the routing stack is empty. |

<a id="pop-1"></a>

## pop

```TypeScript
pop(result: Object, animated?: boolean): NavPathInfo | undefined
```

Pops the top element out of the routing stack and invokes the **onPop** callback to pass the page processing result.

> **NOTE:** 
> 
> When multiple navigation controller methods are called consecutively, any pages popped during the sequence are
> cached. If a page with the same name is later pushed, the system reuses the cached instance instead of
> instantiating a new page.

> Example:

> pathStack: NavPathStack = new NavPathStack()

> //The initial page stack is [A].

> pathStack.pop()

> pathStack.pushPath(A)

> pathStack.pushPath(B)

> // The page stack after the operation is [A B].

> In this case, page A is reused, and the new creation process is not performed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | Object | Yes | Custom processing result on the page. The boolean type is not supported. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) &#124; undefined | **NavPathInfo**: information about the navigation destination page at the top of the stack.<br>**undefined**: the routing stack is empty. |

## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

Returns the routing stack to the page specified by **index**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page. The index is zero-based. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true**<br>**Since:** 11 |

<a id="poptoindex-1"></a>

## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

Returns the routing stack to the page specified by **index** and invokes the **onPop** callback to pass the page processing result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the navigation destination page. The index is zero-based. |
| result | Object | Yes | Custom processing result on the page. The boolean type is not supported. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

Pops pages until the first navigation destination page that matches **name** from the bottom of the routing stack is at the top of the stack.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true**<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the routing stack; returns **-1** if such a page does not exist. |

<a id="poptoname-1"></a>

## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

Pops pages until the first navigation destination page that matches **name** from the bottom of the routing stack is at the top of the stack. This API uses the **onPop** callback to pass in the page processing result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| result | Object | Yes | Custom processing result on the page. The boolean type is not supported. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the routing stack; returns **-1** if such a page does not exist. |

## preloadPath

```TypeScript
preloadPath(info: NavPathInfo, options?: PreloadOptions): Promise<void>
```

Preloads navigation destination page specified by **info**. The preload page will not be displayed immediately, but will be cached. When **pushPath** is called later with matching parameters, preloaded instance will be used for fast display.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Indicates NavDestination to be preloaded. |
| options | [PreloadOptions](arkts-arkui-navigation-comp-preloadoptions-i.md) | No | Indicates options for preloading. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |

## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>
```

Pushes the navigation destination page specified by **info** onto the routing stack. This API uses a promise to return the result.

> **NOTE:** 
> 
> You are not advised to use stack operations in [aboutToAppear](arkts-arkui-common-comp-basecustomcomponent-c.md#abouttoappear), as the
> page has not yet finished building at this stage, which may lead to issues such as white screens or navigation
> failures.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |

<a id="pushdestination-1"></a>

## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

Pushes the navigation destination page specified by **info** onto the routing stack. This API uses a promise to return the result. Depending on the [LaunchMode](arkts-arkui-navigation-comp-launchmode-e.md) specified in the **options** parameter, different behaviors will be implemented.

> **NOTE:** 
> 
> You are not advised to use stack operations in [aboutToAppear](arkts-arkui-common-comp-basecustomcomponent-c.md#abouttoappear), as the
> page has not yet finished building at this stage, which may lead to issues such as white screens or navigation
> failures.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| options | [NavigationOptions](arkts-arkui-navigation-comp-navigationoptions-i.md) | No | Routing stack operation options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |

## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>
```

Pushes the navigation destination page specified by **name**, with the data specified by **param**, to the routing stack. This API uses a promise to return the result.

> **NOTE:** 
> 
> You are not advised to use stack operations in [aboutToAppear](arkts-arkui-common-comp-basecustomcomponent-c.md#abouttoappear), as the
> page has not yet finished building at this stage, which may lead to issues such as white screens or navigation
> failures.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | Detailed parameters for the custom **NavDestination** page. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |

<a id="pushdestinationbyname-1"></a>

## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): Promise<void>
```

Pushes the navigation destination page specified by **name**, with the data specified by **param**, to the routing stack. This API uses the **onPop** callback to handle the result returned when the page is popped out of the stack. It uses a promise to return the result.

> **NOTE:** 
> 
> You are not advised to use stack operations in [aboutToAppear](arkts-arkui-common-comp-basecustomcomponent-c.md#abouttoappear), as the
> page has not yet finished building at this stage, which may lead to issues such as white screens or navigation
> failures.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | Detailed parameters for the custom **NavDestination** page. |
| onPop | import('../api/@ohos.base').Callback&lt;[PopInfo](arkts-arkui-navigation-comp-popinfo-i.md)&gt; | Yes | Callback used to handle the result returned when the page is popped out of the stack. It is triggered only when the **result** parameter is set in [pop](#pop-1), [popToName](#poptoname-1), or [popToIndex](#poptoindex-1). |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean): void
```

Pushes the navigation destination page specified by **info** onto the routing stack.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br>If the input parameter is invalid, the value **true** is used.<br>**Since:** 11 |

<a id="pushpath-1"></a>

## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions): void
```

Pushes the navigation destination page specified by **info** onto the routing stack. Depending on the [LaunchMode](arkts-arkui-navigation-comp-launchmode-e.md) specified in the **options** parameter, different behaviors will be implemented.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| options | [NavigationOptions](arkts-arkui-navigation-comp-navigationoptions-i.md) | No | Routing stack operation options. |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: unknown, animated?: boolean): void
```

Pushes the navigation destination page specified by **name**, with the data specified by **param**, to the routing stack.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | unknown | Yes | Detailed parameters for the custom **NavDestination** page. The **unknown** type can be replaced with a user-defined type. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true**<br>**Since:** 11 |

<a id="pushpathbyname-1"></a>

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): void
```

Pushes the navigation destination page specified by **name**, with the data specified by **param**, to the routing stack. This API uses the **onPop** callback to receive the result returned when the page is popped out of the stack.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | Detailed parameters for the custom **NavDestination** page. |
| onPop | import('../api/@ohos.base').Callback&lt;[PopInfo](arkts-arkui-navigation-comp-popinfo-i.md)&gt; | Yes | Callback used to receive the result. It is triggered only when the **result** parameter is set in [pop](#pop-1), [popToName](#poptoname-1), or [popToIndex](#poptoindex-1). |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

Removes the navigation destination pages specified by **indexes** from the routing stack.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indexes | Array&lt;number&gt; | Yes | Array of indexes of the navigation destination pages to remove. The index is zero-based. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of the navigation destination pages removed. |

## removeByName

```TypeScript
removeByName(name: string): number
```

Removes the navigation destination page specified by **name** from the routing stack.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of the navigation destination pages removed. |

## removeByNavDestinationId

```TypeScript
removeByNavDestinationId(navDestinationId: string): boolean
```

Removes the navigation destination page specified by **navDestinationId** from the routing stack. **navDestinationId** can be obtained from the [onReady](arkts-arkui-navdestination-comp-attribute.md#onready) callback of **NavDestination** or from [NavDestinationInfo](../arkts-apis/arkts-arkui-uiobserver-navdestinationinfo-i.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| navDestinationId | string | Yes | Unique ID of the navigation destination page to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the page is removed successfully.<br>**true**: Removal succeeded. <br>**false**: Removal failed. |

## replaceDestination

```TypeScript
replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

Performs a replacement operation on the routing stack. This API uses a promise to return the result. Its behavior varies depending on the value of [LaunchMode](arkts-arkui-navigation-comp-launchmode-e.md) specified in **options**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Information about the navigation destination page. |
| options | [NavigationOptions](arkts-arkui-navigation-comp-navigationoptions-i.md) | No | Routing stack operation options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

Replaces the top of the routing stack with the navigation destination page specified by **info**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Parameters for the new top page of the routing stack. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

<a id="replacepath-1"></a>

## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

Replaces the top page on the routing stack. Depending on the [LaunchMode](arkts-arkui-navigation-comp-launchmode-e.md) specified in the **options** parameter, different behaviors will be implemented.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) | Yes | Parameters for the new top page of the routing stack. |
| options | [NavigationOptions](arkts-arkui-navigation-comp-navigationoptions-i.md) | No | Routing stack operation options. |

## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

Replaces the top of the routing stack with the page specified by **name**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. |
| param | Object | Yes | Detailed parameters for the custom **NavDestination** page. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

## setInterception

```TypeScript
setInterception(interception: NavigationInterception): void
```

Sets the interception callback for navigation page redirection.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| interception | [NavigationInterception](arkts-arkui-navigation-comp-navigationinterception-i.md) | Yes | Object to be intercepted during navigation redirection. |

## setPathStack

```TypeScript
setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void
```

Updates the array of route page information in this routing stack to the specified content and performs route transitions.

> **NOTE:** 
> 
> 1. You can add or remove pages in batches based on the existing stack. Among the pages added in batches, only the visible pages will trigger creation; other pages, although added to the stack, will not be created immediately.They will only be created when they become visible.
> 
> 2. For routing stacks updated through the batch push functionality, the lifecycle events of each page are triggered from the top to the bottom of the stack. This differs from the triggering order of other push APIs,which are triggered from the bottom to the top of the stack.
> 
> 3. You can operate existing pages using **navDestinationId** (unique ID) in [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md).This ID is system-generated and globally unique (it can be obtained using the [getPathStack](#getpathstack) API and should not be manually reassigned). If the specified ID does not exist in the current routing stack, it indicates a new page. If it exists and the corresponding name is the same, it indicates reuse of an existing page.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pathStack | Array&lt;[NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md)&gt; | Yes | Array of route page information in the current routing stack.<br>**NOTE:** <br>The array length is not limited. |
| animated | boolean | No | Whether to enable the transition animation.<br>**true**: yes; **false**: no<br> Default value: **true** |

## size

```TypeScript
size(): number
```

Obtains the stack size.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Stack size.<br>Value range: [0, +��) |
