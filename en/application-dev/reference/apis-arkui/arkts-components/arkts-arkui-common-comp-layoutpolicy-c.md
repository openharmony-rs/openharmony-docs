# LayoutPolicy

```TypeScript
declare class LayoutPolicy
```

Layout policy for the width and height of a component. It provides three layout policy options: **matchParent**, **wrapContent**, and **fixAtIdealSize**, which are respectively used for scenarios where the component adapts to the parent component layout, adapts to the content but does not exceed the parent component size, and adapts to the content and may exceed the parent component size.

> **NOTE:** 
> 
> - **LayoutPolicy** supports three layout policies: **matchParent** (adapting to the parent component layout), **wrapContent** (adapting to the content but not exceeding the parent component size), and
> **fixAtIdealSize** (adapting to the content and possibly exceeding the parent component size). For
> specific sample code, see
> [Setting the Layout Policy]
> (../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#example-5-setting-the-layout-policy).
> 
> - In the **wrapContent** and **fixAtIdealSize** scenarios, when the component size cannot be determined by the content, if the component size has a default value, the size is measured based on the default value and the component is finally displayed at the default size; if there is no default value, the size is measured based on the width and height (0,0), and the component is finally displayed at zero size.
> 
> - When a container is set to **wrapContent** and a child component is set to **matchParent** (including when **matchParent** is set on only one side), the container is first expanded by child components with determined sizes, and then the child component set to **matchParent** matches the container size. If there is no child component with a determined size, both the container and the child component have a size of 0.
> 
> - The **LayoutPolicy** setting is constrained by **constraintSize**. That is, when **LayoutPolicy** and
> **constraintSize** are set at the same time, the constraint of **constraintSize** takes effect first.
> 
> - Since API version 15, only the width and height attributes of the **Row** and **Column** components support the **LayoutPolicy** type parameter. For other components, setting the **LayoutPolicy** type parameter has the same effect as not setting the width or height. Since API version 20, all basic components support the **LayoutPolicy** type parameter.
> 
> - When the main-axis size of the **Row**, **Column**, or **Flex** component adapts to child components,and child component A sets **matchParent** only on the cross axis, before API version 26.0.0, child component A does not participate in the main-axis size measurement of the **Row**, **Column**, or
> **Flex** component, and the main-axis direction of the **Row**, **Column**, or **Flex** component does
> not adapt to the size of child component A. Since API version 26.0.0, child component A participates in
> the main-axis size measurement of the **Row**, **Column**, or **Flex** component, and the main-axis
> direction of the **Row**, **Column**, or **Flex** component adapts to the size of child component A. The
> same applies to the cross-axis direction. For the specific change effect, see
> [Example 6: Setting matchParent on a Single Direction of a Child Component]
> (../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md
> #example-6-setting-matchparent-on-a-single-direction-of-a-child-component).

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fixAtIdealSize

```TypeScript
static readonly fixAtIdealSize: LayoutPolicy
```

When the current component adapts to its child components (content), its size is equal to that of the child components (content), and its size is not constrained by the content area size of the parent component. This applies to scenarios where the size needs to be automatically adjusted based on the content and can exceed the parent container, such as floating prompts and drop-down menus.

**Type:** [LayoutPolicy](arkts-arkui-common-comp-layoutpolicy-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## matchParent

```TypeScript
static readonly matchParent: LayoutPolicy
```

When the current component adapts to the parent component layout, its size is equal to the content area of the parent component, excluding **padding**, **border**, and **safeAreaPadding**. This applies to scenarios where the component needs to fill the content area of the parent container, such as list items and card containers.

**Type:** [LayoutPolicy](arkts-arkui-common-comp-layoutpolicy-c.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wrapContent

```TypeScript
static readonly wrapContent: LayoutPolicy
```

When the current component adapts to its child components (content), its size is equal to that of the child components (content), and its size is constrained by the content area size of the parent component. This applies to scenarios where the size needs to be automatically adjusted based on the content but cannot exceed the parent container, such as text containers and dialog box content areas.

**Type:** [LayoutPolicy](arkts-arkui-common-comp-layoutpolicy-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
