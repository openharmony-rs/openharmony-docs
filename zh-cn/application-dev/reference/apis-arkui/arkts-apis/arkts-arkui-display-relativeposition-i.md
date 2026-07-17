# RelativePosition

相对坐标系下的坐标位置，以displayId对应的屏幕左上角为原点。

**起始版本：** 20

<!--Device-display-interface RelativePosition--><!--Device-display-interface RelativePosition-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId: number
```

相对坐标所对应的屏幕ID，仅支持整数输入，且需大于等于0。

**类型：** number

**起始版本：** 20

<!--Device-RelativePosition-displayId: long--><!--Device-RelativePosition-displayId: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## position

```TypeScript
position: Position
```

以displayId所指定屏幕左上角为原点的坐标值。

**类型：** Position

**起始版本：** 20

<!--Device-RelativePosition-position: Position--><!--Device-RelativePosition-position: Position-End-->

**系统能力：** SystemCapability.Window.SessionManager

