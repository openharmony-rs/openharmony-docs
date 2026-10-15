# KeyCommandTriggerType (System API)

```TypeScript
export enum KeyCommandTriggerType
```

Enumerates the key command trigger types, which are used to specify the trigger timing of key combinations.

**Since:** 26.0.0

<!--Device-inputConsumer-export enum KeyCommandTriggerType--><!--Device-inputConsumer-export enum KeyCommandTriggerType-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## ALL_RELEASED

```TypeScript
ALL_RELEASED = 3
```

The callback is triggered both when a key is pressed and when it is released, including automatically repeated key presses.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-KeyCommandTriggerType-ALL_RELEASED = 3--><!--Device-KeyCommandTriggerType-ALL_RELEASED = 3-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## PRESSED

```TypeScript
PRESSED = 1
```

Triggered on the first press. The callback is triggered when the final key is pressed for the first time, and is not triggered on automatic repeated presses.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-KeyCommandTriggerType-PRESSED = 1--><!--Device-KeyCommandTriggerType-PRESSED = 1-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## REPEAT_PRESSED

```TypeScript
REPEAT_PRESSED = 2
```

Triggered on repeated press. The callback is triggered each time the final key is pressed, including automatic repeated presses.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-KeyCommandTriggerType-REPEAT_PRESSED = 2--><!--Device-KeyCommandTriggerType-REPEAT_PRESSED = 2-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.
