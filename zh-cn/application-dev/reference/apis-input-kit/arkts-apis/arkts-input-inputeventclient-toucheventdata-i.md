# TouchEventData

触屏注入描述信息。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-inputEventClient-interface TouchEventData--><!--Device-inputEventClient-interface TouchEventData-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## touchEvent

```TypeScript
touchEvent: TouchEvent
```

触屏输入事件。

**类型：** TouchEvent

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-TouchEventData-touchEvent: TouchEvent--><!--Device-TouchEventData-touchEvent: TouchEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## useGlobalCoordinate

```TypeScript
useGlobalCoordinate?: boolean
```

是否使用全局坐标来计算注入的触屏输入事件。默认值为false，取值为false表示使用以指定屏幕左上角为原点的相对坐标系的坐标来计算注入的触屏输入事件。取值为true表示使用以主屏左上角为原点的全局坐标系的坐标来计算注入的触屏 输入事件。

**类型：** boolean

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-TouchEventData-useGlobalCoordinate?: boolean--><!--Device-TouchEventData-useGlobalCoordinate?: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

