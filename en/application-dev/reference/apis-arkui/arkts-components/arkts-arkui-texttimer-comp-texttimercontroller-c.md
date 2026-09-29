# TextTimerController

```TypeScript
declare class TextTimerController
```

Defines the controller for controlling the **TextTimer** component. A **TextTimer** component can only be bound to one controller, and the relevant commands can only be called after the component has been created. A **TextTimerController** can control only the last **TextTimer** component bound to it.

## Objects to Import

``` ts
textTimerController: TextTimerController = new TextTimerController();
```

**Since:** 8

<!--Device-unnamed-declare class TextTimerController--><!--Device-unnamed-declare class TextTimerController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **TextTimerController** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerController-constructor()--><!--Device-TextTimerController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause()
```

Pauses the timer. This API must be called after the component is created.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerController-pause()--><!--Device-TextTimerController-pause()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reset

```TypeScript
reset()
```

Resets the timer. This API must be called after the component is created.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerController-reset()--><!--Device-TextTimerController-reset()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start()
```

Starts the timer. This API must be called after the **TextTimer** component is created and the controller is bound.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerController-start()--><!--Device-TextTimerController-start()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
