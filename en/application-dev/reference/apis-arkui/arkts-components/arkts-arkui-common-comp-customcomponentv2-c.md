# CustomComponentV2

```TypeScript
declare class CustomComponentV2 extends BaseCustomComponent
```

Custom ComponentV2

**Inheritance/Implementation:** CustomComponentV2 extends [BaseCustomComponent](arkts-arkui-common-comp-basecustomcomponent-c.md)

**Since:** 18

<!--Device-unnamed-declare class CustomComponentV2 extends BaseCustomComponent--><!--Device-unnamed-declare class CustomComponentV2 extends BaseCustomComponent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToReuse

```TypeScript
aboutToReuse?(): void
```

When a reusable custom component of state management V2 is re-added to the node tree from the reuse cache, the **aboutToReuse** lifecycle callback is triggered. In frequently invoked scenarios, avoid performing time-consuming operations in it, otherwise frame loss and lag may occur.

For details, see [\@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomComponentV2-aboutToReuse?(): void--><!--Device-CustomComponentV2-aboutToReuse?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
