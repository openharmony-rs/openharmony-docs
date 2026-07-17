# KeyCommandTriggerType（系统接口）

按键命令触发类型枚举，用于指定组合按键的触发时机。

**起始版本：** 26.0.0

<!--Device-inputConsumer-export enum KeyCommandTriggerType--><!--Device-inputConsumer-export enum KeyCommandTriggerType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## PRESSED

```TypeScript
PRESSED = 1
```

首次按下触发。当最终按键首次按下时触发回调，自动重复按下不触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyCommandTriggerType-PRESSED = 1--><!--Device-KeyCommandTriggerType-PRESSED = 1-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## REPEAT_PRESSED

```TypeScript
REPEAT_PRESSED = 2
```

重复按下触发。当最终按键每次按下时都触发回调，包括自动重复按下。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyCommandTriggerType-REPEAT_PRESSED = 2--><!--Device-KeyCommandTriggerType-REPEAT_PRESSED = 2-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## ALL_RELEASED

```TypeScript
ALL_RELEASED = 3
```

按下按键或抬起按键时均会触发回调。包括自动重复按下的按键。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyCommandTriggerType-ALL_RELEASED = 3--><!--Device-KeyCommandTriggerType-ALL_RELEASED = 3-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

