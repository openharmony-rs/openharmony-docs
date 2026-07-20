# rotate

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

<a id="rotate"></a>
## rotate

```TypeScript
function rotate(options: RotateOption): Matrix4Transit
```

Matrix的旋转函数，可以为当前矩阵增加x轴/y轴/z轴旋转效果。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [rotate](arkts-arkui-matrix4-matrix4transit-i.md#rotate-1)

<!--Device-matrix4-function rotate(options: RotateOption): Matrix4Transit--><!--Device-matrix4-function rotate(options: RotateOption): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | 是 | 设置旋转参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 旋转后的矩阵对象。 |

