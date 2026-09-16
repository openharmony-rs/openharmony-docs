# @ohos.arkui.components.ArkDynamicLayout

## 导入模块

```TypeScript
import { DynamicLayout, DynamicLayoutAttribute } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [DynamicLayoutAttribute](arkts-arkui-arkui-components-arkdynamiclayout-dynamiclayoutattribute-c.md) | 支持[通用属性](../arkts-components/arkts-arkui-commonmethod-c.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DynamicLayoutInterface](arkts-arkui-arkui-components-arkdynamiclayout-dynamiclayoutinterface-i.md) | 动态布局容器组件，支持在运行时动态切换不同的布局算法，不改变子组件的状态。使用DynamicLayout可以提升布局灵活性，简化界面适配和多视图切换的开发流程。适用于响应式布局（适配不同屏幕尺寸）、多视图模式切换（如列表/网格/瀑布流切换）、用户自定义布局等场景。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [DynamicLayout](arkts-arkui-arkui-components-arkdynamiclayout-con.md#dynamiclayout) | 动态布局容器组件，支持在运行时动态切换不同的布局算法，不改变子组件的状态。 |
| [DynamicLayoutInstance](arkts-arkui-arkui-components-arkdynamiclayout-con.md#dynamiclayoutinstance) | Defines DynamicLayout Component instance. |

## 示例

```TypeScript
### 示例1（自定义布局算法实现瀑布流布局）

该示例展示如何重写onMeasure、onLayout函数，实现瀑布流布局展示商品列表的功能。瀑布流布局通过测量阶段计算子组件高度并记录每列累计高度，在布局阶段将子组件分配到当前高度最小的列，实现自动填充效果。

从API version 24开始，新增onMeasure、onLayout。


```

```TypeScript
### 示例2（切换布局算法）

该示例通过改变[@Local](../../../ui/state-management/arkts-new-local.md)装饰的LayoutAlgorithm类型变量，实现动态切换DynamicLayout组件布局算法的功能。示例展示如何切换布局算法为RowLayoutAlgorithm（水平线性布局）、ColumnLayoutAlgorithm（垂直线性布局）、StackLayoutAlgorithm（堆叠布局）和GridLayoutAlgorithm（网格布局）。

> 说明：
> 
> 示例中预置的layoutGravity属性仅在Stack布局算法下生效，在Row/Column布局算法下该属性不生效。

从API version 24开始，新增RowLayoutAlgorithm、ColumnLayoutAlgorithm、StackLayoutAlgorithm、GridLayoutAlgorithm。


```

```TypeScript
### 示例3（修改布局算法属性）

该示例通过修改RowLayoutAlgorithm的space和justifyContent属性，实现DynamicLayout组件布局效果刷新的功能。

从API version 24开始，新增space、justifyContent属性。
```
