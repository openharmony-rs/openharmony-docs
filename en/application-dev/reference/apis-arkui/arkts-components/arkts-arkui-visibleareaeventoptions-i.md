# VisibleAreaEventOptions

Describes visible area change configuration options.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## expectedUpdateInterval

```TypeScript
expectedUpdateInterval?: number
```

Expected calculation interval, in ms. If the value is less than 100 or set to **NaN**, the default value **100** is used. If the value is greater than 2^31-1, the default value **2^31-1** is used.

Default value: **1000**.

**Type:** number

**Default:** 1000

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## measureFromViewport

```TypeScript
measureFromViewport?: boolean
```

Visible area calculation mode.

**true**: considers the parent's [clip](arkts-arkui-commonmethod-c.md#clip) attribute. If [clip](arkts-arkui-commonmethod-c.md#clip) is **false**, areas of the child component beyond the parent's bounds are counted as visible; if [clip](arkts-arkui-commonmethod-c.md#clip) is **true**, such areas are counted as invisible. **false**: ignores the parent's [clip](arkts-arkui-commonmethod-c.md#clip) attribute, treating areas beyond the parent's bounds as invisible.

Default value: **false**.

When **measureFromViewport** is set to **true**, and an ancestor node has the [scale](arkts-arkui-commonmethod-c.md#scale) attribute set, the component's visible ratio will be correctly calculated.

**Type:** boolean

**Default:** false

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ratios

```TypeScript
ratios: Array<number>
```

Threshold array. Each threshold represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. The value of each threshold ranges from 0.0 to 1.0. If a threshold value is less than 0.0, it is clamped to 0.0; if it is greater than 1.0, it is clamped to 1.0.

**Type:** Array&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
