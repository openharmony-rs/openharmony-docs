# @ohos.arkui.componentUtils

提供获取组件绘制区域坐标和大小的能力。

**起始版本：** 10

<!--Device-unnamed-declare namespace componentUtils--><!--Device-unnamed-declare namespace componentUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getRectangleById](arkts-arkui-componentutils-getrectanglebyid-f.md#getrectanglebyid) | 根据组件ID获取组件实例对象，通过组件实例对象将获取的坐标位置和大小同步返回给开发者。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getItemsInShapePath](arkts-arkui-componentutils-getitemsinshapepath-f-sys.md#getitemsinshapepath) | 获取位于选定区域内的图像对象。 |
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
| [GetItemsInShapePathParams](arkts-arkui-componentutils-getitemsinshapepathparams-i-sys.md) | 需要获取图像对象时设置的图像选项。 |
| [ImageItem](arkts-arkui-componentutils-imageitem-i-sys.md) | 带有布局信息的图像对象。 |
| [Rotation2D](arkts-arkui-componentutils-rotation2d-i-sys.md) | 描述二维空间中的旋转，可以通过旋转角度和旋转中心来定义。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [Matrix4Result](arkts-arkui-componentutils-matrix4result-t.md) | 列优先四阶矩阵。 |

