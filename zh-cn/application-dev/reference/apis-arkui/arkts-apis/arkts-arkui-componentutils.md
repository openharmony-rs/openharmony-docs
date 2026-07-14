# @ohos.arkui.componentUtils

提供获取组件绘制区域坐标和大小的能力。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getRectangleById](arkts-arkui-getrectanglebyid-f.md#getrectanglebyid-1) | 根据组件ID获取组件实例对象，通过组件实例对象将获取的坐标位置和大小同步返回给开发者。@link @ohos.arkui.UIContext}中的&gt; [getComponentUtils](arkts-arkui-uicontext-c.md#getcomponentutils-1)方法获取当前UI上下&gt; 文关联的[ComponentUtils](arkts-arkui-componentutils-c.md)对象。在目标组件布局完成后，通过该接口能够获取组件坐标和尺寸信息。建议在&gt; [布局回调](arkts-arkui-inspector.md)中使用该接口。如果组件动态创建但未挂载组件树，则无法通过该接口获取正常的组件信息。因为组件在未挂载组件树的情况下，一般未经过UI框架正常&gt; 的测量与布局，此时请确保组件正常挂载组件树后再尝试获取组件信息。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getItemsInShapePath](arkts-arkui-getitemsinshapepath-f-sys.md#getitemsinshapepath-1) | 获取位于选定区域内的图像对象。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComponentInfo](arkts-arkui-componentinfo-i.md) | 组件大小、位置、平移缩放旋转及仿射矩阵属性信息。 |
| [Offset](arkts-arkui-offset-i.md) | 定义坐标属性。 |
| [RotateResult](arkts-arkui-rotateresult-i.md) | 旋转信息。 |
| [ScaleResult](arkts-arkui-scaleresult-i.md) | 缩放信息。 |
| [Size](arkts-arkui-size-i.md) | 定义尺寸属性。 |
| [TranslateResult](arkts-arkui-translateresult-i.md) | 平移信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [GetItemsInShapePathParams](arkts-arkui-getitemsinshapepathparams-i-sys.md) | 需要获取图像对象时设置的图像选项。 |
| [ImageItem](arkts-arkui-imageitem-i-sys.md) | 带有布局信息的图像对象。 |
| [Rotation2D](arkts-arkui-rotation2d-i-sys.md) | 描述二维空间中的旋转，可以通过旋转角度和旋转中心来定义。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [Matrix4Result](arkts-arkui-matrix4result-t.md) | 列优先四阶矩阵。 |

