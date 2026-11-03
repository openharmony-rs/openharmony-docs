# RepeatController

```TypeScript
declare class RepeatController
```

Defines a controller of the **Repeat** component. You can bind the controller to the **Repeat** component through the **controller** field in [RepeatOptions](arkts-arkui-repeat-comp-repeatoptions-i.md) and call [clearCache](#clearcache) to clear the nodes in the reuse pool of the **Repeat** component as needed.

**Since:** 26.1.0

<!--Device-unnamed-declare class RepeatController--><!--Device-unnamed-declare class RepeatController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clearCache

```TypeScript
clearCache(): void
```

Clears the nodes in the reuse pool of the **Repeat** component bound to this controller.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RepeatController-clearCache(): void--><!--Device-RepeatController-clearCache(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a <em>RepeatController</em> object.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RepeatController-constructor()--><!--Device-RepeatController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
