# Position

坐标位置：在全局坐标系中，以主屏左上角为原点。在相对坐标系中，以指定屏幕左上角为原点。

**起始版本：** 20

<!--Device-display-interface Position--><!--Device-display-interface Position-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## x

```TypeScript
x: number
```

相对原点的横坐标，单位为px，该参数应为32位有符号整数，输入浮点数时向下取整。

**类型：** number

**起始版本：** 20

<!--Device-Position-x: long--><!--Device-Position-x: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## y

```TypeScript
y: number
```

相对原点的纵坐标，单位为px，该参数应为32位有符号整数，输入浮点数时向下取整。

**类型：** number

**起始版本：** 20

<!--Device-Position-y: long--><!--Device-Position-y: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

