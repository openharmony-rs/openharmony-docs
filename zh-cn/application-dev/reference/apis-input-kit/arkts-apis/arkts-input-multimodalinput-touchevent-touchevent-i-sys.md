# TouchEvent

触屏输入事件。

**继承/实现关系：** TouchEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export declare interface TouchEvent extends InputEvent--><!--Device-unnamed-export declare interface TouchEvent extends InputEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## fixedMode

```TypeScript
fixedMode?: FixedMode
```

修正坐标的模式。

**类型：** FixedMode

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-TouchEvent-fixedMode?: FixedMode--><!--Device-TouchEvent-fixedMode?: FixedMode-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## isInject

```TypeScript
isInject?: boolean
```

表示该触屏输入事件是否为注入事件。注入事件详细介绍可参考 [@ohos.multimodalInput.inputEventClient]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** boolean

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-TouchEvent-isInject?: boolean--><!--Device-TouchEvent-isInject?: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

