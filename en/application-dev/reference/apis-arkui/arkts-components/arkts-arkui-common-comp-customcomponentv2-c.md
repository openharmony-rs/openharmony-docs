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

aboutToReuse Method for @ComponentV2, it is executed when fetching instance of custom component from RecyclePool. It is different from the @Reusable in CustomComponent, there is no param parameter in this callback.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomComponentV2-aboutToReuse?(): void--><!--Device-CustomComponentV2-aboutToReuse?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
