# RecordCmdUtils

该类提供了一组录制回放命令的操作。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## beginRecording

```TypeScript
beginRecording(width: number, height: number): Canvas
```

获取记录绘制命令的画布。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 录制画布的宽度。<br>单位: px <br>取值范围:大于0的整数。<br>宽度值必须大于0。 |
| height | number | 是 | 录制画布的高度。<br>单位: px <br>取值范围:大于0的整数。<br>高度值必须大于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Canvas](arkts-arkgraphics2d-drawing-canvas-c.md) | 返回用于录制绘制指令的画布对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## finishRecording

```TypeScript
finishRecording(): RecordCmd
```

结束录制，返回录制的绘制指令对象。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RecordCmd](arkts-arkgraphics2d-drawing-recordcmd-i.md) | 返回已录制的绘制指令对象。 |

## getHeight

```TypeScript
getHeight(): number
```

获取录制画布的高度。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回录制画布的高度。 |

## getWidth

```TypeScript
getWidth(): number
```

获取录制画布的宽度。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回录制画布的宽度。 |
