# min-height CSS能力开发指南

## 概述

min-height用于设置flex子项的**最小高度**。布局计算过程中，如果子项高度小于该约束，最终高度会被限制到min-height。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| 像素值 | 最小高度，例如70px |
| 数字值 | 按像素值处理，例如70 |

取值范围：0 ~ 32767。

### 默认行为

不设置min-height时，默认没有最小高度约束。引擎层UIView内部以-1表示未设置（UIView::GetMinHeight()返回-1），布局计算时负值按0处理，即默认等效最小高度为0。

### Native接口

JS应用的min-height CSS属性，在引擎层对应ui_lite的UIView尺寸约束属性。Native（C++）开发可直接使用以下接口设置子项最小高度：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| UIView::SetMinHeight | int16_t height：最小高度 | 无（void） | 设置子项最小高度，需父容器重新布局后生效 |

涉及的头文件：

```cpp
#include "components/ui_view.h"   // OHOS::UIView
#include "layout/flex_layout.h"   // OHOS::FlexLayout
#include "layout/layout.h"        // OHOS::LAYOUT_VER 等
#include "gfx_utils/color.h"      // OHOS::Color（设置背景色用）
```

### 与flex布局的关系

- min-height是高度下限，会参与普通尺寸计算；
- 主轴方向上，它会约束flex-grow或flex-shrink后得到的结果；
- 交叉轴方向上，它会约束align-items: stretch或align-self: stretch后得到的结果。

## 使用示例

### JS使用示例

#### 最小高度约束

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red min"></div>
    <div class="item item-green"></div>
    <div class="item item-blue"></div>
</div>
```

```css
/* index.css */
.container {
    flex-direction: row;
    align-items: flex-start;
    width: 300px;
    height: 200px;
}

.item {
    width: 60px;
}

.item-red {
    background-color: #e74c3c;
}

.item-green {
    height: 80px;
    background-color: #2ecc71;
}

.item-blue {
    height: 60px;
    background-color: #3498db;
}

.min {
    height: 50px;
    min-height: 120px;
}
```

预期效果：红色子项高度被min-height限制为不小于120px，绿色、蓝色子项按各自高度显示。效果图中红色子项下方的黄色横线为示意标注，表示min-height限制边界（代码本身不会渲染该黄线）。

![min-height最小高度约束效果](../figures/flex-min-height.png)

### Native接口使用示例

#### 最小高度约束

```cpp
#include "components/ui_view.h"
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 300, 200);
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);

OHOS::UIView* viewA = new OHOS::UIView();
viewA->Resize(60, 50);
viewA->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);
viewA->SetMinHeight(120);
layout->Add(viewA);

OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(60, 80);
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Green().full);
layout->Add(viewB);

OHOS::UIView* viewC = new OHOS::UIView();
viewC->Resize(60, 60);
viewC->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Blue().full);
layout->Add(viewC);

layout->LayoutChildren();
layout->Invalidate();
```

预期效果：红色子视图高度被min-height限制为不小于120，绿色、蓝色子视图按各自高度显示。

![min-height最小高度约束效果](../figures/flex-min-height.png)

## 约束

### CSS取值约束

以下为 **CSS属性侧**的取值约束：JS页面（HML/CSS）中min-height当前仅支持0 ~ 32767范围内的像素值或数字值。百分比值（如50%）不生效；auto等非数字字符串会被按strtol规则解析——auto解析结果为0，等效于不设置约束；带小数的像素值（如10.9px）会被截断取整。

### 生效约束

- 该能力需打开ui_lite_enable_flex_layout_config和ace_engine_lite_enable_flex_layout_config两个特性开关后编译生效；
- 负数或超出INT16_MAX的值不支持；
- 约束只限制最终布局尺寸，不改变CSS中原始配置值。

### 取值冲突

同一元素上若同时设置min-height和max-height，应保证min-height <= max-height。
