# PatternLockController

```TypeScript
declare class PatternLockController
```

Controller of the **PatternLock** component, used to reset the component state and set the pattern password state.

**Since:** 9

<!--Device-unnamed-declare class PatternLockController--><!--Device-unnamed-declare class PatternLockController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Objects to Import

```typescript
let patternLockController: PatternLockController = new PatternLockController();
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **PatternLockController** instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockController-constructor()--><!--Device-PatternLockController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reset

```TypeScript
reset()
```

Resets the component state. This API takes effect only when the corresponding controller parameter is passed in when the **PatternLock** component is constructed. If it is not passed in, the call does not take effect.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockController-reset()--><!--Device-PatternLockController-reset()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setChallengeResult

```TypeScript
setChallengeResult(result: PatternLockChallengeResult): void
```

Sets the correct or incorrect state of the pattern password. This API takes effect only when the corresponding controller parameter is passed in when the **PatternLock** component is constructed. If it is not passed in, the call does not take effect.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockController-setChallengeResult(result: PatternLockChallengeResult): void--><!--Device-PatternLockController-setChallengeResult(result: PatternLockChallengeResult): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [PatternLockChallengeResult](arkts-arkui-patternlock-comp-patternlockchallengeresult-e.md) | Yes | Authentication challenge result of the pattern password. The status can be correct or incorrect. |
