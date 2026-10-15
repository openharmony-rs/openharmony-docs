# BaseCustomComponent

```TypeScript
declare class BaseCustomComponent extends CommonAttribute
```

Custom Component base class and it is migrated from class CustomComponent.

**Inheritance/Implementation:** BaseCustomComponent extends [CommonAttribute](arkts-arkui-common-comp-attribute.md#commonattribute)

**Since:** 18

<!--Device-unnamed-declare class BaseCustomComponent extends CommonAttribute--><!--Device-unnamed-declare class BaseCustomComponent extends CommonAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

Invoked after a new instance of the custom component is created and before its **build()** function is executed. You can change [state variables](../../../ui/state-management/arkts-state-management-glossary.md#state-variable) in the **aboutToAppear** function, and the changes will take effect in the subsequent execution of the **build()** function. The **aboutToAppear** lifecycle of a custom component that implements [custom layout](#onmeasuresize) is triggered during the layout process. For details about how to use it, see [Custom Component Lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md).

> **NOTE:** 
> 
> * In this callback function, it is recommended that you only perform initialization logic for the current node component. Avoid high-time-consuming operations that may block the main thread. For high-time-consuming operations, consider caching or asynchronous solutions. For best practices, see [Optimizing Performance of UI Components: Avoiding Time-Consuming Operations During the Lifecycle of Custom Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-ui-component-performance-optimization#section18755173594714).
> 
> * In scenarios where components need to be frequently created and destroyed, this callback will be called frequently. For best practices, see [Optimizing Time-Consuming Operations in the Main Thread: Component Lifecycle Callback](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread#section418843713435).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseCustomComponent-aboutToAppear?(): void--><!--Device-BaseCustomComponent-aboutToAppear?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

Executed when the custom component is destructed and destroyed. Do not change state variables in the **aboutToDisappear** function. In particular, modifying the \@Link variable may cause unstable app behavior. For details about how to use it, see [Custom Component Lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md). It is not recommended to trigger logic such as [creating a custom dialog box](../arkts-apis/arkts-arkui-customdialogcontroller-c.md#open) after the **aboutToDisappear** function is called, because this may cause abnormal app behavior due to the loss of component tree information, for example, [\@Consume](../../../ui/state-management/arkts-provide-and-consume.md) cannot find the corresponding [\@Provide](../../../ui/state-management/arkts-provide-and-consume.md), or the dialog box displays a blank screen without components.

> **NOTE:** 
> 
> In scenarios where components need to be frequently created and destroyed, this callback will be called
> frequently. For best practices, see
> [Optimizing Time-Consuming Operations in the Main Thread: Component Lifecycle Callback](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread#section418843713435).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseCustomComponent-aboutToDisappear?(): void--><!--Device-BaseCustomComponent-aboutToDisappear?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToRecycle

```TypeScript
aboutToRecycle?(): void
```

Invoked before a reusable component is added to the reuse cache from the node tree. When the component is subsequently reused from the reuse cache, the [aboutToReuse](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#abouttoreuse10) lifecycle callback is triggered. In frequently invoked scenarios, avoid performing time-consuming operations in it, otherwise frame loss and lag may occur.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseCustomComponent-aboutToRecycle?(): void--><!--Device-BaseCustomComponent-aboutToRecycle?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

The **build()** function is used to define the declarative UI description of a custom component. Every custom component must define a **build()** function.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseCustomComponent-build(): void--><!--Device-BaseCustomComponent-build(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getDialogController

```TypeScript
getDialogController(): PromptActionDialogController | undefined
```

The dialog controller of the custom component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-BaseCustomComponent-getDialogController(): PromptActionDialogController | undefined--><!--Device-BaseCustomComponent-getDialogController(): PromptActionDialogController | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PromptActionDialogController](arkts-arkui-common-comp-promptactiondialogcontroller-t.md) &#124; undefined | The controller of dialog, or undefined if it is not available |

## getUIContext

```TypeScript
getUIContext(): UIContext
```

Get current UIContext and it is migrated from class CustomComponent.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseCustomComponent-getUIContext(): UIContext--><!--Device-BaseCustomComponent-getUIContext(): UIContext-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-common-comp-uicontext-t.md) | The UIContext that the custom component belongs to. |

## getUniqueId

```TypeScript
getUniqueId(): number
```

Get uniqueId of the custom component and it is migrated from class CustomComponent.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseCustomComponent-getUniqueId(): number--><!--Device-BaseCustomComponent-getUniqueId(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | The uniqueId of the custom component. |

## onBackPress

```TypeScript
onBackPress?(): void | boolean
```

Takes effect on a router-managed page (a custom component decorated with [\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry)) and is triggered when the user clicks the back button. The value **true** indicates that the page handles the back logic by itself and does not perform page routing; the value **false** indicates that the default routing back logic is used. If no return value is set, it is processed as **false**. Typical use cases include: blocking the back action to prompt the user to save when the page has unsaved edits, and popping up a custom confirmation dialog box to replace the default system back behavior.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseCustomComponent-onBackPress?(): void | boolean--><!--Device-BaseCustomComponent-onBackPress?(): void | boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidBuild

```TypeScript
onDidBuild?(): void
```

Invoked after the **build()** function of the custom component is executed. You can use this callback for actions that do not directly affect the UI, such as tracking data reporting. For details, see [Custom Component Lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseCustomComponent-onDidBuild?(): void--><!--Device-BaseCustomComponent-onDidBuild?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFormRecover

```TypeScript
onFormRecover?(statusData: string): void
```

Invoked when the widget is recovered. The widget provider can obtain the data saved by the widget manager during widget recycling. This data can be saved to the widget manager using the [onFormRecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#onformrecycle11) callback.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-BaseCustomComponent-onFormRecover?(statusData: string): void--><!--Device-BaseCustomComponent-onFormRecover?(statusData: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| statusData | string | Yes | Data saved by the widget manager during widget recycling. |

## onFormRecycle

```TypeScript
onFormRecycle?(): string
```

Invoked when the widget is recycled. The widget provider can return the data to be saved by the widget manager. This data is passed back to the widget provider using the [onFormRecover](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#onformrecover11) API when the widget is recovered.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-BaseCustomComponent-onFormRecycle?(): string--><!--Device-BaseCustomComponent-onFormRecycle?(): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Data that the widget provider requests the widget manager to save. |

## onMeasureSize

```TypeScript
onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult
```

Invoked when the custom component needs to determine its size. Through this callback the component receives its layout information and size constraints from the ArkUI framework. State variables should not be changed in this callback.

> **NOTE:** 
> 
> - When a custom layout is created in builder mode, only **this.builder()** is allowed in the **build()** method of a custom component, as shown in the recommended usage in the example below.
> - The size parameters of the parent component (custom component), except **aspectRatio**, are at a lower priority than those specified by [onMeasureSize](#onmeasuresize).
> - The position parameters of the child component, except **offset**, **position**, and **markAnchor**, are at a lower priority than those specified by [onPlaceChildren](#onplacechildren),and do not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseCustomComponent-onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult--><!--Device-BaseCustomComponent-onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selfLayoutInfo | [GeometryInfo](arkts-arkui-common-comp-geometryinfo-i.md) | Yes | Information about the component's computed layout properties after measurement.<br>During the first layout, the component will use its own set attributes as the basis for layout. |
| children | Array&lt;[Measurable](arkts-arkui-common-comp-measurable-i.md)&gt; | Yes | Array containing layout information for all child components after measurement.<br>When a child component does not have its layout information set, it retains the previous layout settings or, if no previous layout settings are available, stays at the default size of 0. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Layout constraints applied to the component. |

**Return value:**

| Type | Description |
| --- | --- |
| [SizeResult](arkts-arkui-common-comp-sizeresult-i.md) | Component size information. |

## onNewParam

```TypeScript
onNewParam?(param: ESObject): void
```

Invoked when a page in the routing stack is moved to the top of the stack in the singleton mode of [RouterMode](../arkts-apis/arkts-arkui-router-routermode-e.md). This callback takes effect only for custom components decorated with [\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry) within the [router](../arkts-apis/arkts-arkui-router.md) page stack.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-BaseCustomComponent-onNewParam?(param: ESObject): void--><!--Device-BaseCustomComponent-onNewParam?(param: ESObject): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [ESObject](../../apis-default/arkts-apis/arkts-esobject-t.md) | Yes | Data passed to the target page during routing. It is consistent with the data passed by the **params** field in **router.pushUrl()**, and its structure is defined by the developer. |

## onPageHide

```TypeScript
onPageHide?(): void
```

Invoked each time a router-managed page (a custom component decorated with [\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry)) is hidden, including scenarios such as route navigation and the application moving to the background.

> **NOTE:** 
> 
> To ensure smooth UI responsiveness, avoid executing time-consuming operations within the callback function that
> may block the main thread. For resource-intensive tasks such as camera resource deallocation, consider
> implementing asynchronous solutions. For best practices, see
> [Reducing Application Latency: Postponing Resource Release](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-application-latency-optimization-cases#section8783201923819).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseCustomComponent-onPageHide?(): void--><!--Device-BaseCustomComponent-onPageHide?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onPageShow

```TypeScript
onPageShow?(): void
```

Invoked each time a router-managed page (a custom component decorated with [\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry)) is displayed, including scenarios such as route redirection and the app entering the foreground. It is recommended that you avoid performing time- consuming operations that block the main thread in this callback function, so as not to affect page display performance.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseCustomComponent-onPageShow?(): void--><!--Device-BaseCustomComponent-onPageShow?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onPlaceChildren

```TypeScript
onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void
```

Invoked when the custom component needs to determine the positions of its child components. Through this callback the component receives its child component size constraints from the ArkUI framework. State variables should not be changed in this callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseCustomComponent-onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void--><!--Device-BaseCustomComponent-onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selfLayoutInfo | [GeometryInfo](arkts-arkui-common-comp-geometryinfo-i.md) | Yes | Information about the component's computed layout properties after measurement. |
| children | Array&lt;[Layoutable](arkts-arkui-common-comp-layoutable-i.md)&gt; | Yes | Array containing layout information for all child components after measurement. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Layout constraints applied to the component. |

## onWillApplyTheme

```TypeScript
onWillApplyTheme?(theme: Theme): void
```

Invoked before the **build()** function of a new instance of the custom component is executed, to obtain the **Theme** object of the component context. Unlike **aboutToAppear**, **onWillApplyTheme** is used to initialize state variables based on the **Theme** object, while **aboutToAppear** is used for general initialization logic. You can change state variables in **onWillApplyTheme**, and the changes will take effect in the subsequent execution of the **build()** function.

> **NOTE:** 
> 
> Since API version 18, this API is supported in the components of V2.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseCustomComponent-onWillApplyTheme?(theme: Theme): void--><!--Device-BaseCustomComponent-onWillApplyTheme?(theme: Theme): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| theme | [Theme](arkts-arkui-common-comp-theme-t.md) | Yes | **Theme** object currently in effect for the custom component. In the callback, you can use this object to obtain resources such as theme colors to update the style variables of the component. |

## pageTransition

```TypeScript
pageTransition?(): void
```

Defines the transition animations for page entry and page exit.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseCustomComponent-pageTransition?(): void--><!--Device-BaseCustomComponent-pageTransition?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="querynavdestinationinfo1"></a>

## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(): NavDestinationInfo | undefined
```

Queries the **NavDestination** information of this custom component. This API has effect only when the component is contained within a **NavDestination** component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseCustomComponent-queryNavDestinationInfo(): NavDestinationInfo | undefined--><!--Device-BaseCustomComponent-queryNavDestinationInfo(): NavDestinationInfo | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [NavDestinationInfo](arkts-arkui-common-comp-navdestinationinfo-t.md) &#124; undefined | **NavDestinationInfo** instance obtained. |

<a id="querynavdestinationinfo2"></a>

## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(isInner: Optional<boolean>): NavDestinationInfo | undefined
```

Queries the information of the nearest **NavDestination** component (a navigation page or subpage of the **Navigation** component) associated with this custom component. The search direction is controlled by **isInner**: **true** for inward search and **false** for outward search.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-BaseCustomComponent-queryNavDestinationInfo(isInner: Optional<boolean>): NavDestinationInfo | undefined--><!--Device-BaseCustomComponent-queryNavDestinationInfo(isInner: Optional<boolean>): NavDestinationInfo | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isInner | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to search inward for the nearest **NavDestination** component in the navigation stack.<br>**true**: Search inward.<br>**false**: Search outward. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavDestinationInfo](arkts-arkui-common-comp-navdestinationinfo-t.md) &#124; undefined | **NavDestinationInfo** instance obtained. |

## queryNavigationInfo

```TypeScript
queryNavigationInfo(): NavigationInfo | undefined
```

Queries the **Navigation** information of this custom component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseCustomComponent-queryNavigationInfo(): NavigationInfo | undefined--><!--Device-BaseCustomComponent-queryNavigationInfo(): NavigationInfo | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [NavigationInfo](arkts-arkui-common-comp-navigationinfo-t.md) &#124; undefined | **NavigationInfo** instance obtained. |

## queryRouterPageInfo

```TypeScript
queryRouterPageInfo(): RouterPageInfo | undefined
```

Obtains a **RouterPageInfo** instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseCustomComponent-queryRouterPageInfo(): RouterPageInfo | undefined--><!--Device-BaseCustomComponent-queryRouterPageInfo(): RouterPageInfo | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RouterPageInfo](arkts-arkui-common-comp-routerpageinfo-t.md) &#124; undefined | **RouterPageInfo** instance obtained. |
