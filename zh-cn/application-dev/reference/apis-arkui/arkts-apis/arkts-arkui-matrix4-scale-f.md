# scale

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

<a id="scale"></a>
## scale

```TypeScript
function scale(options: ScaleOption): Matrix4Transit
```

Matrix的缩放函数，可以为当前矩阵增加x轴/y轴/z轴缩放效果。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [scale](arkts-arkui-matrix4-matrix4transit-i.md#scale-1)

<!--Device-matrix4-function scale(options: ScaleOption): Matrix4Transit--><!--Device-matrix4-function scale(options: ScaleOption): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | 是 | 设置缩放参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 缩放后的矩阵对象。 |

