# DynamicLayout
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

动态布局容器组件，支持在运行时动态切换不同的布局算法，不改变子组件的状态。

> **说明：**
>
> 该组件从API version 24开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 子组件

可以包含子组件。

## 接口

DynamicLayout(algorithm: LayoutAlgorithm)  

动态布局容器。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| algorithm | [LayoutAlgorithm](#layoutalgorithm) | 是 | 指定动态布局组件的布局算法。取非法值时，按照[堆叠布局算法](#stacklayoutalgorithm)布局子组件，子组件堆叠排列。|

## 属性

支持[通用属性](ts-component-general-attributes.md)，当布局算法为[StackLayoutAlgorithm](#stacklayoutalgorithm)时，子组件设置[layoutGravity](ts-universal-attributes-location.md#layoutgravity20)属性生效。

## 事件

支持[通用事件](ts-component-general-events.md)。

## LayoutAlgorithm

动态布局容器的布局算法基础类型。

> **说明：**
>
> 该类型变量可以赋值具体的布局算法类对象，如[CustomLayoutAlgorithm](#customlayoutalgorithm)类对象、[RowLayoutAlgorithm](#rowlayoutalgorithm)类对象等。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CustomLayoutAlgorithm

自定义布局算法类。

> **说明：**
>
> CustomLayoutAlgorithm类对象可以赋值给[LayoutAlgorithm](#layoutalgorithm)类型变量，作为DynamicLayout组件的入参指定布局算法。

**装饰器类型：** \@ObservedV2

### onMeasure
onMeasure(self: FrameNode, constraint: LayoutConstraint): void

通过重写此函数，开发者可以自定义测量子组件的大小。ArkUI框架会在动态布局组件确定尺寸时，将该组件对应的FrameNode和布局约束通过onMeasure传递给开发者。不允许在onMeasure函数中改变状态变量。

> **说明：**
>
> 在此函数中，开发者可以调用[FrameNode](../js-apis-arkui-frameNode.md#framenode-1)的[getChild()](../js-apis-arkui-frameNode.md#getchild12)方法获取子组件FrameNode，调用[FrameNode](../js-apis-arkui-frameNode.md#framenode-1)的[measure()](../js-apis-arkui-frameNode.md#measure12)方法测量子组件大小，参考[示例1（自定义布局算法实现瀑布流布局）](#示例1自定义布局算法实现瀑布流布局)。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| self | [FrameNode](../js-apis-arkui-frameNode.md#framenode-1) | 是 | 动态布局组件在组件树上的实体节点。|
| constraint | [LayoutConstraint](../js-apis-arkui-frameNode.md#layoutconstraint12) | 是 | 动态布局组件进行测量时使用的布局约束。|

### onLayout
onLayout(self: FrameNode, position: Position): void

通过重写此函数，开发者可以自定义排列子组件的位置。ArkUI框架会在动态布局组件确定位置时，将该组件对应的FrameNode和布局位置通过onLayout传递给开发者。不允许在onLayout函数中改变状态变量。

> **说明：**
>
> 在此函数中，开发者可以调用[FrameNode](../js-apis-arkui-frameNode.md#framenode-1)的[getChild()](../js-apis-arkui-frameNode.md#getchild12)方法获取子组件FrameNode，调用[FrameNode](../js-apis-arkui-frameNode.md#framenode-1)的[layout()](../js-apis-arkui-frameNode.md#layout12)方法设置子组件位置，参考[示例1（自定义布局算法实现瀑布流布局）](#示例1自定义布局算法实现瀑布流布局)。

**模型约束：** 此接口仅可在Stage模型下使用。
  
**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| self | [FrameNode](../js-apis-arkui-frameNode.md#framenode-1) | 是 | 动态布局组件在组件树上的实体节点。|
| position | [Position](../js-apis-arkui-graphics.md#position) | 是 | 动态布局组件进行布局时使用的位置信息。|

## RowLayoutAlgorithm

水平方向线性布局算法类。

> **说明：**
>
> RowLayoutAlgorithm类对象可以赋值给[LayoutAlgorithm](#layoutalgorithm)类型变量，作为DynamicLayout组件的入参指定布局算法。

**装饰器类型：** \@ObservedV2

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 横向布局元素水平方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |
| alignItems | [VerticalAlign](ts-appendix-enums.md#verticalalign) | 否 | 是 | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：VerticalAlign.Center <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |
| justifyContent | [FlexAlign](ts-appendix-enums.md#flexalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |
|isReverse| boolean | 否 | 是 | 子组件在水平方向上的排列是否反转。取值为true表示子组件在水平方向上反转排列，由于水平方向受通用属性[direction](ts-universal-attributes-location.md#direction)影响，如果[direction](ts-universal-attributes-location.md#direction)属性生效，再做一次反转。取值为false表示子组件在水平方向上正序排列。<br/>默认值：false <br> 非法值：按默认值处理。<br/>装饰器类型：@Trace |

### constructor

constructor(option?: RowLayoutAlgorithmOptions)

水平方向线性布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [RowLayoutAlgorithmOptions](#rowlayoutalgorithmoptions对象说明) | 否 | 水平方向线性布局算法的构造入参，设置布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。|

## RowLayoutAlgorithmOptions对象说明

设置水平方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 横向布局元素水平方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|
| alignItems | [VerticalAlign](ts-appendix-enums.md#verticalalign) | 否 | 是 | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：VerticalAlign.Center <br/> 非法值：按默认值处理。|
| justifyContent | [FlexAlign](ts-appendix-enums.md#flexalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。|
| isReverse | boolean | 否 | 是 | 子组件在水平方向上的排列是否反转。取值为true表示子组件在水平方向上反转排列，由于水平方向受通用属性[direction](ts-universal-attributes-location.md#direction)影响，如果[direction](ts-universal-attributes-location.md#direction)属性生效，再做一次反转。取值为false表示子组件在水平方向上正序排列。<br/>默认值：false <br> 非法值：按默认值处理。|

## ColumnLayoutAlgorithm

垂直方向线性布局算法类。

> **说明：**
>
> ColumnLayoutAlgorithm类对象可以赋值给[LayoutAlgorithm](#layoutalgorithm)类型变量，作为DynamicLayout组件的入参指定布局算法。

**装饰器类型：** \@ObservedV2

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 纵向布局元素垂直方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |
| alignItems | [HorizontalAlign](ts-appendix-enums.md#horizontalalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：HorizontalAlign.Center <br/>  非法值：按默认值处理。<br/>装饰器类型：@Trace |
| justifyContent | [FlexAlign](ts-appendix-enums.md#flexalign) | 否 | 是 | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |
| isReverse | boolean | 否 | 是 | 子组件在垂直方向上的排列是否反转。取值为true表示子组件在垂直方向上反转排列。取值为false表示子组件在垂直方向上正序排列。<br/>默认值：false <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |

### constructor 

constructor(option?: ColumnLayoutAlgorithmOptions)

垂直方向线性布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [ColumnLayoutAlgorithmOptions](#columnlayoutalgorithmoptions对象说明) | 否 | 垂直方向线性布局算法的构造入参，设置布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。|

## ColumnLayoutAlgorithmOptions对象说明

设置垂直方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 纵向布局元素垂直方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|
| alignItems | [HorizontalAlign](ts-appendix-enums.md#horizontalalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：HorizontalAlign.Center <br/>  非法值：按默认值处理。|
| justifyContent | [FlexAlign](ts-appendix-enums.md#flexalign) | 否 | 是  | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。|
| isReverse | boolean | 否 | 是 | 子组件在垂直方向上的排列是否反转。取值为true表示子组件在垂直方向上反转排列。取值为false表示子组件在垂直方向上正序排列。<br/>默认值：false <br/> 非法值：按默认值处理。|

## StackLayoutAlgorithm

堆叠布局算法类。

> **说明：**
>
> StackLayoutAlgorithm类对象可以赋值给[LayoutAlgorithm](#layoutalgorithm)类型变量，作为DynamicLayout组件的入参指定布局算法。


**装饰器类型：** \@ObservedV2

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| alignContent | [LocalizedAlignment](ts-appendix-enums.md#localizedalignment20) | 否 | 是 | 设置子组件在堆叠布局算法中对齐格式。 <br/> 默认值：LocalizedAlignment.CENTER <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |

### constructor

constructor(option?: StackLayoutAlgorithmOptions)

堆叠布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [StackLayoutAlgorithmOptions](#stacklayoutalgorithmoptions对象说明) | 否 | 堆叠布局算法的构造入参，设置九宫格对齐格式。|

## StackLayoutAlgorithmOptions对象说明

设置堆叠布局算法的对齐方式。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| alignContent | [LocalizedAlignment](ts-appendix-enums.md#localizedalignment20) | 否 | 是 | 设置子组件在堆叠布局算法中对齐格式。<br/> 默认值：LocalizedAlignment.CENTER <br/> 非法值：按默认值处理。|

## GridLayoutAlgorithm

网格布局算法类。

> **说明：**
>
> GridLayoutAlgorithm类对象可以赋值给[LayoutAlgorithm](#layoutalgorithm)类型变量，作为DynamicLayout组件的入参指定布局算法。

**装饰器类型：** \@ObservedV2

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./ts-types.md#itemfillpolicy22) | 否 | 是 | 设置当前网格布局的列数。<br/> 默认值：'1fr' <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |
| columnsGap | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 列与列之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |
| rowsGap | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 行与行之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：@Trace |

### constructor

constructor(option?: GridLayoutAlgorithmOptions)

网格布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [GridLayoutAlgorithmOptions](#gridlayoutalgorithmoptions对象说明) | 否 | 网格布局算法的构造入参，设置网格布局的列数、列间距、行间距。|

## GridLayoutAlgorithmOptions对象说明

设置网格布局算法的列数模板、列间距、行间距。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./ts-types.md#itemfillpolicy22) | 否 | 是 | 设置当前网格布局的列数。<br/> 默认值：'1fr' <br/> 非法值：按默认值处理。|
| columnsGap | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 列与列之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|
| rowsGap | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 行与行之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|

## 示例

### 示例1（自定义布局算法实现瀑布流布局）

该示例展示如何重写[onMeasure](#onmeasure)、[onLayout](#onlayout)函数，实现瀑布流布局展示商品列表的功能。

从API version 24开始，新增onMeasure、onLayout。

```typescript
import { DynamicLayout, DynamicLayoutAttribute, CustomLayoutAlgorithm, LayoutAlgorithm, FrameNode, LayoutConstraint, Position } from '@kit.ArkUI';

// 瀑布流布局算法
class WaterfallLayout extends CustomLayoutAlgorithm {
  private columnCount: number = 2;
  private columnGap: number = 10;
  private rowGap: number = 10;

  onMeasure(self: FrameNode, constraint: LayoutConstraint): void {
    const childCount = self.getChildrenCount();
    const columnWidth = (constraint.maxSize.width - (this.columnCount - 1) * this.columnGap) / this.columnCount;

    // 记录每列的当前高度
    const columnHeights: number[] = new Array(this.columnCount).fill(0);

    for (let i = 0; i < childCount; i++) {
      const child = self.getChild(i);
      if (child) {
        // 通过将minSize和maxSize设置为相同值来约束子组件宽度
        const childConstraint: LayoutConstraint = {
          maxSize: {
            width: columnWidth,
            height: constraint.maxSize.height
          },
          minSize: {
            width: columnWidth,
            height: 0
          },
          percentReference: constraint.percentReference
        };

        child.measure(childConstraint);

        // 找到当前高度最小的列
        const minColumn = columnHeights.indexOf(Math.min(...columnHeights));
        columnHeights[minColumn] += child.getMeasuredSize().height + this.rowGap;
      }
    }

    const maxHeight = Math.max(...columnHeights);
    self.setMeasuredSize({
      width: constraint.maxSize.width,
      height: maxHeight
    });
  }

  onLayout(self: FrameNode, position: Position): void {
    const childCount = self.getChildrenCount();
    const measuredSize = self.getMeasuredSize();
    const columnWidth = (measuredSize.width - (this.columnCount - 1) * this.columnGap) / this.columnCount;

    // 记录每列的当前Y坐标
    const columnYs: number[] = new Array(this.columnCount).fill(0);

    for (let i = 0; i < childCount; i++) {
      const child = self.getChild(i);
      if (child) {
        const childSize = child.getMeasuredSize();

        // 找到当前Y坐标最小的列
        const minColumn = columnYs.indexOf(Math.min(...columnYs));
        const x = minColumn * (columnWidth + this.columnGap);
        const y = columnYs[minColumn];

        child.layout({ x, y });

        columnYs[minColumn] += childSize.height + this.rowGap;
      }
    }

    self.setLayoutPosition(position);
  }
}

@Entry
@ComponentV2
struct WaterfallLayoutExample {
  @Local algorithm: LayoutAlgorithm = new WaterfallLayout();

  // 商品数据
  private products: Product[] = [
    { id: '1', name: '时尚运动鞋', price: '¥399', height: 180, image: '商品图' },
    { id: '2', name: '休闲双肩包', price: '¥259', height: 220, image: '商品图' },
    { id: '3', name: '无线蓝牙耳机', price: '¥599', height: 150, image: '商品图' },
    { id: '4', name: '智能手表', price: '¥1299', height: 200, image: '商品图' },
    { id: '5', name: '太阳眼镜', price: '¥199', height: 130, image: '商品图' },
    { id: '6', name: '便携充电宝', price: '¥129', height: 170, image: '商品图' },
    { id: '7', name: '机械键盘', price: '¥459', height: 160, image: '商品图' },
    { id: '8', name: '游戏鼠标', price: '¥189', height: 140, image: '商品图' },
    { id: '9', name: '高清显示器', price: '¥1599', height: 210, image: '商品图' },
    { id: '10', name: '智能音箱', price: '¥299', height: 190, image: '商品图' }
  ];

  // 商品卡片组件
  @Builder ProductCard(product: Product) {
    Column() {
      Text(product.image)
        .fontSize(18)
        .margin({ bottom: 8 })
      Text(product.name)
        .fontSize(14)
        .fontWeight(FontWeight.Medium)
        .fontColor(0x333333)
        .margin({ bottom: 4 })
        .maxLines(1)
        .textOverflow({ overflow: TextOverflow.Ellipsis })
      Text(product.price)
        .fontSize(16)
        .fontColor(0xFF6B35)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .padding(12)
    .backgroundColor(0xFAFAFA)
    .borderRadius(8)
    .border({ width: 1, color: 0xE0E0E0 })
    .height(product.height)
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Text('商品列表 - 瀑布流布局')
        .fontSize(18)
        .fontWeight(FontWeight.Bold)
        .margin({ bottom: 20 })

      Scroll() {
        DynamicLayout(this.algorithm) {
          ForEach(this.products, (product: Product) => {
            this.ProductCard(product)
          })
        }
        .width('100%')
        .backgroundColor(0xEFEFEF)
        .borderRadius(12)
        .padding(10)
      }
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.Auto)
      .edgeEffect(EdgeEffect.Spring)
      .width('100%')
      .layoutWeight(1)

      Text('商品卡片自动分配到高度最小的列')
        .fontSize(14)
        .fontColor(Color.Gray)
        .margin({ top: 12 })
    }
    .padding(20)
    .width('100%')
    .height('100%')
  }
}

// 商品数据模型
interface Product {
  id: string;
  name: string;
  price: string;
  height: number;
  image: string;
}
```
![](figures/dynamiclayout_waterflow_customlayout.png)

### 示例2（切换布局算法）

该示例通过改变[@Local](../../../ui/state-management/arkts-new-local.md)装饰的LayoutAlgorithm变量，实现动态切换DynamicLayout组件布局算法的功能。示例展示如何切换布局算法为[水平线性布局算法](#rowlayoutalgorithm)、[垂直线性布局算法](#columnlayoutalgorithm)、[堆叠布局算法](#stacklayoutalgorithm)和[网格布局算法](#gridlayoutalgorithm)。

从API version 24开始，新增RowLayoutAlgorithm、ColumnLayoutAlgorithm、StackLayoutAlgorithm、GridLayoutAlgorithm。

```typescript
import { DynamicLayout, DynamicLayoutAttribute, RowLayoutAlgorithm, ColumnLayoutAlgorithm, StackLayoutAlgorithm, GridLayoutAlgorithm, LayoutAlgorithm, LengthMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct LayoutSwitchExample {
  @Local algorithm: LayoutAlgorithm = new RowLayoutAlgorithm({
    space: LengthMetrics.vp(10),
    alignItems: VerticalAlign.Center
  });
  @Local childWidth: string = '20%'
  @Local childHeight: string = '20%'

  build() {
    Column() {
      // 使用状态变量控制布局算法
      DynamicLayout(this.algorithm) {
        Text('Item 1')
          .width(this.childWidth)
          .height(this.childHeight)
          .fontSize(14)
          .textAlign(TextAlign.Center)
          .backgroundColor(0xF5DEB3)
          .borderRadius(8)
          .layoutGravity(LocalizedAlignment.TOP_START)
        Text('Item 2')
          .width(this.childWidth)
          .height(this.childHeight)
          .fontSize(14)
          .textAlign(TextAlign.Center)
          .backgroundColor(0xF5DEB3)
          .borderRadius(8)
          .layoutGravity(LocalizedAlignment.TOP_END)
        Text('Item 3')
          .width(this.childWidth)
          .height(this.childHeight)
          .fontSize(14)
          .textAlign(TextAlign.Center)
          .backgroundColor(0xF5DEB3)
          .borderRadius(8)
          .layoutGravity(LocalizedAlignment.BOTTOM_START)
        Text('Item 4')
          .width(this.childWidth)
          .height(this.childHeight)
          .fontSize(14)
          .textAlign(TextAlign.Center)
          .backgroundColor(0xF5DEB3)
          .borderRadius(8)
          .layoutGravity(LocalizedAlignment.BOTTOM_END)
      }
      .width(300)
      .height(280)
      .backgroundColor(0xEFEFEF)
      .borderRadius(12)
      .padding(10)

      Column({ space: 10 }) {
        Row({ space: 10 }) {
          Button('Row布局')
            .fontSize(14)
            .onClick(() => {
              this.algorithm = new RowLayoutAlgorithm({
                space: LengthMetrics.vp(10),
                alignItems: VerticalAlign.Center
              });
              this.childWidth = '20%'
              this.childHeight = '20%'
            })
          Button('Column布局')
            .fontSize(14)
            .onClick(() => {
              this.algorithm = new ColumnLayoutAlgorithm({
                space: LengthMetrics.vp(10),
                alignItems: HorizontalAlign.Center
              });
              this.childWidth = '20%'
              this.childHeight = '20%'
            })
        }
        Row({ space: 10 }) {
          Button('Stack布局')
            .fontSize(14)
            .onClick(() => {
              this.algorithm = new StackLayoutAlgorithm({
                alignContent: LocalizedAlignment.CENTER
              });
              this.childWidth = '20%'
              this.childHeight = '20%'
            })
          Button('Grid布局')
            .fontSize(14)
            .onClick(() => {
              this.algorithm = new GridLayoutAlgorithm({
                columnsTemplate: '1fr 1fr',
                rowsGap: LengthMetrics.vp(5),
                columnsGap: LengthMetrics.vp(5)
              });
              this.childWidth = '100%'
              this.childHeight = '50%'
            })
        }
      }
      .margin({ top: 20 })
    }
    .padding(20)
  }
}
```
![](figures/dynamiclayout_change_flag.gif)

### 示例3（修改布局算法属性）

该示例通过修改[RowLayoutAlgorithm](#rowlayoutalgorithm)的space和justifyContent属性，实现DynamicLayout组件布局效果刷新的功能。

从API version 24开始，新增space、justifyContent属性。

```typescript
import { DynamicLayout, DynamicLayoutAttribute, RowLayoutAlgorithm, LengthMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct PropertyChangeExample {
  algorithm: RowLayoutAlgorithm = new RowLayoutAlgorithm({
    space: LengthMetrics.vp(10),
    justifyContent: FlexAlign.Start
  });

  build() {
    Column() {
      DynamicLayout(this.algorithm) {
        Text('Item 1')
          .width(60)
          .height(40)
          .fontSize(14)
          .backgroundColor(0xF5DEB3)
        Text('Item 2')
          .width(60)
          .height(40)
          .fontSize(14)
          .backgroundColor(0xD2B48C)
        Text('Item 3')
          .width(60)
          .height(40)
          .fontSize(14)
          .backgroundColor(0xF5DEB3)
      }
      .width('100%')
      .height(80)
      .backgroundColor(0xEFEFEF)

      Row({ space: 10 }) {
        Button('增加间距')
          .fontSize(14)
          .onClick(() => {
            // 修改space属性触发重新布局
            const currentSpace = this.algorithm.space?.value;
            this.algorithm.space = LengthMetrics.vp(currentSpace as number + 5);
          })
        Button('居中对齐')
          .fontSize(14)
          .onClick(() => {
            // 修改justifyContent属性触发重新布局
            this.algorithm.justifyContent = FlexAlign.Center;
          })
        Button('两端对齐')
          .fontSize(14)
          .onClick(() => {
            this.algorithm.justifyContent = FlexAlign.SpaceBetween;
          })
      }
      .margin({ top: 20 })
    }
    .padding(20)
  }
}
```
![](figures/dynamiclayout_change_property.gif)
