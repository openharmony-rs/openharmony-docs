# TabsController

```TypeScript
declare class TabsController
```

Defines a tab controller, which is used to control switching of tabs. One **TabsController** cannot control multiple **Tabs** components.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(value: number): void
```

Switches to the specified tab.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Index of the tab. The value starts from 0.<br>**NOTE:** <br>If this parameter is set to a value less than 0 or greater than the maximum number, the default value **0** is used. |

## constructor

```TypeScript
constructor()
```

A constructor used to create a **TabsController** object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getBarDisplayMode

```TypeScript
getBarDisplayMode(): TabBarDisplayMode
```

Get the current display mode of the Tabs.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TabBarDisplayMode](arkts-arkui-tabs-comp-tabbardisplaymode-e.md) | The current display mode. |

## preloadItems

```TypeScript
preloadItems(indices: Optional<Array<number>>): Promise<void>
```

Preloads child nodes. After this API is called, all specified child nodes will be loaded at once. Therefore, for performance considerations, it is recommended that you load child nodes in batches.

> **NOTE:** 
> 
> - **preloadItems** of **Tabs** needs to be called after **Tabs** is created. You are advised to control the first preloading in the [onAppear](arkts-arkui-common-comp-commonmethod-c.md#onappear) lifecycle of **Tabs**.
> 
> - If the **TabsController** object is not bound to any **Tabs** component, a JavaScript exception will be thrown when this API is called. Therefore, you are advised to use **try-catch** to handle potential exceptions when calling this API.
> 
> - When using **preloadItems** to preload tabs, you are advised to use **ComponentContent** to customize the content displayed on the tab bar. For details, see [Example 10](../../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md#example-10-setting-tabbar-using-componentcontent).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indices | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Array&lt;number&gt;&gt; | Yes | Array of indexes of the child nodes to preload.<br>The default value is an empty array. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter invalid. Possible causes:<br> 1. The parameter type is not Array&lt;number&gt;. <br> 2. The parameter is an empty array. <br> 3. The parameter contains an invalid index. |

## setTabBarOpacity

```TypeScript
setTabBarOpacity(opacity: number): void
```

Sets the opacity of the tab bar.

> **NOTE:** 
> 
> When a **Tabs** component is bound to a scrollable container using APIs like
> [bindTabsToScrollable](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstoscrollable13)
> or bindTabsToNestedScrollable](../arkts-apis-uicontext-uicontext.md#bindtabstonestedscrollable13), scrolling the
> container will trigger the display and hide animations of the tab bar for all **Tabs** components bound to it. In
> this case, any **TabBar** opacity set via the **setTabBarOpacity** API will be overridden. Therefore, avoid using
> **bindTabsToScrollable**, **bindTabsToNestedScrollable**, and **setTabBarOpacity** simultaneously.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opacity | number | Yes | Opacity of the tab bar. The value range is [0.0, 1.0]. A value less than 0.0 is handed as **0.0**. A value greater than **1.0** is handed as **1.0**.<br> Default value: **1.0**. |

## setTabBarTranslate

```TypeScript
setTabBarTranslate(translate: TranslateOptions): void
```

Sets the translation distance of the tab bar.

> **NOTE:** 
> 
> When a **Tabs** component is bound to a scrollable container using APIs like
> [bindTabsToScrollable](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstoscrollable13)
> or bindTabsToNestedScrollable](../arkts-apis-uicontext-uicontext.md#bindtabstonestedscrollable13), scrolling the
> container will trigger the display and hide animations of the tab bar for all **Tabs** components bound to it. In
> this case, calling the **setTabBarTranslate** API has no effect. Therefore, avoid using **bindTabsToScrollable**,
> **bindTabsToNestedScrollable**, and **setTabBarTranslate** simultaneously.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| translate | [TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md) | Yes | Translation distance of the tab bar. |
