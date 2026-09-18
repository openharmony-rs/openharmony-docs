# BreakPoints

Sets breakpoints for the responsive grid container. For details about breakpoints, see [Breakpoints](../../../ui/arkts-layout-development-grid-layout.md#breakpoints).

<!--code_no_check-->

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reference

```TypeScript
reference?: BreakpointsReference
```

Breakpoint switching reference.

Default value: **BreakpointsReference.WindowSize**

Invalid values are treated as the default value.

**Type:** [BreakpointsReference](arkts-arkui-breakpointsreference-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: Array<string>
```

Array of monotonically increasing breakpoints.

Default value: **["320vp", "600vp", "840vp"]**

Invalid values are treated as the default value.

Unit: vp.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
