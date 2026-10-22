# KeyOptions (System API)

```TypeScript
interface KeyOptions
```

Represents key combination options.

**Since:** 8

<!--Device-inputConsumer-interface KeyOptions--><!--Device-inputConsumer-interface KeyOptions-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## finalKey

```TypeScript
finalKey: number
```

Final key. This parameter is mandatory. A callback is triggered by the final key.

For example, in the combination keys **Ctrl+Alt+A**, **A** is the final key.

**Type:** number

**Since:** 8

<!--Device-KeyOptions-finalKey: int--><!--Device-KeyOptions-finalKey: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## finalKeyDownDuration

```TypeScript
finalKeyDownDuration: number
```

Duration for which the final key is held down, in microseconds (μs).

When finalKeyDownDuration is 0, the callback function is triggered immediately.

When finalKeyDownDuration is greater than 0 and isFinalKeyDown is true, the callback function is triggered after the final key is held down for longer than the set duration; when isFinalKeyDown is false, the callback function is triggered when the time from pressing to releasing the final key is shorter than the set duration.

**Type:** number

**Since:** 8

<!--Device-KeyOptions-finalKeyDownDuration: int--><!--Device-KeyOptions-finalKeyDownDuration: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## isFinalKeyDown

```TypeScript
isFinalKeyDown: boolean
```

Whether the final key is pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 8

<!--Device-KeyOptions-isFinalKeyDown: boolean--><!--Device-KeyOptions-isFinalKeyDown: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## isRepeat

```TypeScript
isRepeat?: boolean
```

Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite. The default value is **true**.

**Type:** boolean

**Since:** 18

<!--Device-KeyOptions-isRepeat?: boolean--><!--Device-KeyOptions-isRepeat?: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## preKeys

```TypeScript
preKeys: Array<number>
```

Set of preKeys, with the number ranging from 0 to 4. The order of preKeys is not required.

For example, in the key combination Ctrl+Alt+A, Ctrl+Alt are the preKeys.

**Type:** Array&lt;number&gt;

**Since:** 8

<!--Device-KeyOptions-preKeys: Array<int>--><!--Device-KeyOptions-preKeys: Array<int>-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## triggerType

```TypeScript
triggerType?: KeyCommandTriggerType
```

Trigger mode. The value can be PRESSED (1), REPEAT_PRESSED (2), or ALL_RELEASED (3). The command trigger mode is enabled. Once this value is set, isFinalKeyDown and isRepeat are ignored. This parameter is optional for the [inputConsumer.on('key')](arkts-input-inputconsumer-on-f-sys.md#onkey) API and mandatory for the [inputConsumer.onKey](arkts-input-inputconsumer-onkey-f-sys.md#onkey-2) API.

**Type:** [KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-KeyOptions-triggerType?: KeyCommandTriggerType--><!--Device-KeyOptions-triggerType?: KeyCommandTriggerType-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.
