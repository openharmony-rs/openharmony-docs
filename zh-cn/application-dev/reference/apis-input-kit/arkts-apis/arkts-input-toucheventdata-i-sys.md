# TouchEventData（系统接口）

触屏注入描述信息。

**起始版本：** 11

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## touchEvent

```TypeScript
touchEvent: TouchEvent
```

触屏输入事件。

**类型：** TouchEvent

**起始版本：** 11

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## useGlobalCoordinate

```TypeScript
useGlobalCoordinate?: boolean
```

是否使用全局坐标来计算注入的触屏输入事件。默认值为false，取值为false表示使用以指定屏幕左上角为原点的相对坐标系的坐标来计算注入的触屏输入事件。取值为true表示使用以主屏左上角为原点的全局坐标系的坐标来计算注入的触屏
输入事件。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

