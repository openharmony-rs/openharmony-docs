# GuideLinePosition

```TypeScript
declare interface GuideLinePosition
```

Defines the position of a guideline.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end? : Dimension
```

Distance from the guideline to the right or bottom edge of the container. Unit: vp. Either this parameter or **start** is used. If both are declared, only **start** takes effect. If the **width** of the container is declared as **"auto"**, a guideline of the **Axis.Vertical** type does not support declaration in the **end** mode. If the **height** of the container is declared as **"auto"**, a guideline of the **Axis.Horizontal** type does not support declaration in the **end** mode.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start? : Dimension
```

Distance from the guideline to the left or top edge of the container. Unit: vp.

Default value: **0**. Either this parameter or **end** is used. If both are declared, only **start** takes effect. If the **width** of the container is declared as "auto", a guideline of the **Axis.Vertical** type can be declared only in the **start** mode (percentage is not allowed). If the **height** of the container is declared as **"auto"**, a guideline of the **Axis.Horizontal** type can be declared only in the **start** mode (percentage is not allowed).

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
