# KeyOptions (System API)

Represents combination key options.

**Since:** 8

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

For example, in the combination keys **Ctrl+Alt+A**, **A** is called the final key.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## finalKeyDownDuration

```TypeScript
finalKeyDownDuration: number
```

Duration for holding down the key, in μs.

If the value of this field is **0**, a callback is triggered immediately.

If the value of this field is greater than **0** and **isFinalKeyDown** is **true**, a callback is triggered when the key keeps being pressed after the specified duration expires. If **isFinalKeyDown** is **false**, a callback is triggered when the key is released before the specified duration expires.

**Type:** number

**Since:** 8

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

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## isRepeat

```TypeScript
isRepeat?: boolean
```

Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite. The default value is **true**.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## preKeys

```TypeScript
preKeys: Array<number>
```

Preceding key set. The number of preceding keys ranges from 0 to 4. There is no requirement on the sequence of the keys.

For example, in the combination keys **Ctrl+Alt+A**, **Ctrl+Alt** are called preceding keys.

**Type:** Array&lt;number&gt;

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

## triggerType

```TypeScript
triggerType?: KeyCommandTriggerType
```

Trigger type, which indicates that the conditions for triggering the callback expected by the shortcut key are met. Once this value is set, isFinalKeyDown and isRepeat will be ignored. This property is only for use in APIs that take KeyCommandCallback as the callback function and must be specified.

**Type:** [KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.
