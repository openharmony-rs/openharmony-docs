# GridColColumnOption

Describes the numbers of grid columns occupied by the **GridCol** component on devices with different width types.

- In versions earlier than API version 20: When you configure **GridCol** column spans only at specific breakpoints,  
unconfigured breakpoints inherit values from the next smaller configured breakpoint. If no smaller breakpoint is configured, the default value of **1** is used. <!--code_no_check-->  
 ```ts
 span: {xs:2, md:4, lg:8} // Equivalent to span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
 span: {md:4, lg:8} // Equivalent to span: {xs:1, sm:1, md:4, lg:8, xl:8, xxl:8}.
 ```  
- Since API version 20: When you configure **GridCol** column spans only at specific breakpoints, unconfigured  
breakpoints inherit values from the next smaller configured breakpoint. If no smaller breakpoint exists, values are inherited from the next larger configured breakpoint. <!--code_no_check-->  
 ```ts
 span: {xs:2, md:4, lg:8} // Equivalent to span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
 span: {md:4, lg:8} // Equivalent to span: {xs:4, sm:4, md:4, lg:8, xl:8, xxl:8}.
 ```  
- Recommendation: Explicitly configure **GridCol** column spans for all required breakpoints to prevent unexpected  
layout behavior caused by automatic value inheritance.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lg

```TypeScript
lg?: number
```

Number of grid columns on the device where the grid size is lg.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## md

```TypeScript
md?: number
```

Number of grid columns on the device where the grid size is md.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sm

```TypeScript
sm?: number
```

Number of grid columns on the device where the grid size is sm.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## xl

```TypeScript
xl?: number
```

Number of grid columns on the device where the grid size is xl.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## xs

```TypeScript
xs?: number
```

Number of grid columns on the device where the grid size is xs.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## xxl

```TypeScript
xxl?: number
```

Number of grid columns on the device where the grid size is xxl.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
