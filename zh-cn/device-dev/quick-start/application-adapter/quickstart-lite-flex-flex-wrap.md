# flex-wrap CSS能力开发指南

## 概述

flex-wrap用于设置flex容器内子元素在**主轴方向排满后是否换行**：不换行（单行）或换行（多行）。主轴方向由flex-direction决定。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| nowrap（默认值） | 不换行，子元素在主轴方向单行排列；排满后继续按序排列，可能溢出容器 |
| wrap | 换行：row时水平排满后向下换行，column时垂直排满后向右换列 |

不设置flex-wrap时，容器按默认值nowrap单行排列。

> **说明：**
>
> nowrap模式下子元素超出容器主轴尺寸时不会被自动压缩，超出部分会溢出容器（是否可见由容器overflow相关能力决定）。如需多行排布请显式设置wrap。

### Native接口

JS应用的flex-wrap CSS属性，在引擎层对应ui_lite的FlexLayout（div / list-item的底层布局实现）。Native（C++）开发可直接使用以下接口控制换行：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| FlexLayout::SetFlexWrap | uint8_t wrap：FlexLayout::NOWRAP（默认）/ FlexLayout::WRAP | 无（void） | 设置主轴排满后是否换行。仅更新标记，需再调用LayoutChildren()重新布局、Invalidate()刷新显示 |

FlexLayout换行取值常量（`layout/flex_layout.h`）：

| 常量 | 数值 | 含义 |
| --- | --- | --- |
| FlexLayout::NOWRAP | 0 | 不换行（对应CSS nowrap） |
| FlexLayout::WRAP | 1 | 换行（对应CSS wrap） |

涉及的头文件：

```cpp
#include "layout/flex_layout.h"   // OHOS::FlexLayout
#include "layout/layout.h"        // OHOS::LAYOUT_HOR / LAYOUT_VER
```

### 与其他flex属性的关系

- flex-wrap的换行方向跟随主轴：row → 向下换行，column → 向右换列；
- 换行后形成多条"行"（flex line），justify-content在每行内独立生效；
- align-items在每行的交叉轴范围内生效；配合align-items: stretch时，子元素拉伸到**所在行**的交叉轴尺寸，而非整个容器的交叉轴尺寸；
- align-content与row-gap只在flex-wrap: wrap时生效：nowrap模式下设置align-content不会产生多行分布效果，row-gap也不会产生行间距。

## 使用示例

### JS使用示例

#### nowrap单行排列（默认）

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red"></div>
    <div class="item item-green"></div>
    <div class="item item-blue"></div>
</div>
```

```css
/* index.css */
.container {
    flex-direction: row;
    flex-wrap: nowrap; /* 默认值，可不写 */
    width: 300px;
}

.item {
    width: 130px;
    height: 60px;
}

.item-red {
    background-color: #e74c3c;
}

.item-green {
    background-color: #2ecc71;
}

.item-blue {
    background-color: #3498db;
}
```

预期效果：三个130px宽的色块在300px宽容器内单行排列，蓝色块超出容器部分溢出。

![nowrap单行排列效果](../figures/flex-flex-wrap-nowrap.png)

#### wrap多行排列

```css
.container {
    flex-direction: row;
    flex-wrap: wrap; /* 排满后向下换行 */
    width: 300px;
}
```

预期效果：红、绿色块在第一行，蓝色块换到第二行。

![wrap多行排列效果](../figures/flex-flex-wrap-wrap.png)

#### column方向下换列

```css
.container {
    flex-direction: column; /* 主轴：垂直 */
    flex-wrap: wrap;        /* 排满后向右换列 */
    height: 200px;
}

.item {
    width: 100px;
    height: 90px;
}
```

预期效果：垂直方向排满后，蓝色块在红、绿色块右侧另起一列。

![column方向换列效果](../figures/flex-flex-wrap-column.png)

### Native接口使用示例

#### nowrap单行排列（NOWRAP，默认）

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"      // OHOS::Color（设置背景色用）

// 创建 flex 容器（FlexLayout 本身即容器视图，直接挂载子视图）
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 300, 100);            // 容器位置和大小：x, y, width, height
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);   // 主轴：水平
layout->SetFlexWrap(OHOS::FlexLayout::NOWRAP);  // 默认值，可不写

// 添加三个 130px 宽的子元素（分别设置红、绿、蓝背景色，总宽超过容器宽 300px）
OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(130, 60);
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);
OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(130, 60);
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);
OHOS::UIView* viewC = new OHOS::UIView();
viewC->Resize(130, 60);
viewC->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Blue().full);
layout->Add(viewA);
layout->Add(viewB);
layout->Add(viewC);

layout->LayoutChildren(); // 触发布局
layout->Invalidate();     // 触发重绘
```

预期效果：红、绿、蓝三个子视图单行排列，蓝色子视图超出容器部分溢出。

![NOWRAP单行排列效果](../figures/flex-flex-wrap-nowrap.png)

#### wrap多行排列（WRAP）

```cpp
layout->SetFlexWrap(OHOS::FlexLayout::WRAP);  // 排满后向下换行
layout->LayoutChildren();
layout->Invalidate();
```

预期效果：红、绿色子视图在第一行，蓝色子视图换到第二行。

![WRAP多行排列效果](../figures/flex-flex-wrap-wrap.png)

## 约束

### CSS取值约束

以下为 **CSS属性侧**的取值约束：JS页面（HML/CSS）中flex-wrap仅支持nowrap / wrap两个值，**不支持** W3C标准中的以下值：

| 不支持的值 | 说明 |
| --- | --- |
| wrap-reverse | 反向换行，当前不支持 |

如需反向换行视觉效果，请调整HML中子元素的书写顺序。


