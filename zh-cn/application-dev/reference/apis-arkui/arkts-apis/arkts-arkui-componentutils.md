# @ohos.arkui.componentUtils

提供获取组件绘制区域坐标和大小的能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace componentUtils--><!--Device-unnamed-declare namespace componentUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getItemsInShapePath](arkts-arkui-componentutils-getitemsinshapepath-f-sys.md) | Get the image objects located within the selected area. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComponentInfo](arkts-arkui-componentutils-componentinfo-i.md) | 组件大小、位置、平移缩放旋转及仿射矩阵属性信息。 |
| [Offset](arkts-arkui-componentutils-offset-i.md) | 定义坐标属性。 |
| [RotateResult](arkts-arkui-componentutils-rotateresult-i.md) | 旋转信息。 |
| [ScaleResult](arkts-arkui-componentutils-scaleresult-i.md) | 缩放信息。 |
| [Size](arkts-arkui-componentutils-size-i.md) | 定义尺寸属性。 |
| [TranslateResult](arkts-arkui-componentutils-translateresult-i.md) | 平移信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [GetItemsInShapePathParams](arkts-arkui-componentutils-getitemsinshapepathparams-i-sys.md) | Image options setted when need to get the image objects. |
| [ImageItem](arkts-arkui-componentutils-imageitem-i-sys.md) | Image object with layout information. |
| [Rotation2D](arkts-arkui-componentutils-rotation2d-i-sys.md) | Describe a rotate in 2D, which can be defined by rotation angle and rotation center. |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [Matrix4Result](arkts-arkui-componentutils-matrix4result-t.md) | 列优先四阶矩阵。 |

