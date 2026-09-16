# @ohos.matrix4(矩阵变换)

用于对组件进行图形变换的各种操作，为组件提供矩阵变换能力，支持对图形进行平移、旋转和缩放等。

Matrix4的使用场景包括：

图形变换中的transform接口通过使用图形变换矩阵Matrix4对象设置组件的二维变换矩阵，[transform3D](../arkts-components/arkts-arkui-commonmethod-c.md#transform3d)接口通过使用图形变换矩阵Matrix4对象设置组件的三维变换矩阵。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [combine](arkts-arkui-matrix4-combine-f.md) | Matrix的叠加函数，可以将两个矩阵的效果叠加起来作用于当前矩阵。会改变调用该函数的原始矩阵。 |
| [copy](arkts-arkui-matrix4-copy-f.md) | Matrix的拷贝函数，可以拷贝一份当前的矩阵对象。 |
| [identity](arkts-arkui-matrix4-identity-f.md) | Matrix的初始化函数，可以返回一个初始的单位矩阵对象，可作为后续矩阵变换操作的基础。 |
| [init](arkts-arkui-matrix4-init-f.md) | Matrix的构造函数，可以通过传入的参数创建一个四阶矩阵，矩阵为列优先，即输入数组的16个值按列依次填充至矩阵：array[0]~array[3]为第1列，array[4]~array[7]为第2列，array[8]~array [11]为第3列，array[12]~array[15]为第4列。当仅需单位矩阵时，推荐使用matrix4.identity()。 |
| [invert](arkts-arkui-matrix4-invert-f.md) | Matrix的逆函数，可以返回一个当前矩阵对象的逆矩阵，即效果正好相反。会改变调用该函数的原始矩阵。 |
| [rotate](arkts-arkui-matrix4-rotate-f.md) | Matrix的旋转函数，可以为当前矩阵增加x轴/y轴/z轴旋转效果。会改变调用该函数的原始矩阵。 |
| [scale](arkts-arkui-matrix4-scale-f.md) | Matrix的缩放函数，可以为当前矩阵增加x轴/y轴/z轴缩放效果。会改变调用该函数的原始矩阵。 |
| [transformPoint](arkts-arkui-matrix4-transformpoint-f.md) | Matrix的坐标点转换函数，可以将当前的变换效果作用到一个坐标点上。 |
| [translate](arkts-arkui-matrix4-translate-f.md) | Matrix的平移函数，可以为当前矩阵增加x轴/y轴/z轴平移效果。会改变调用该函数的原始矩阵。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 矩阵对象。支持通过链式调用translate、scale、rotate、skew等方法组合多种变换效果。 |
| [Point](arkts-arkui-matrix4-point-i.md) | 坐标点的数据结构。 |
| [PolyToPolyOptions](arkts-arkui-matrix4-polytopolyoptions-i.md) | 多边形到多边形的映射选项。 |
| [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | 旋转参数。 |
| [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | 缩放参数。 |
| [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | 平移参数。 |
