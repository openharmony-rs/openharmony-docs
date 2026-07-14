# Touch

触屏点信息。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## globalX

```TypeScript
globalX?: number
```

该触屏输入事件以主屏左上角为原点的全局坐标系的X坐标，单位为像素（px）。<!--Del-->作为入参时，若接口参数中的
[TouchEventData.useGlobalCoordinate](arkts-input-toucheventdata-i-sys.md)为
true，该值必填，当前仅支持整数。若为false，该值无需填写，使用指定屏幕左上角为原点的相对坐标系的X坐标计算注入事件。<!--DelEnd-->作为出参时，由系统上报。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## globalY

```TypeScript
globalY?: number
```

该触屏输入事件以主屏左上角为原点的全局坐标系的Y坐标，单位为像素（px）。<!--Del-->作为入参时，若接口参数中的
[TouchEventData.useGlobalCoordinate](arkts-input-toucheventdata-i-sys.md)为
true，该值必填，当前仅支持整数。若为false，该值无需填写，使用指定屏幕左上角为原点的相对坐标系的Y坐标计算注入事件。<!--DelEnd-->作为出参时，由系统上报。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## height

```TypeScript
height: number
```

触屏区域的高度，单位为像素（px）。当前仅支持整数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## id

```TypeScript
id: number
```

触屏输入事件ID。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## pressedTime

```TypeScript
pressedTime: number
```

按下时间戳，表示系统启动运行至今逝去的微秒数，单位为微秒（μs）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## pressure

```TypeScript
pressure: number
```

压力值，取值范围是[0.0, 1.0]，0.0表示不支持。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## rawX

```TypeScript
rawX: number
```

输入设备上的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## rawY

```TypeScript
rawY: number
```

输入设备上的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenX

```TypeScript
screenX: number
```

该触屏输入事件以指定屏幕左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenY

```TypeScript
screenY: number
```

该触屏输入事件以指定屏幕左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## tiltX

```TypeScript
tiltX: number
```

相对YZ平面的角度，单位为度，取值的范围[-90, 90]，其中正值是向右倾斜。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## tiltY

```TypeScript
tiltY: number
```

相对XZ平面的角度，单位为度，取值的范围[-90, 90]，其中正值是向下倾斜。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolHeight

```TypeScript
toolHeight: number
```

工具区域高度，单位为像素（px）。当前仅支持整数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolType

```TypeScript
toolType: ToolType
```

工具类型。

**类型：** ToolType

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolWidth

```TypeScript
toolWidth: number
```

工具区域宽度，单位为像素（px）。当前仅支持整数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolX

```TypeScript
toolX: number
```

工具区域的中心点以指定屏幕左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolY

```TypeScript
toolY: number
```

工具区域的中心点以指定屏幕左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## width

```TypeScript
width: number
```

触屏区域的宽度，单位为像素（px）。当前仅支持整数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowX

```TypeScript
windowX: number
```

触屏所在窗口左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowY

```TypeScript
windowY: number
```

触屏所在窗口左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

