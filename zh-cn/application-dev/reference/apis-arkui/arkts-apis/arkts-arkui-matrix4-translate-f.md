# translate

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## translate

```TypeScript
function translate(options: TranslateOption): Matrix4Transit
```

Matrix的平移函数，可以为当前矩阵增加x轴/y轴/z轴平移效果。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [translate](arkts-arkui-matrix4-matrix4transit-i.md#translate-1)

<!--Device-matrix4-function translate(options: TranslateOption): Matrix4Transit--><!--Device-matrix4-function translate(options: TranslateOption): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | 是 | 设置平移参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 平移后的矩阵对象。 |

