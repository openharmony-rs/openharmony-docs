# DynamicLayoutInterface

动态布局容器组件，支持在运行时动态切换不同的布局算法，不改变子组件的状态。使用DynamicLayout可以提升布局灵活性，简化界面适配和多视图切换的开发流程。适用于响应式布局（适配不同屏幕尺寸）、多视图模式切换（如列表/网格/瀑布流切换）、用户自定义布局等场景。

## 子组件

可以包含子组件。

**起始版本：** 24

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DynamicLayout, DynamicLayoutAttribute } from '@kit.ArkUI';
```

## [[Call]]

```TypeScript
(algorithm: LayoutAlgorithm): DynamicLayoutAttribute
```

动态布局容器。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithm | [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md) | 是 | 指定动态布局容器的布局算法。支持使用[RowLayoutAlgorithm](arkts-arkui-layoutalgorithm-rowlayoutalgorithm-c.md)（水平线性布局，适用于水平排列场景）、[ColumnLayoutAlgorithm](arkts-arkui-layoutalgorithm-columnlayoutalgorithm-c.md)（垂直线性布局，适用于垂直排列场景）、[StackLayoutAlgorithm](arkts-arkui-layoutalgorithm-stacklayoutalgorithm-c.md)（堆叠布局，适用于层叠覆盖场景）、[GridLayoutAlgorithm](arkts-arkui-layoutalgorithm-gridlayoutalgorithm-c.md)（网格布局，适用于规整网格场景）和[CustomLayoutAlgorithm](arkts-arkui-layoutalgorithm-customlayoutalgorithm-c.md)（自定义布局，适用于复杂特殊布局场景）等布局算法实例，详见[LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)。取非法值（如null、undefined或无效的布局算法对象）时，按照[StackLayoutAlgorithm](arkts-arkui-layoutalgorithm-stacklayoutalgorithm-c.md)布局子组件，子组件堆叠排列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DynamicLayoutAttribute](arkts-arkui-arkui-components-arkdynamiclayout-dynamiclayoutattribute-c.md) |  |
