# flex-basis CSS能力开发指南

## 概述

flex-basis用于设置flex子项参与主轴空间分配前的**基础尺寸**。它可以理解为flex布局开始计算前，先给子项一个主轴方向上的初始宽度或高度。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| 像素值 | 设置主轴基础尺寸，例如120px |
| 数字值 | 按像素值处理，例如120 |

取值范围：0 ~ 32767。

### 默认行为

不设置flex-basis时，使用子项当前主轴尺寸作为基础尺寸。

### Native接口

JS应用的flex-basis CSS属性，在引擎层对应ui_lite的UIView flex子项属性。Native（C++）开发可直接使用以下接口设置子项参与flex布局前的主轴基础尺寸：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| UIView::SetFlexBasis | int16_t basis：主轴基础尺寸 | 无（void） | 设置子项主轴基础尺寸，需父容器重新布局后生效 |

涉及的头文件：

```cpp
#include "components/ui_view.h"   // OHOS::UIView
#include "layout/flex_layout.h"   // OHOS::FlexLayout
#include "layout/layout.h"        // OHOS::LAYOUT_HOR 等
#include "gfx_utils/color.h"      // OHOS::Color（设置背景色用）
```

### 与flex-direction的关系

| flex-direction | flex-basis影响的尺寸 |
| --- | --- |
| row | 宽度 |
| column | 高度 |

## 使用示例

### JS使用示例

#### 设置主轴基础尺寸

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red"></div>
    <div class="item item-green basis"></div>
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

.basis {
    flex-basis: 120px;
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

预期效果：绿色.basis子项参与布局时，主轴基础宽度按120px计算。

![flex-basis基础尺寸效果](../figures/flex-flex-basis.png)

### Native接口使用示例

#### 设置主轴基础尺寸

```cpp
#include "components/ui_view.h"
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 400, 100);
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);

// 绿色子视图原始宽度为 80px，设置 flex-basis 后按 120px 参与主轴布局。
OHOS::UIView* view = new OHOS::UIView();
view->Resize(80, 60);
view->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);
view->SetFlexBasis(120);
layout->Add(view);
layout->LayoutChildren();
layout->Invalidate();
```

预期效果：绿色子视图参与布局时，主轴基础宽度按120px计算。

![flex-basis基础尺寸效果](../figures/flex-flex-basis.png)

## 约束

### CSS取值约束

以下为 **CSS属性侧**的取值约束：JS页面（HML/CSS）中flex-basis当前仅支持0 ~ 32767范围内的像素值或数字值，**不支持**百分比、auto、content等W3C其他取值。

### 生效约束

- 该能力需打开ui_lite_enable_flex_layout_config和ace_engine_lite_enable_flex_layout_config两个特性开关后编译生效；
- 负数或超出INT16_MAX的值不支持；
- 最终尺寸仍会继续受min-width / max-width / min-height / max-height约束影响。

### 与width / height的优先级

flex-basis设置的是子项参与flex布局前的**主轴基础尺寸**。它会作为主轴方向尺寸计算的起点，后续再叠加flex-grow / flex-shrink及min-* / max-*约束。

| flex-direction | flex-basis影响 | 与width / height的关系 |
| --- | --- | --- |
| row | 宽度 | 优先作为主轴基础宽度参与计算，最终宽度仍受flex-grow / flex-shrink / max-width / min-width约束 |
| column | 高度 | 优先作为主轴基础高度参与计算，最终高度仍受flex-grow / flex-shrink / max-height / min-height约束 |

> **注意：**
>
> flex-basis不会覆盖width / height在布局树中的配置值，但flex布局计算会以flex-basis为起点。若同时设置，建议避免让width / height与flex-basis产生互斥预期。
