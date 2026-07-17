# combine

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## combine

```TypeScript
function combine(options: Matrix4Transit): Matrix4Transit
```

Matrix的叠加函数，可以将两个矩阵的效果叠加起来生成一个新的矩阵对象。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [combine](arkts-arkui-matrix4-matrix4transit-i.md#combine-1)

<!--Device-matrix4-function combine(options: Matrix4Transit): Matrix4Transit--><!--Device-matrix4-function combine(options: Matrix4Transit): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 是 | 待叠加的矩阵对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 叠加后的矩阵对象。 |

