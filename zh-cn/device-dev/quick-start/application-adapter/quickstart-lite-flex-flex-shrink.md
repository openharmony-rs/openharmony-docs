# flex-shrink CSS能力开发指南

## 概述

flex-shrink用于设置flex子项在**主轴空间不足**时的收缩比例。当所有子项的主轴尺寸之和超过容器时，设置了flex-shrink的子项会按比例缩小。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| 非负整数 | 收缩比例，数值越大，承担的收缩量越多 |
| 0 | 不参与收缩 |

取值范围：0 ~ 65535。

### 默认行为

不设置flex-shrink时，默认值为0，即默认不参与收缩。

### Native接口

JS应用的flex-shrink CSS属性，在引擎层对应ui_lite的UIView flex子项属性。Native（C++）开发可直接使用以下接口控制子项主轴收缩比例：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| UIView::SetFlexShrink | uint16_t shrink：收缩比例 | 无（void） | 设置子项主轴收缩比例，需父容器重新布局后生效 |

涉及的头文件：

```cpp
#include "components/ui_view.h"   // OHOS::UIView
#include "layout/flex_layout.h"   // OHOS::FlexLayout
#include "layout/layout.h"        // OHOS::LAYOUT_HOR 等
#include "gfx_utils/color.h"      // OHOS::Color（设置背景色用）
```

### 与尺寸约束的关系

- flex-shrink只在父容器主轴空间不足时生效；
- 收缩计算会结合子项当前主轴尺寸和flex-shrink比例计算收缩量，再受最小尺寸约束影响；
- 某个子项达到最小尺寸后会被冻结，剩余溢出量继续分配给其他可收缩子项。

## 使用示例

### JS使用示例

#### 按比例收缩

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red shrink"></div>
    <div class="item item-green shrink-more"></div>
    <div class="item item-blue fixed"></div>
</div>
```

```css
/* index.css */
.container {
    flex-direction: row;
    width: 200px;
    height: 100px;
}

.item {
    width: 100px;
    height: 80px;
}

.fixed {
    flex-shrink: 0;
}

.shrink {
    flex-shrink: 1;
}

.shrink-more {
    flex-shrink: 2;
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

预期效果：空间不足时，蓝色.fixed不缩小，红色和绿色子项按1:2比例承担收缩。

![flex-shrink收缩效果](../figures/flex-flex-shrink.png)

### Native接口使用示例

#### 按比例收缩

```cpp
#include "components/ui_view.h"
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 200, 100);
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);

OHOS::UIView* viewA = new OHOS::UIView();
OHOS::UIView* viewB = new OHOS::UIView();
OHOS::UIView* viewC = new OHOS::UIView();
viewA->Resize(100, 80);
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);
viewB->Resize(100, 80);
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);
viewC->Resize(100, 80);
viewC->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Blue().full);
viewA->SetFlexShrink(1);
viewB->SetFlexShrink(2);
viewC->SetFlexShrink(0);
layout->Add(viewA);
layout->Add(viewB);
layout->Add(viewC);
layout->LayoutChildren();
layout->Invalidate();
```

预期效果：主轴空间不足时，三个子视图按收缩比例参与计算。

![flex-shrink收缩效果](../figures/flex-flex-shrink.png)

## 约束

### CSS取值约束

以下为 **CSS属性侧**的取值约束：JS页面（HML/CSS）中flex-shrink仅支持0 ~ 65535范围内的非负整数。

### 生效约束

- 该能力需打开ui_lite_enable_flex_layout_config和ace_engine_lite_enable_flex_layout_config两个特性开关后编译生效；
- 负数不支持；
- 父容器主轴空间足够时，flex-shrink不产生收缩效果。

### 与尺寸约束的优先级

flex-shrink在空间不足时按比例收缩子项，但子项最终尺寸仍受min-width / min-height / max-width / max-height约束。当收缩结果低于下限时，会被min-*截断。

| 约束 | 对flex-shrink结果的影响 |
| --- | --- |
| 无min-*约束 | 按flex-shrink比例收缩 |
| 达到min-width / min-height | 该子项被冻结在min-*值，剩余溢出量继续分配给其他子项 |

> **注意：**
>
> 主轴方向上max-*约束对flex-shrink通常不影响（flex-shrink是收缩变小），但min-*会限制收缩下限。
