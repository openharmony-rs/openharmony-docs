# GridRow

栅格布局可以为布局提供规律性的结构，解决多尺寸多设备的动态布局问题，保证不同设备上各个模块的布局一致性。

栅格容器组件，仅可以和栅格子组件(GridCol)在栅格布局场景中使用。

支持根据设备尺寸和断点动态调整列数与间距，实现响应式布局。

> **说明：** > > 该组件从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件

可以包含GridCol子组件。

## GridRow

```TypeScript
GridRow(option?: GridRowOptions)
```

栅格行布局容器。仅可以和栅格子组件在栅格布局场景中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridRowOptions](arkts-arkui-gridrowoptions-i.md) | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BreakPoints](arkts-arkui-breakpoints-i.md) | 设置栅格容器组件的断点。更多断点的说明参考[栅格容器断点](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)。 |
| [GridRowColumnOption](arkts-arkui-gridrowcolumnoption-i.md) | 栅格在不同宽度设备类型下的栅格列数配置。 |
| [GridRowOptions](arkts-arkui-gridrowoptions-i.md) | 设置栅格行布局容器的布局选项。 |
| [GridRowSizeOption](arkts-arkui-gridrowsizeoption-i.md) | 栅格在不同宽度设备类型下的gutter大小配置。 |
| [GutterOption](arkts-arkui-gutteroption-i.md) | 栅格布局间距类型，用于描述栅格子组件不同方向的间距。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BreakpointsReference](arkts-arkui-breakpointsreference-e.md) | 设置栅格容器组件的断点参照物。 |
| [GridRowDirection](arkts-arkui-gridrowdirection-e.md) | 栅格元素排列方向。 |

## 示例

```TypeScript
### 示例1（栅格布局的基本用法）

本示例展示GridRow组件的基本用法。


```

```TypeScript
### 示例2（AlignItems的基本用法）

本示例展示GridCol组件在不同alignItems对齐方式下的效果。
```
