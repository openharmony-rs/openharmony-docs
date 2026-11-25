# justify-content CSS能力开发指南

## 概述

justify-content用于设置flex容器内子元素在**主轴方向**上的对齐与空白分配方式。主轴方向由flex-direction决定：row时主轴为水平方向，column时主轴为垂直方向。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| flex-start（默认值） | 子元素向主轴起点对齐 |
| flex-end | 子元素向主轴终点对齐 |
| center | 子元素在主轴方向居中 |
| space-between | 子元素两端对齐，元素之间间隔相等 |
| space-around | 子元素两侧间隔相等（元素之间的间隔是边缘间隔的两倍） |
| space-evenly | 子元素之间、元素与容器边缘的间隔全部相等 |

不设置justify-content时，容器按默认值flex-start排列。

> **说明：**
>
> space-between / space-around / space-evenly只有在主轴方向存在剩余空间时才有视觉效果；子元素恰好排满主轴时，三者表现与flex-start相同。

### Native接口

JS应用的justify-content CSS属性，在引擎层对应ui_lite的FlexLayout（div / list-item的底层布局实现）。Native（C++）开发可直接使用以下接口控制主轴对齐：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| FlexLayout::SetMajorAxisAlign | const AlignType& align：对齐常量 | 无（void） | 设置主轴方向的对齐与空白分配。仅更新对齐标记，需再调用LayoutChildren()重新布局、Invalidate()刷新显示 |

AlignType取值常量（`layout/layout.h`，类型为uint8_t）：

| 常量 | 数值 | 含义 |
| --- | --- | --- |
| ALIGN_START | 0 | 主轴起点对齐（对应CSS flex-start） |
| ALIGN_END | 1 | 主轴终点对齐（对应CSS flex-end） |
| ALIGN_CENTER | 2 | 主轴居中（对应CSS center） |
| ALIGN_EVENLY | 3 | 间隔全部相等（对应CSS space-evenly） |
| ALIGN_AROUND | 4 | 两侧间隔相等（对应CSS space-around） |
| ALIGN_BETWEEN | 5 | 两端对齐（对应CSS space-between） |

涉及的头文件：

```cpp
#include "layout/flex_layout.h"   // OHOS::FlexLayout
#include "layout/layout.h"        // OHOS::AlignType / ALIGN_START 等
```

### 与其他flex属性的关系

- justify-content始终作用于**主轴**：flex-direction: row时控制水平方向，flex-direction: column时控制垂直方向；
- 修改flex-direction后，justify-content的作用方向随之旋转；
- 交叉轴方向的对齐请使用align-items（见[《quickstart-lite-flex-align-items.md》](quickstart-lite-flex-align-items.md)）。

## 使用示例

### JS使用示例

#### 主轴居中

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
    justify-content: center; /* 子元素整体水平居中 */
}

.item {
    width: 100px;
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

预期效果：红、绿、蓝三个色块作为一个整体在容器水平方向居中。

![主轴居中效果](../figures/flex-justify-content-center.png)

#### space-between两端对齐（工具栏常用）

```html
<!-- index.hml -->
<div class="toolbar">
    <div class="item item-red"></div>
    <div class="item item-green"></div>
    <div class="item item-blue"></div>
</div>
```

```css
/* index.css */
.toolbar {
    flex-direction: row;
    justify-content: space-between; /* 左右贴边，中间均分 */
    width: 100%;
    height: 60px;
}

.item {
    width: 120px;
    height: 40px;
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

预期效果：红色块靠左、蓝色块靠右、绿色块在中间，间距自动均分。

![space-between两端对齐效果](../figures/flex-justify-content-space-between.png)

#### column方向下使用

```css
.container {
    flex-direction: column;        /* 主轴：垂直 */
    justify-content: space-evenly; /* 垂直方向间隔均分 */
    height: 100%;
}
```

预期效果：各子元素在垂直方向均匀分布（含首尾与容器边缘的间隔）。

![space-evenly间隔均分效果](../figures/flex-justify-content-space-evenly.png)

### Native接口使用示例

#### 主轴居中（ALIGN_CENTER）

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"      // OHOS::Color（设置背景色用）

// 创建 flex 容器（FlexLayout 本身即容器视图，直接挂载子视图）
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 300, 100);            // 容器位置和大小：x, y, width, height
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);   // 主轴：水平
layout->SetMajorAxisAlign(OHOS::ALIGN_CENTER);  // 对应 justify-content: center

// 添加三个子元素（分别设置红、绿、蓝背景色）
OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(100, 60);
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);
OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(100, 60);
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);
OHOS::UIView* viewC = new OHOS::UIView();
viewC->Resize(100, 60);
viewC->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Blue().full);
layout->Add(viewA);
layout->Add(viewB);
layout->Add(viewC);

layout->LayoutChildren(); // 触发布局
layout->Invalidate();     // 触发重绘
```

预期效果：红、绿、蓝三个子视图作为一个整体在容器水平方向居中。

![ALIGN_CENTER主轴居中效果](../figures/flex-justify-content-center.png)

#### 两端对齐（ALIGN_BETWEEN）

```cpp
layout->SetMajorAxisAlign(OHOS::ALIGN_BETWEEN); // 对应 justify-content: space-between
layout->LayoutChildren();
layout->Invalidate();
```

预期效果：红色子视图贴容器左端、蓝色子视图贴右端，其余间隔均分。

![ALIGN_BETWEEN两端对齐效果](../figures/flex-justify-content-space-between.png)

#### 垂直方向间隔均分（ALIGN_EVENLY）

```cpp
layout->SetLayoutDirection(OHOS::LAYOUT_VER);   // 主轴：垂直
layout->SetMajorAxisAlign(OHOS::ALIGN_EVENLY);  // 对应 justify-content: space-evenly
layout->LayoutChildren();
layout->Invalidate();
```

预期效果：各子视图在垂直方向均匀分布（含首尾与容器边缘的间隔）。

![ALIGN_EVENLY间隔均分效果](../figures/flex-justify-content-space-evenly.png)

## 约束

### 剩余空间约束

space-between / space-around / space-evenly依赖主轴剩余空间；主轴无剩余空间（子元素排满）时与flex-start表现相同，不属于布局异常。

### 与其他flex属性的优先级

#### margin-left: auto会覆盖justify-content对该子项的控制

当某个子项设置了margin-left: auto时，该子项左侧的剩余空间会被auto全部吸收，从而被推向主轴终点方向。此时容器设置的justify-content不再影响该子项的位置。

| 场景 | 结果 |
| --- | --- |
| 子项未设置margin-left: auto | justify-content正常生效 |
| 子项设置margin-left: auto | 该子项位置由auto决定，justify-content对其失效 |

> **注意：**
>
> margin-left: auto只在flex-direction: row时生效，详见[《quickstart-lite-flex-margin-left.md》](quickstart-lite-flex-margin-left.md)。

#### flex-grow占满空间时，space-* 不会产生间距

如果容器内子项通过flex-grow把主轴剩余空间全部占满，主轴上实际没有剩余空间，此时space-between / space-around / space-evenly的表现与flex-start相同。

| 组合 | 实际效果 |
| --- | --- |
| justify-content: space-between + 子项flex-grow占满 | 子项贴紧主轴起点排列，无间距 |
| justify-content: space-evenly + 子项flex-grow占满 | 子项贴紧主轴起点排列，无间距 |
