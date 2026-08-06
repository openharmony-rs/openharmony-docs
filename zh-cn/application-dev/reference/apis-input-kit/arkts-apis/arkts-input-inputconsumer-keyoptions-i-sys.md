# KeyOptions（系统接口）

组合键选项。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-inputConsumer-interface KeyOptions--><!--Device-inputConsumer-interface KeyOptions-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## finalKey

```TypeScript
finalKey: int
```

最终按键，此项必填，最终按键触发上报回调函数。 如组合按键Ctrl+Alt+A中，A称为最终按键。

**类型：** int

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyOptions-finalKey: int--><!--Device-KeyOptions-finalKey: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## finalKeyDownDuration

```TypeScript
finalKeyDownDuration: int
```

最终按键保持按下持续时间，单位为微秒（μs）。 当finalKeyDownDuration为0时，立即触发回调函数。 当finalKeyDownDuration大于0时，isFinalKeyDown为true，则最终按键按下超过设置时长后触发回调函数；isFinalKeyDown为false，则最终按键按下到抬起时间小于设置时长时触发回调函 数。

**类型：** int

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyOptions-finalKeyDownDuration: int--><!--Device-KeyOptions-finalKeyDownDuration: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## isFinalKeyDown

```TypeScript
isFinalKeyDown: boolean
```

最终按键状态。 true表示按键按下，false表示按键抬起。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyOptions-isFinalKeyDown: boolean--><!--Device-KeyOptions-isFinalKeyDown: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## isRepeat

```TypeScript
isRepeat?: boolean
```

是否上报重复的按键事件。true表示上报，false表示不上报，若不填默认为true。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-KeyOptions-isRepeat?: boolean--><!--Device-KeyOptions-isRepeat?: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## preKeys

```TypeScript
preKeys: Array<int>
```

前置按键集合，数量范围[0, 4]，前置按键无顺序要求。 如组合按键Ctrl+Alt+A中，Ctrl+Alt称为前置按键。

**类型：** Array&lt;int&gt;

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyOptions-preKeys: Array<int>--><!--Device-KeyOptions-preKeys: Array<int>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

## triggerType

```TypeScript
triggerType?: KeyCommandTriggerType
```

触发模式。取值为PRESSED(1)、REPEAT\_PRESSED(2)或ALL\_RELEASED(3)。启用命令触发模式。一旦设置此值，isFinalKeyDown和isRepeat将被忽略。对于 [inputConsumer.on('key')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 接口该参数是可选参数，对于 [inputConsumer.onKey]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口该参数是必填参数。

**类型：** KeyCommandTriggerType

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyOptions-triggerType?: KeyCommandTriggerType--><!--Device-KeyOptions-triggerType?: KeyCommandTriggerType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

