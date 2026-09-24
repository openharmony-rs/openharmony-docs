# GridRowColumnOption

```TypeScript
declare interface GridRowColumnOption
```

Describes the grid column number configuration for different device width types.

Before API Version 20, if only partial breakpoints are set for **GridRow**'s grid column count, unconfiguredbreakpoints inherit the column count from the nearest smaller configured breakpoint (for instance, **sm** is the nearest smaller breakpoint of **md**). If no such smaller breakpoint is configured, the default grid column count 12 is used as a fallback.

<!--code_no_check-->

```ts
columns: {xs:2, md:4, lg:8} // Equivalent to columns: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
columns: {md:4, lg:8} // Equivalent to columns: {xs:12, sm:12, md:4, lg:8, xl:8, xxl:8}.
```

Since API version 20, if only partial breakpoints are set for **GridRow**'s grid column count, unconfiguredbreakpoints inherit the column count from the nearest smaller configured breakpoint. If no smaller configured breakpoint is available, the value from the nearest larger configured breakpoint is used as a fallback.

<!--code_no_check-->

```ts
columns: {xs:2, md:4, lg:8} // Equivalent to columns: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
columns: {md:4, lg:8} // Equivalent to columns: {xs:4, sm:4, md:4, lg:8, xl:8, xxl:8}.
```

Recommendation: Explicitly configure **GridRow** column spans for all required breakpoints to prevent unexpected layout behavior caused by automatic value inheritance.

The width of each column is the content area size of the **GridRow** component minus the gutter of the grid child components, and then divided by the total number of columns. For example, if a **GridRow** with a width of 800 vp has **columns** set to 12, **gutter** set to 10 vp, and **padding** set to 20 vp, the width of each column is (800 – 20 × 2 – 10 × 11)/12.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lg

```TypeScript
lg?: number
```

Number of grid columns of the grid container on a large-width device. The value is a positive integer.

- Before API version 20: the default value is **12**.  
- Since API version 20: the default value is **12**.

If an invalid value is set, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## md

```TypeScript
md?: number
```

Number of grid columns of the grid container on a medium-width device. The value is a positive integer.

- Before API version 20: the default value is **12**.  
- Since API version 20: the default value is **8**.

If an invalid value is set, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sm

```TypeScript
sm?: number
```

Number of grid columns of the grid container on a small-width device. The value is a positive integer.

- Before API version 20: the default value is **12**.  
- Since API version 20: the default value is **4**.

If an invalid value is set, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## xl

```TypeScript
xl?: number
```

Number of grid columns of the grid container on an extra-large-width device. The value is a positive integer.

- Before API version 20: the default value is **12**.  
- Since API version 20: the default value is **12**.

If an invalid value is set, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## xs

```TypeScript
xs?: number
```

Number of grid columns of the grid container on a minimum-width device. The value is a positive integer.

- Before API version 20: the default value is **12**.  
- Since API version 20: the default value is **2**.

If an invalid value is set, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## xxl

```TypeScript
xxl?: number
```

Number of grid columns of the grid container on an extra-extra-large-width device. The value is a positive integer.

- Before API version 20: the default value is **12**.  
- Since API version 20: the default value is **12**.

If an invalid value is set, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
