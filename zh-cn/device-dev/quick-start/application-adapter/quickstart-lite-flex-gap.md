# gap CSS能力开发指南

## 概述

gap用于设置flex容器内**子元素之间的间距**。row-gap是**行与行之间**的间距，column-gap是**列与列之间**的间距。gap简写形式可同时设置两者。

## 能力范围

### 支持的值（CSS）

| 属性 | 支持的值 | 含义 |
| --- | --- | --- |
| gap | 单个值：具体像素值 / 百分比；或两个值：10px 20px | 单值同时设置row-gap和column-gap；双值时第一个为row-gap，第二个为column-gap |
| row-gap | 具体像素值 / 百分比 | 行与行之间的间距 |
| column-gap | 具体像素值 / 百分比 | 列与列之间的间距 |

不设置时，默认值为0px。负值会被限制为0px。

> **说明：**
>
> 百分比基于容器的content-box尺寸计算；容器对应方向尺寸为auto时，该方向百分比gap退化为0px。

### Native接口

JS应用的gap CSS属性，在引擎层对应ui_lite的FlexLayout。Native（C++）开发可直接使用以下接口控制间距：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| FlexLayout::SetGap | int16_t gap：像素值 | 无（void） | 同时设置row-gap和column-gap |
| FlexLayout::SetRowGap | int16_t gap：像素值 | 无（void） | 设置行与行之间的间距 |
| FlexLayout::SetColumnGap | int16_t gap：像素值 | 无（void） | 设置列与列之间的间距 |
| FlexLayout::SetRowGapPercent | float percent：百分比值 | 无（void） | 设置行与行之间的百分比间距 |
| FlexLayout::SetColumnGapPercent | float percent：百分比值 | 无（void） | 设置列与列之间的百分比间距 |
| FlexLayout::GetRowGap | 无 | int16_t | 获取当前row-gap像素值 |
| FlexLayout::GetColumnGap | 无 | int16_t | 获取当前column-gap像素值 |

涉及的头文件：

```cpp
#include "layout/flex_layout.h"   // OHOS::FlexLayout
```

## 使用示例

### JS使用示例

#### 固定间距

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
    gap: 20px; /* 子元素之间水平间距 20px */
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

.item-green {
    background-color: #2ecc71;
}

.item-blue {
    background-color: #3498db;
}
```

预期效果：红、绿、蓝三个色块水平排列，两两之间间距20px。

![固定间距效果](../figures/flex-gap-fixed.png)

#### 换行场景下分别设置row-gap和column-gap

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red"></div>
    <div class="item item-green"></div>
    <div class="item item-blue"></div>
    <div class="item item-red"></div>
    <div class="item item-green"></div>
</div>
```

```css
/* index.css */
.container {
    flex-direction: row;
    flex-wrap: wrap;
    row-gap: 15px;    /* 换行后行与行之间间距 15px */
    column-gap: 10px; /* 同行内列与列之间间距 10px */
    width: 300px;
    height: 200px;
}

.item {
    width: 70px;
    height: 50px;
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

预期效果：5个子元素排满后自动换行（第一行3个，第二行2个），同行内间距10px，换行后行间距15px。

![换行场景间距效果](../figures/flex-gap-wrap.png)

### Native接口使用示例

#### 固定间距

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

// 创建 flex 容器
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 400, 100);
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);
layout->SetGap(20); // 同时设置 row-gap 和 column-gap 为 20px

// 添加三个子元素
OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(80, 60);
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);

OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(80, 60);
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);

OHOS::UIView* viewC = new OHOS::UIView();
viewC->Resize(80, 60);
viewC->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Blue().full);

layout->Add(viewA);
layout->Add(viewB);
layout->Add(viewC);

layout->LayoutChildren();
layout->Invalidate();
```

预期效果：三个子视图水平排列，两两之间间距20px。

![固定间距效果](../figures/flex-gap-fixed.png)

#### 换行场景下分别设置

```cpp
// 再添加两个子元素，凑齐 5 个以产生换行
OHOS::UIView* viewD = new OHOS::UIView();
viewD->Resize(70, 50);
viewD->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);

OHOS::UIView* viewE = new OHOS::UIView();
viewE->Resize(70, 50);
viewE->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);

layout->Add(viewD);
layout->Add(viewE);

layout->SetFlexWrap(OHOS::FlexLayout::WRAP);
layout->SetRowGap(15);    // 换行后行间距 15px
layout->SetColumnGap(10); // 同行内列间距 10px
layout->LayoutChildren();
layout->Invalidate();
```

预期效果：5个子视图排满后自动换行（第一行3个，第二行2个），同行内间距10px，换行后行间距15px。

![换行场景间距效果](../figures/flex-gap-wrap.png)

## 约束

### 特性开关约束

gap CSS能力需在config.json中打开ui_lite_enable_flex_layout_config（对应ui_lite）和ace_engine_lite_enable_flex_layout_config（对应ace_engine_lite）两个特性开关后编译生效。宏关闭时CSS属性不生效。

### 取值约束

- 负值会被限制为0px；
- row-gap只在产生多行（flex-wrap: wrap且实际换行）时生效；单行排列时设置row-gap无视觉效果。

### 与其他flex属性的依赖关系

#### row-gap依赖flex-wrap: wrap

row-gap控制的是行与行之间的间距，只有在flex-wrap: wrap且实际产生多行时才会生效。flex-wrap: nowrap或wrap但未换行时，row-gap不会产生视觉效果。

| flex-wrap | 子项排列 | row-gap是否生效 |
| --- | --- | --- |
| nowrap | 单行 | 不生效 |
| wrap（未换行） | 单行 | 不生效 |
| wrap（实际换行） | 多行 | 生效 |

#### 百分比gap与容器尺寸的退化

gap / row-gap / column-gap设置为百分比时，基于容器对应方向的content-box尺寸计算。若容器在该方向上尺寸为auto，则该方向的百分比gap退化为0px。

| 容器尺寸 | 百分比gap行为 |
| --- | --- |
| 固定尺寸 | 按百分比计算 |
| auto | 退化为0px |
