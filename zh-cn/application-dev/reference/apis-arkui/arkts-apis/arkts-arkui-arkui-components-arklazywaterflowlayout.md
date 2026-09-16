# @ohos.arkui.components.ArkLazyWaterFlowLayout

## 导入模块

```TypeScript
import { LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute, LazyWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [LazyVWaterFlowLayoutAttribute](arkts-arkui-arkui-components-arklazywaterflowlayout-lazyvwaterflowlayoutattribute-c.md) | 定义懒加载垂直瀑布流布局属性。 |
| [LazyWaterFlowLayoutAttribute](arkts-arkui-arkui-components-arklazywaterflowlayout-lazywaterflowlayoutattribute-c.md) | 定义懒加载瀑布流布局属性。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [LazyVWaterFlowLayoutInterface](arkts-arkui-arkui-components-arklazywaterflowlayout-lazyvwaterflowlayoutinterface-i.md) | 定义懒加载垂直瀑布流布局组件。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [LazyVWaterFlowLayout](arkts-arkui-arkui-components-arklazywaterflowlayout-con.md#lazyvwaterflowlayout) | 定义LazyVWaterFlowLayout组件。 |
| [LazyVWaterFlowLayoutInstance](arkts-arkui-arkui-components-arklazywaterflowlayout-con.md#lazyvwaterflowlayoutinstance) | 定义LazyVWaterFlowLayout组件实例。 |

## 示例

```TypeScript
### 示例1（实现懒加载瀑布流布局）

通过[Scroll](ts-container-scroll.md)和LazyVWaterFlowLayout组件实现懒加载瀑布流布局。

MyDataSource实现了LazyForEach数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给LazyVWaterFlowLayout提供子组件。

从API版本26.0.0开始，新增支持LazyVWaterFlowLayout组件。
```

```TypeScript

```

```TypeScript
### 示例2（设置头部组件或尾部组件及吸附效果）

该示例通过[Scroll](ts-container-scroll.md)嵌套LazyVWaterFlowLayout，并通过header、footer、sticky实现瀑布流顶部和底部吸附效果。滚动过程中header吸附在可视区域顶部，footer吸附在可视区域底部。

从API版本26.0.0开始，新增支持header、footer和sticky属性。


```

```TypeScript
### 示例3（设置自适应列数）

该示例通过columnsTemplate设置repeat(auto-fill, track-size)和ItemFillPolicy，实现LazyVWaterFlowLayout列数自适应。

从API版本26.0.0开始，新增columnsTemplate接口。
```
