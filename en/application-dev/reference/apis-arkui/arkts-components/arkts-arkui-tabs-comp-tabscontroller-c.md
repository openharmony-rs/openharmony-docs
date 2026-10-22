# TabsController

```TypeScript
declare class TabsController
```

Defines the controller of the **Tabs** component, used to control the **Tabs** component to perform tab switching. A single **TabsController** cannot control multiple **Tabs** components.

**Since:** 7

<!--Device-unnamed-declare class TabsController--><!--Device-unnamed-declare class TabsController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(value: number): void
```

Controls **Tabs** to switch to a specified tab. Use this API when you need to implement tab switching through buttons, drop-down menus, or other controls, for example, tapping the "Previous"/"Next" button to switch tabs.

> **NOTE:** 
> 
> When **animationMode** is set to [AnimationMode.NO_ANIMATION](arkts-arkui-tabs-comp-attribute.md#animationmode), the default
> animation does not take effect when this API is called to switch **TabContent**. You can set
> [animationDuration](arkts-arkui-tabs-comp-attribute.md#animationduration) to **0** to switch without animation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsController-changeIndex(value: number): void--><!--Device-TabsController-changeIndex(value: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Index of the tab, starting from 0. Value range: [0, total number of tabs - 1]. If the value is out of range, it is processed as 0. |

## constructor

```TypeScript
constructor()
```

Constructor of **TabsController**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsController-constructor()--><!--Device-TabsController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getBarDisplayMode

```TypeScript
getBarDisplayMode(): TabBarDisplayMode
```

Get the current display mode of the Tabs.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-TabsController-getBarDisplayMode(): TabBarDisplayMode--><!--Device-TabsController-getBarDisplayMode(): TabBarDisplayMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TabBarDisplayMode](arkts-arkui-tabs-comp-tabbardisplaymode-e.md) | The current display mode. |

## preloadItems

```TypeScript
preloadItems(indices: Optional<Array<number>>): Promise<void>
```

Controls the preloading of specified child nodes in **Tabs**. After this API is called, all specified child nodes are loaded at once. Therefore, for performance considerations, it is recommended to load child nodes in batches. This API is applicable to scenarios where certain tabs need to be loaded in advance to improve switching performance, for example, when the content of some tabs is complex or resource-intensive, preloading can be used to optimize user experience.

> **NOTE:** 
> 
> - The **preloadItems** API of **Tabs** must be called after **Tabs** is created. For the first preloading, it is recommended to control it in the [onAppear](arkts-arkui-common-comp-commonmethod-c.md#onappear) lifecycle of **Tabs**.
> 
> - If the **TabsController** object is not bound to any **Tabs** component, calling this API directly throws a JS exception. Therefore, when using this API, it is recommended to catch the exception through try-catch.
> 
> - When using **preloadItems** to preload tab pages, if you need to customize the content displayed on the tab bar, it is recommended to use **ComponentContent**. For a usage example, see [Example 10](../../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md#example-10-preloading-child-nodes-using-componentcontent).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsController-preloadItems(indices: Optional<Array<number>>): Promise<void>--><!--Device-TabsController-preloadItems(indices: Optional<Array<number>>): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indices | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Array&lt;number&gt;&gt; | Yes | Array of indices of the child nodes to be preloaded.<br>Default value: empty array. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter invalid. Possible causes: <br> 1. The parameter type is not Array<number>. <br> 2. The parameter is an empty array. <br> 3. The parameter contains an invalid index. |

## setTabBarOpacity

```TypeScript
setTabBarOpacity(opacity: number): void
```

Sets the opacity of the tab bar. This API is suitable for scenarios where the tab bar display transparency needs to be adjusted, such as the fade-in and fade-out effect of the tab bar and reducing the visual interference of the tab bar to highlight content.

> **NOTE:** 
> 
> After the **Tabs** component is bound to a scrollable container component using APIs such as
> [bindTabsToScrollable](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#bindtabstoscrollable) or
> [bindTabsToNestedScrollable](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#bindtabstonestedscrollable),
> when the scrollable container component is swiped, the show and hide animations of the tab bar of all **Tabs**
> components bound to it are triggered, and the tab bar opacity set by calling **setTabBarOpacity** becomes
> invalid. Therefore, it is not recommended to use **bindTabsToScrollable**, **bindTabsToNestedScrollable**, and
> **setTabBarOpacity** at the same time.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-TabsController-setTabBarOpacity(opacity: number): void--><!--Device-TabsController-setTabBarOpacity(opacity: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opacity | number | Yes | Opacity of the tab bar. The value **1.0** indicates fully opaque, and the value 0.0 indicates fully transparent. The value range is [0.0, 1.0]. If the set value is less than 0.0, it is processed as 0.0. If the set value is greater than 1.0, it is processed as 1.0. <br> Default value: **1.0**. |

## setTabBarTranslate

```TypeScript
setTabBarTranslate(translate: TranslateOptions): void
```

Sets the translation distance of the tab bar. This API is applicable to scenarios where the tab bar position needs to be adjusted dynamically, such as the slide-to-hide/show effect of the tab bar and immersive experience achieved by scrolling the page together with the tab bar.

> **NOTE:** 
> 
> After the **Tabs** component is bound to a scrollable container component through APIs such as
> bindTabsToScrollable or
> bindTabsToNestedScrollable,
> scrolling the scrollable container component triggers the show/hide animation of the tab bar of all **Tabs**
> components bound to it. In this case, the tab bar translation distance set by calling **setTabBarTranslate**
> becomes invalid. Therefore, it is not recommended to use **bindTabsToScrollable**,
> **bindTabsToNestedScrollable**, and **setTabBarTranslate** at the same time.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-TabsController-setTabBarTranslate(translate: TranslateOptions): void--><!--Device-TabsController-setTabBarTranslate(translate: TranslateOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| translate | [TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md) | Yes | Translation distance of the tab bar. |
