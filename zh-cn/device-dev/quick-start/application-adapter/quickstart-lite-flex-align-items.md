# align-items CSS能力开发指南

## 概述

align-items用于设置flex容器内子元素在**交叉轴方向**上的对齐方式。交叉轴与主轴垂直：flex-direction: row时交叉轴为垂直方向，flex-direction: column时交叉轴为水平方向。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| flex-start | 子元素向交叉轴起点对齐 |
| flex-end | 子元素向交叉轴终点对齐 |
| center | 子元素在交叉轴方向居中 |
| stretch | 交叉轴方向**未设置尺寸**的子元素被拉伸至容器（换行时为所在行）的交叉轴尺寸；已显式设置尺寸的子元素保持原尺寸，并按flex-start对齐。**该值需打开特性宏后生效，见 [stretch生效约束](#stretch生效约束)** |

### 默认行为

不设置align-items时：

- **JS/CSS页面中**，子元素在交叉轴方向按 **flex-start** 对齐；
- **直接使用ui_lite FlexLayout接口创建容器时**，默认对齐方式为 **center**。

> **说明：**
>
> ace_engine_lite在创建div组件时会将对齐方式默认设置为flex-start，覆盖了ui_lite FlexLayout本身的默认center。因此本能力文档以 **JS/CSS行为**为准；不设置align-items时，测试用例应按默认flex-start验证。

### Native接口

JS应用的align-items CSS属性，在引擎层对应ui_lite的FlexLayout（div / list-item的底层布局实现）。Native（C++）开发可直接使用以下接口控制交叉轴对齐：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| FlexLayout::SetSecondaryAxisAlign | const AlignType& align：对齐常量 | 无（void） | 设置交叉轴方向的对齐方式。仅更新对齐标记，需再调用LayoutChildren()重新布局、Invalidate()刷新显示 |

AlignType取值常量（`layout/layout.h`，类型为uint8_t）：

| 常量 | 数值 | 含义 |
| --- | --- | --- |
| ALIGN_START | 0 | 交叉轴起点对齐（对应CSS flex-start） |
| ALIGN_END | 1 | 交叉轴终点对齐（对应CSS flex-end） |
| ALIGN_CENTER | 2 | 交叉轴居中（对应CSS center） |
| ALIGN_STRETCH | 6 | 交叉轴拉伸（对应CSS stretch），**需打开特性宏后生效，见 [stretch生效约束](#stretch生效约束)** |

涉及的头文件：

```cpp
#include "layout/flex_layout.h"   // OHOS::FlexLayout
#include "layout/layout.h"        // OHOS::AlignType / ALIGN_START 等
```

### 与其他flex属性的关系

- align-items始终作用于**交叉轴**：flex-direction: row时控制垂直方向，flex-direction: column时控制水平方向；
- 修改flex-direction后，align-items的作用方向随之旋转；
- 主轴方向的对齐请使用justify-content（见[《quickstart-lite-flex-justify-content.md》](quickstart-lite-flex-justify-content.md)）。

## 使用示例

### JS使用示例

#### 交叉轴居中（最常用）

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red"></div>
    <div class="item item-green tall"></div>
    <div class="item item-blue"></div>
</div>
```

```css
/* index.css */
.container {
    flex-direction: row;
    align-items: center; /* 高度不同的子元素垂直居中 */
    height: 120px;
}

.item {
    width: 100px;
    height: 60px;
}

.tall {
    height: 90px;
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

预期效果：高度不一的红、绿、蓝三个色块在容器垂直方向居中对齐。

![交叉轴居中效果](../figures/flex-align-items-center.png)

#### 交叉轴起点 / 终点对齐

```css
.container {
    flex-direction: row;
    align-items: flex-start; /* 顶部对齐，改为 flex-end 则底部对齐 */
    height: 120px;
}
```

预期效果：高度不一的色块顶部对齐（flex-end时底部对齐）。

![交叉轴起点对齐效果](../figures/flex-align-items-flex-start.png)

![交叉轴终点对齐效果](../figures/flex-align-items-flex-end.png)

#### column方向下使用

```css
.container {
    flex-direction: column;  /* 交叉轴：水平 */
    align-items: center;     /* 子元素水平居中 */
}
```

预期效果：垂直堆叠的色块在水平方向居中（表单类页面常用）。

![column方向交叉轴居中效果](../figures/flex-flex-direction-column-center.png)

#### stretch拉伸

```html
<!-- index.hml -->
<div class="container">
    <div class="auto-item"></div>
    <div class="fixed-item"></div>
</div>
```

```css
/* index.css */
.container {
    flex-direction: row;
    align-items: stretch;
    height: 100px;
}

.auto-item {
    width: 80px;
    /* 未设置 height：被拉伸至容器高度 100px */
    background-color: #2ecc71;
}

.fixed-item {
    width: 80px;
    height: 40px; /* 显式设置高度：保持 40px，顶部对齐 */
    background-color: #e74c3c;
}
```

预期效果：绿色块被拉伸至容器全高，红色块保持自身40px高度。（需打开特性宏，见 [stretch生效约束](#stretch生效约束)）

![stretch拉伸效果](../figures/flex-align-items-stretch.png)

### Native接口使用示例

#### 交叉轴居中（ALIGN_CENTER）

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"      // OHOS::Color（设置背景色用）

// 创建 flex 容器（FlexLayout 本身即容器视图，直接挂载子视图）
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 300, 120);              // 容器位置和大小：x, y, width, height
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);     // 主轴：水平
layout->SetSecondaryAxisAlign(OHOS::ALIGN_CENTER); // 对应 align-items: center

// 添加三个高度不一的子元素（分别设置红、绿、蓝背景色）
OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(100, 60);
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);
OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(100, 90);
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

预期效果：高度不一的红、绿、蓝三个子视图在容器垂直方向居中对齐。

![ALIGN_CENTER交叉轴居中效果](../figures/flex-align-items-center.png)

#### 交叉轴终点对齐（ALIGN_END）

```cpp
layout->SetSecondaryAxisAlign(OHOS::ALIGN_END); // 对应 align-items: flex-end
layout->LayoutChildren();
layout->Invalidate();
```

预期效果：高度不一的三个子视图底部对齐。

![ALIGN_END交叉轴终点对齐效果](../figures/flex-align-items-flex-end.png)

#### 交叉轴拉伸（ALIGN_STRETCH，需打开特性宏）

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

// 创建 flex 容器
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 300, 100);                // 容器高度 100px（交叉轴尺寸）
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);       // 主轴：水平，交叉轴：垂直
layout->SetSecondaryAxisAlign(OHOS::ALIGN_STRETCH); // 对应 align-items: stretch

// 添加绿色子视图：只设置宽度，高度传 0 表示未显式设置（auto）
OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(80, 0);                               // 高度为 auto，将被拉伸至容器高度 100px
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);

// 添加红色子视图：显式设置宽度和高度
OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(80, 40);
viewB->SetHasExplicitHeight(true);                    // 标记为显式设置高度，保持 40px 原尺寸
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);

layout->Add(viewA);
layout->Add(viewB);

layout->LayoutChildren(); // 触发布局
layout->Invalidate();     // 触发重绘
```

预期效果：绿色子视图未设置高度，被拉伸至容器高度100px；红色子视图显式设置了高度40px，保持原尺寸。

> **注意：**
>
> 该取值需打开特性宏后生效，见 [stretch生效约束](#stretch生效约束)。

![ALIGN_STRETCH交叉轴拉伸效果](../figures/flex-align-items-stretch.png)

## 约束

### CSS取值约束

以下为 **CSS属性侧**的取值约束：JS页面（HML/CSS）中align-items仅支持stretch / flex-start / flex-end / center四个值，baseline当前不支持。

### stretch生效约束
- stretch只对交叉轴方向**未设置尺寸**的子元素生效，显式设置了交叉轴尺寸的子元素保持原尺寸；
- **stretch的完整语义（拉伸、尊重显式尺寸、换行时拉伸到所在行高度、方向切换后恢复原尺寸）需在config.json中打开ui_lite_enable_flex_layout_config（对应ui_lite）和ace_engine_lite_enable_flex_layout_config（对应ace_engine_lite）两个特性开关后编译生效**。宏关闭时设置stretch不生效，容器保持默认对齐行为。

### 与其他flex属性的优先级

#### align-self会覆盖align-items

align-items是容器为所有子项设置的默认交叉轴对齐规则。如果某个子项单独设置了align-self，则以该子项的align-self为准，不再受容器align-items控制。

| 场景 | 生效属性 |
| --- | --- |
| 子项未设置align-self | align-items |
| 子项设置align-self | align-self覆盖align-items |

#### stretch与显式尺寸/约束的优先级

align-items: stretch不会覆盖子项在交叉轴方向上的显式尺寸，也不会超过min-* / max-*约束。

| 子项状态 | stretch行为 |
| --- | --- |
| 未显式设置交叉轴尺寸 | 拉伸到容器（或所在行）交叉轴尺寸 |
| 显式设置交叉轴尺寸 | 保持原尺寸，按flex-start对齐 |
| 拉伸结果超过max-width / max-height | 被max-*约束截断 |
| 拉伸结果小于min-width / min-height | 被min-*约束截断 |
