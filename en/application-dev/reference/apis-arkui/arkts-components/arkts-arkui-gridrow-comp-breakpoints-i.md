# BreakPoints

```TypeScript
declare interface BreakPoints
```

Sets breakpoints for the responsive grid container. For details about breakpoints, see [Breakpoints](../../../ui/arkts-layout-development-grid-layout.md#breakpoints).

<!--code_no_check-->

```ts
// Enable the xs, sm, and md breakpoints.
breakpoints: {value: ['100vp', '200vp']}
// Enable four breakpoints: xs, sm, md, and lg. The breakpoint range must be monotonically increasing.
breakpoints: {value: ['320vp', '600vp', '840vp']}
// Enable five breakpoints: xs, sm, md, lg, and xl. The count of breakpoint ranges must not be greater than
// the total number of configurable breakpoints minus one.
breakpoints: {value: ['320vp', '600vp', '840vp', '1080vp']}
```

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reference

```TypeScript
reference?: BreakpointsReference
```

Reference object for breakpoint switching. The options are **WindowSize** (using the window as the reference) and **ComponentSize** (using the container as the reference).

Default value: **BreakpointsReference.WindowSize**

Invalid value: The default value is used.

**Type:** [BreakpointsReference](arkts-arkui-gridrow-comp-breakpointsreference-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: Array<string>
```

Monotonically increasing array of breakpoint positions. The string format is "number+vp", for example, "320vp" and"600vp".

Default value: **["320vp", "600vp", "840vp"]**

Invalid value: The default value is used.

Unit: vp

The default breakpoints apply to most scenarios. You can customize them for special screen sizes or specific layout requirements.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
