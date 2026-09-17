# LayoutPolicy

Enumerates the layout policies for component width and height.

> **NOTE:** 
> 
> - **LayoutPolicy** supports three layout policies: **matchParent** (adapts to the parent component's layout),
> **wrapContent** (adapts to content but does not exceed the parent component's size), **fixAtIdealSize**
> (adapts to content and may exceed the parent component's size).
> 
> - For **wrapContent** and **fixAtIdealSize**:If the component's size cannot be determined by its content, it uses the default size (if available);otherwise, it calculates the size as (0, 0).
> 
> - When a container is set to **wrapContent** and contains child components set to **matchParent**(including cases where only one side is set to **matchParent**): (1) The container is first expanded by child components with determinate sizes. (2) Child components set to **matchParent** then adapt to the container's size. (3) If no child components have determinate sizes, both the container and its child components have a zero size.
> 
> - **LayoutPolicy** has lower priority than **constraintSize**.
> 
> - Since API version 15, only the width and height attributes of **Row** and **Column** components support the **LayoutPolicy** type. Setting **LayoutPolicy** on other components produces the same behavior as having no width or height specified. Since API version 20, all basic components support the **LayoutPolicy** type.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fixAtIdealSize

```TypeScript
static readonly fixAtIdealSize: LayoutPolicy
```

When the component adapts to its child components (content), its size equals the child components (content) and is not constrained by the parent component's content area size.

**Type:** [LayoutPolicy](arkts-arkui-layoutpolicy-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## matchParent

```TypeScript
static readonly matchParent: LayoutPolicy
```

When the component adapts to the parent component's layout, its size equals the parent component's content area (excluding the areas defined by **padding**, **border**, and **safeAreaPadding**).

**Type:** [LayoutPolicy](arkts-arkui-layoutpolicy-c.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wrapContent

```TypeScript
static readonly wrapContent: LayoutPolicy
```

When the component adapts to its child components (content), its size equals the child components (content) and is constrained by the parent component's content area size.

**Type:** [LayoutPolicy](arkts-arkui-layoutpolicy-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
