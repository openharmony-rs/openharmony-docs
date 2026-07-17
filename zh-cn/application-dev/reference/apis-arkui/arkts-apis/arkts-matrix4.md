# @ohos.matrix4

用于对组件进行[图形变换](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)的各种操作，为组件提供矩阵变换能力，支持对图形进行平移、旋转和缩放等。

Matrix4的使用场景包括：

[图形变换](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)中的[transform](../arkts-components/arkts-arkui-common-commonmethod-c.md#transform-2)接口通过使用图形变换矩阵Matrix4对象显示二维变换时的矩阵变换，[transform3D](../arkts-components/arkts-arkui-common-commonmethod-c.md#transform3d-1)接口通过使用图形变换矩阵Matrix4对象设置组件的三维变换矩阵。

**起始版本：** 7

<!--Device-unnamed-declare namespace matrix4--><!--Device-unnamed-declare namespace matrix4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [combine](arkts-arkui-matrix4-combine-f.md#combine-1) | Matrix的叠加函数，可以将两个矩阵的效果叠加起来生成一个新的矩阵对象。 |
| [copy](arkts-arkui-matrix4-copy-f.md#copy-1) | Matrix的拷贝函数，可以拷贝一份当前的矩阵对象。 |
| [identity](arkts-arkui-matrix4-identity-f.md#identity-1) | Matrix的初始化函数，可以返回一个单位矩阵对象。 |
| [init](arkts-arkui-matrix4-init-f.md#init-1) | Matrix的构造函数，可以通过传入的参数创建一个四阶矩阵，矩阵为列优先。 |
| [invert](arkts-arkui-matrix4-invert-f.md#invert-1) | Matrix的逆函数，可以返回一个当前矩阵对象的逆矩阵，即效果正好相反。 |
| [rotate](arkts-arkui-matrix4-rotate-f.md#rotate-1) | Matrix的旋转函数，可以为当前矩阵增加x轴/y轴/z轴旋转效果。 |
| [scale](arkts-arkui-matrix4-scale-f.md#scale-1) | Matrix的缩放函数，可以为当前矩阵增加x轴/y轴/z轴缩放效果。 |
| [transformPoint](arkts-arkui-matrix4-transformpoint-f.md#transformpoint-1) | Matrix的坐标点转换函数，可以将当前的变换效果作用到一个坐标点上。 |
| [translate](arkts-arkui-matrix4-translate-f.md#translate-1) | Matrix的平移函数，可以为当前矩阵增加x轴/y轴/z轴平移效果。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 矩阵对象。 |
| [Point](arkts-arkui-matrix4-point-i.md) | 坐标点的数据结构。 |
| [PolyToPolyOptions](arkts-arkui-matrix4-polytopolyoptions-i.md) | 多边形到多边形的映射选项。 |
| [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | 旋转参数。 |
| [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | 缩放参数。 |
| [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | 平移参数。 |

