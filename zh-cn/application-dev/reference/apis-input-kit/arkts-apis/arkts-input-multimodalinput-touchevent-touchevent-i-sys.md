# TouchEvent

触屏输入事件。

**继承/实现关系：** TouchEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
```

## fixedMode

```TypeScript
fixedMode?: FixedMode
```

修正坐标的模式。默认值为FixedMode.NONE。

**类型：** [FixedMode](arkts-input-multimodalinput-touchevent-fixedmode-e-sys.md)

**起始版本：** 19

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## isInject

```TypeScript
isInject?: boolean
```

表示该触屏输入事件是否为注入事件。默认值为false。注入事件详细介绍可参考 [@ohos.multimodalInput.inputEventClient](arkts-multimodalinput-inputeventclient.md)。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。
