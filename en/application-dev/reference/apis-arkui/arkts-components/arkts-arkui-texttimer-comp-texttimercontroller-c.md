# TextTimerController

```TypeScript
declare class TextTimerController
```

Defines the controller for controlling the **TextTimer** component. A **TextTimer** component can only be bound to one controller, and the relevant commands can only be called after the component has been created. A **TextTimerController** can control only the last **TextTimer** component bound to it.

## Objects to Import

```ts
textTimerController: TextTimerController = new TextTimerController()
```

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **TextTimerController** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause()
```

Pauses the timer.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reset

```TypeScript
reset()
```

Resets the timer.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start()
```

Starts the timer.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
