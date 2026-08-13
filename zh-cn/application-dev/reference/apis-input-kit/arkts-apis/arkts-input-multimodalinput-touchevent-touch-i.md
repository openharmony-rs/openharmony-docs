# Touch

触屏点信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface Touch--><!--Device-unnamed-export declare interface Touch-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## globalX

```TypeScript
globalX?: int
```

该触屏输入事件以主屏左上角为原点的全局坐标系的X坐标，单位为像素（px）。&lt;!--Del--&gt;作为入参时，若接口参数中的 [TouchEventData.useGlobalCoordinate](arkts-input-inputeventclient-toucheventdata-i-sys.md#TouchEventData（系统接口）)为 true，该值必填，当前仅支持整数。若为false，该值无需填写，使用指定屏幕左上角为原点的相对坐标系的X坐标计算注入事件。&lt;!--DelEnd--&gt;作为出参时，由系统上报。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-globalX?: int--><!--Device-Touch-globalX?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## globalY

```TypeScript
globalY?: int
```

该触屏输入事件以主屏左上角为原点的全局坐标系的Y坐标，单位为像素（px）。&lt;!--Del--&gt;作为入参时，若接口参数中的 [TouchEventData.useGlobalCoordinate](arkts-input-inputeventclient-toucheventdata-i-sys.md#TouchEventData（系统接口）)为 true，该值必填，当前仅支持整数。若为false，该值无需填写，使用指定屏幕左上角为原点的相对坐标系的Y坐标计算注入事件。&lt;!--DelEnd--&gt;作为出参时，由系统上报。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-globalY?: int--><!--Device-Touch-globalY?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## height

```TypeScript
height: int
```

触屏区域的高度，单位为像素（px）。当前仅支持整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-height: int--><!--Device-Touch-height: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## id

```TypeScript
id: int
```

触屏输入事件ID。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-id: int--><!--Device-Touch-id: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## pressedTime

```TypeScript
pressedTime: long
```

按下时间戳，表示系统启动运行至今逝去的微秒数，单位为微秒（μs）。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-pressedTime: long--><!--Device-Touch-pressedTime: long-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## pressure

```TypeScript
pressure: double
```

压力值，取值范围是[0.0, 1.0]，0.0表示不支持。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-pressure: double--><!--Device-Touch-pressure: double-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## rawX

```TypeScript
rawX: int
```

输入设备上的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-rawX: int--><!--Device-Touch-rawX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## rawY

```TypeScript
rawY: int
```

输入设备上的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-rawY: int--><!--Device-Touch-rawY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenX

```TypeScript
screenX: int
```

该触屏输入事件以指定屏幕左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-screenX: int--><!--Device-Touch-screenX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenY

```TypeScript
screenY: int
```

该触屏输入事件以指定屏幕左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-screenY: int--><!--Device-Touch-screenY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## tiltX

```TypeScript
tiltX: int
```

相对YZ平面的角度，单位为度，取值的范围[-90, 90]，其中正值是向右倾斜。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-tiltX: int--><!--Device-Touch-tiltX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## tiltY

```TypeScript
tiltY: int
```

相对XZ平面的角度，单位为度，取值的范围[-90, 90]，其中正值是向下倾斜。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-tiltY: int--><!--Device-Touch-tiltY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolHeight

```TypeScript
toolHeight: int
```

工具区域高度，单位为像素（px）。当前仅支持整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-toolHeight: int--><!--Device-Touch-toolHeight: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolType

```TypeScript
toolType: ToolType
```

工具类型。

**类型：** [ToolType](arkts-input-multimodalinput-touchevent-tooltype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-toolType: ToolType--><!--Device-Touch-toolType: ToolType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolWidth

```TypeScript
toolWidth: int
```

工具区域宽度，单位为像素（px）。当前仅支持整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-toolWidth: int--><!--Device-Touch-toolWidth: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolX

```TypeScript
toolX: int
```

工具区域的中心点以指定屏幕左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-toolX: int--><!--Device-Touch-toolX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolY

```TypeScript
toolY: int
```

工具区域的中心点以指定屏幕左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-toolY: int--><!--Device-Touch-toolY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## width

```TypeScript
width: int
```

触屏区域的宽度，单位为像素（px）。当前仅支持整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-width: int--><!--Device-Touch-width: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowX

```TypeScript
windowX: int
```

触屏所在窗口左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-windowX: int--><!--Device-Touch-windowX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowY

```TypeScript
windowY: int
```

触屏所在窗口左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Touch-windowY: int--><!--Device-Touch-windowY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

