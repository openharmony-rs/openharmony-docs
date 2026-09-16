# combine

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## combine

```TypeScript
function combine(options: Matrix4Transit): Matrix4Transit
```

Matrix的叠加函数，可以将两个矩阵的效果叠加起来作用于当前矩阵。会改变调用该函数的原始矩阵。

> **说明：** 
> 
> matrixA.combine(matrixB)与matrixB.combine(matrixA)的变换结果不同。combine()的调用顺序决定了变换的叠加顺序，例如先平移后缩放与先缩放后平移的变换效果不同。使用时需根据预期
> 的变换效果选择正确的调用顺序。如需保留原始矩阵不被修改，应先调用copy()再调用combine()，例如：matrixA.copy().combine(matrixB)。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [combine](arkts-arkui-matrix4-matrix4transit-i.md#combine)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 是 | 待叠加的矩阵对象，其变换效果将与单位矩阵进行叠加。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 叠加后的矩阵对象。 |
