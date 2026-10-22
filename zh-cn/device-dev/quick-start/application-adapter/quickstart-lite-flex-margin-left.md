# margin-left CSS能力开发指南

## 概述

margin-left用于设置元素**左侧外边距**，控制元素与其左侧参照物之间的间距。在flex-direction: row的flex容器中，margin-left作用于主轴方向，影响子元素在水平方向上的起始位置。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| 具体像素值，如20px | 左侧留出固定间距 |
| 百分比，如30% | 左侧间距为容器宽度的百分比 |
| auto | 吸收主轴剩余空间，将元素推向右侧（**需打开特性宏后生效，见 [margin-left: auto生效约束](#margin-left-auto生效约束)**） |

不设置margin-left时，默认值为0px。

### Native接口

JS应用的margin-left CSS属性，在引擎层对应ui_lite的UIView样式设置。Native（C++）开发可直接使用以下接口控制左侧外边距：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| UIView::SetStyle | STYLE_MARGIN_LEFT + int16_t value：像素值 | 无（void） | 设置固定左侧外边距。需再调用Invalidate()刷新显示 |
| UIView::SetMarginLeftAuto | bool isAuto：true开启auto / false关闭 | 无（void） | 设置左侧外边距为auto（吸收剩余空间）。**需打开特性宏后生效，见 [margin-left: auto生效约束](#margin-left-auto生效约束)** |
| UIView::IsMarginLeftAuto | 无 | bool | 查询是否开启了左侧auto margin |
| UIView::GetStyle | STYLE_MARGIN_LEFT | int16_t | 获取当前左侧外边距像素值 |

涉及的头文件：

```cpp
#include "components/ui_view.h"   // OHOS::UIView / STYLE_MARGIN_LEFT
```

## 使用示例

### JS使用示例

#### 固定左侧间距

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
    width: 400px;
    height: 100px;
}

.item {
    width: 80px;
    height: 60px;
}

.item-red {
    background-color: #e74c3c;
    margin-left: 20px; /* 红色块左侧留出 20px 间距 */
}

.item-green {
    background-color: #2ecc71;
    margin-left: 10px; /* 绿色块左侧留出 10px 间距 */
}

.item-blue {
    background-color: #3498db;
    /* margin-left 默认为 0px */
}
```

预期效果：红色块左侧有20px空白，绿色块左侧有10px空白，蓝色块紧贴前元素。

![固定左侧间距效果](../figures/flex-margin-left-fixed.png)

#### margin-left: auto右对齐

```css
/* index.css */
.container {
    flex-direction: row;
    justify-content: flex-start; /* 默认从左对齐 */
    width: 400px;
    height: 100px;
}

.item {
    width: 80px;
    height: 60px;
}

.item-red {
    background-color: #e74c3c;
}

.item-blue {
    background-color: #3498db;
    margin-left: auto; /* 吸收剩余空间，蓝色块被推到最右侧 */
}
```

预期效果：红色块靠左排列，蓝色块被推到容器最右侧，中间留白由auto吸收。

![margin-left auto右对齐效果](../figures/flex-margin-left-auto.png)

> **注意：**
>
> margin-left: auto需打开特性宏后生效，见 [margin-left: auto生效约束](#margin-left-auto生效约束)。

### Native接口使用示例

#### 固定左侧间距

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

// 创建 flex 容器（FlexLayout 本身即容器视图，直接挂载子视图）
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 400, 100);            // 容器位置和大小
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);   // 主轴：水平

// 添加红色子视图，左侧间距 20px
OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(80, 60);
viewA->SetStyle(STYLE_MARGIN_LEFT, 20);         // margin-left: 20px
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);

// 添加绿色子视图，左侧间距 10px
OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(80, 60);
viewB->SetStyle(STYLE_MARGIN_LEFT, 10);         // margin-left: 10px
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);

// 添加蓝色子视图，默认左侧间距 0px
OHOS::UIView* viewC = new OHOS::UIView();
viewC->Resize(80, 60);
viewC->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Blue().full);

layout->Add(viewA);
layout->Add(viewB);
layout->Add(viewC);

layout->LayoutChildren(); // 触发布局
layout->Invalidate();     // 触发重绘
```

预期效果：红色子视图左侧有20px空白，绿色子视图左侧有10px空白，蓝色子视图紧贴前元素。

![固定左侧间距效果](../figures/flex-margin-left-fixed.png)

#### margin-left: auto右对齐

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

// 创建 flex 容器
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 400, 100);
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);
layout->SetMajorAxisAlign(OHOS::ALIGN_START);   // 主轴起点对齐

// 添加红色子视图
OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(80, 60);
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);

// 添加蓝色子视图，设置 margin-left: auto
OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(80, 60);
viewB->SetMarginLeftAuto(true);                 // margin-left: auto
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Blue().full);

layout->Add(viewA);
layout->Add(viewB);

layout->LayoutChildren();
layout->Invalidate();
```

预期效果：红色子视图靠左排列，蓝色子视图被推到容器最右侧。

> **注意：**
>
> SetMarginLeftAuto(true)需打开特性宏后生效，见 [margin-left: auto生效约束](#margin-left-auto生效约束)。

![margin-left auto右对齐效果](../figures/flex-margin-left-auto.png)

## 约束

### margin-left: auto生效约束
margin-left: auto需在config.json中打开ui_lite_enable_flex_layout_config（对应ui_lite）和ace_engine_lite_enable_flex_layout_config（对应ace_engine_lite）两个特性开关后编译生效。宏关闭时设置auto不生效，保持默认0px行为。

margin-left: auto仅在flex-direction: row时吸收主轴剩余空间。
