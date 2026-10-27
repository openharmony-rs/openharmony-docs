# position CSS能力开发指南

## 概述

position用于设置元素在页面中的**定位方式**。本能力聚焦absolute定位：设置position: absolute后，元素脱离正常布局流，按照W3C规则向上查找最近的非static祖先作为定位参照物，可通过left / top / right / bottom控制具体位置。

> **说明：**
>
> static是CSS默认布局行为（元素参与正常flex布局流），不属于本能力新增范围；未设置position时即为static。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| absolute | 元素脱离正常布局流，以最近的非static祖先作为containing block进行定位；找不到非static祖先时，以初始包含块（视图树最顶层视图，通常为页面根视图）为参照（**需打开特性宏后生效，见 [特性开关约束](#特性开关约束)**） |

未设置position时，默认值为static，元素按正常flex布局流排列。

### 配套偏移属性（absolute定位时）

当position: absolute时，可通过以下属性控制具体位置：

| 属性 | 支持的值 | 含义 |
| --- | --- | --- |
| left | 具体像素值 / 百分比 | 元素左边缘距离containing block左边缘的偏移 |
| top | 具体像素值 / 百分比 | 元素上边缘距离containing block上边缘的偏移 |
| right | 具体像素值 / 百分比 | 元素右边缘距离containing block右边缘的偏移 |
| bottom | 具体像素值 / 百分比 | 元素下边缘距离containing block下边缘的偏移 |

### Native接口

JS应用的position CSS属性，在引擎层对应ui_lite的UIView::SetPositionType接口。Native（C++）开发可直接使用以下接口控制定位：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| UIView::SetPositionType | uint8_t type：POSITION_ABSOLUTE | 无（void） | 设置定位方式为绝对定位。未设置时默认值为POSITION_STATIC（正常布局流） |
| UIView::GetPositionType | 无 | uint8_t | 获取当前定位方式 |
| UIView::SetFlexLeft | int16_t v：像素值 | 无（void） | 设置left偏移 |
| UIView::SetFlexLeftPercent | float percent：百分比 | 无（void） | 设置left百分比偏移 |
| UIView::SetFlexTop | int16_t v：像素值 | 无（void） | 设置top偏移 |
| UIView::SetFlexTopPercent | float percent：百分比 | 无（void） | 设置top百分比偏移 |
| UIView::SetFlexRight | int16_t v：像素值 | 无（void） | 设置right偏移 |
| UIView::SetFlexRightPercent | float percent：百分比 | 无（void） | 设置right百分比偏移 |
| UIView::SetFlexBottom | int16_t v：像素值 | 无（void） | 设置bottom偏移 |
| UIView::SetFlexBottomPercent | float percent：百分比 | 无（void） | 设置bottom百分比偏移 |
| UIView::ClearFlexLeft | 无 | 无（void） | 清除left偏移设置 |
| UIView::ClearFlexRight | 无 | 无（void） | 清除right偏移设置 |
| UIView::ClearFlexTop | 无 | 无（void） | 清除top偏移设置 |
| UIView::ClearFlexBottom | 无 | 无（void） | 清除bottom偏移设置 |

PositionType取值常量（`layout/layout.h`，类型为uint8_t）：

| 常量 | 数值 | 含义 |
| --- | --- | --- |
| POSITION_ABSOLUTE | 2 | 绝对定位（对应CSS absolute），**本能力交付的值** |

> **说明：**
>
> POSITION_STATIC（数值0，对应CSS static）是UIView的默认定位方式，表示元素参与正常flex布局流。本能力不对static做额外开发，未调用SetPositionType时即为此默认状态。

涉及的头文件：

```cpp
#include "components/ui_view.h"   // OHOS::UIView / SetPositionType 等
#include "layout/layout.h"        // OHOS::POSITION_STATIC / POSITION_ABSOLUTE
```

### 与其他属性的关系

- position: absolute的元素**脱离正常flex布局流**，不参与justify-content / align-items的计算，也不占用flex行空间；
- 定位参照物按W3C规则确定：向上查找最近的非static祖先（当前引擎中非static仅可能为absolute）作为containing block；若不存在非static祖先，则以初始包含块（视图树最顶层视图）为参照物。

## 使用示例

### JS使用示例

#### absolute单点定位

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red"></div>
</div>
```

```css
/* index.css */
.container {
    position: absolute; /* 容器自身设为 absolute，成为子项的定位参照物（最近的非 static 祖先） */
    left: 0px;          /* 容器自身无定位祖先，参照初始包含块（页面根），落在页面左上角 */
    top: 0px;
    flex-direction: row;
    width: 400px;
    height: 100px;
}

.item-red {
    position: absolute; /* 脱离正常流，以 .container 为参照物 */
    left: 120px;        /* 距离参照物左边缘 120px */
    top: 30px;          /* 距离参照物上边缘 30px */
    width: 80px;
    height: 50px;
    background-color: #e74c3c;
}
```

预期效果：红色块脱离正常布局流，以.container（最近的非static祖先）为参照物，定位在容器内 (120, 30) 处。

> **说明：**
> 
> - 若.container不设置position（即为static），红色块将向上越过它，直接以初始包含块（页面根视图）为参照物；
> - 把容器设为absolute后容器自身也脱离布局流，建议同时用left/top给定其位置；当前引擎未实现W3C中absolute元素在normal flow里的默认静态位置，不写偏移时容器会落在其参照物的原点（0,0）。

![absolute单点定位效果](../figures/flex-position-absolute.png)

> **注意：**
>
> position: absolute及偏移属性需打开特性宏后生效，见 [特性开关约束](#特性开关约束)。

### Native接口使用示例

#### absolute单点定位

```cpp
#include "layout/flex_layout.h"
#include "layout/layout.h"
#include "gfx_utils/color.h"

// 创建 flex 容器，并设为 absolute，使其成为子项的定位参照物（子项最近的非 static 祖先）
OHOS::FlexLayout* layout = new OHOS::FlexLayout();
layout->SetPosition(0, 0, 400, 100);
layout->SetLayoutDirection(OHOS::LAYOUT_HOR);
layout->SetPositionType(OHOS::POSITION_ABSOLUTE); // 关键：容器设为非 static，子项才以它为参照

// 添加红色子视图（absolute 定位）
OHOS::UIView* viewB = new OHOS::UIView();
viewB->Resize(80, 50);
viewB->SetPositionType(OHOS::POSITION_ABSOLUTE); // 脱离正常布局流
viewB->SetFlexLeft(120);                         // left: 120px，相对参照物 layout
viewB->SetFlexTop(30);                           // top: 30px，相对参照物 layout
viewB->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);

layout->Add(viewB);

layout->LayoutChildren();
layout->Invalidate();
```

预期效果：红色子视图脱离正常布局流，定位在容器内 (120, 30) 处。

> **注意：**
>
> POSITION_ABSOLUTE及偏移接口需打开特性宏后生效，见 [特性开关约束](#特性开关约束)。

> **说明：**
>
> 本例中layout通过SetPositionType(OHOS::POSITION_ABSOLUTE)设为非static，因此子项viewB向上查找到的第一个非static祖先就是它，直接以该祖先为参照物。layout自身没有非static祖先且未挂接父视图，其位置保持SetPosition给定值不变；若容器不设POSITION_ABSOLUTE，子项会继续向上查找，找不到非static祖先时以视图树最顶层视图（初始包含块）为参照物。另外注意：absolute视图自身未设置SetFlexLeft/SetFlexTop等偏移时，会落在其参照物的原点（0,0）；当前引擎未实现W3C中absolute元素在normal flow里的默认静态位置。

![absolute单点定位效果](../figures/flex-position-absolute.png)

## 约束

### CSS取值约束

以下为 **CSS属性侧**的取值约束：本能力交付position: absolute；static是默认行为，无需也不在本能力范围内显式配置。JS页面（HML/CSS）中**不支持** W3C标准中的以下值：

| 不支持的值 | 说明 |
| --- | --- |
| relative | 相对定位，本版本暂时不支持 |
| fixed | 固定定位，本版本暂时不支持 |

### 特性开关约束
position: absolute及left / top / right / bottom偏移能力需在config.json中打开ui_lite_enable_flex_layout_config（对应ui_lite）和ace_engine_lite_enable_flex_layout_config（对应ace_engine_lite）两个特性开关后编译生效。宏关闭时设置absolute不生效，元素保持static行为。

### 与flex布局属性的冲突

position: absolute的元素**脱离正常flex布局流**，不参与flex容器的一切布局计算。具体而言，以下flex容器级能力对absolute元素均不生效：

| 能力类别 | 说明 |
| --- | --- |
| 主轴方向对齐与分布 | 如justify-content、主轴方向的margin-left: auto等 |
| 交叉轴方向对齐 | 如align-items、align-self |
| 多行分布 | 如align-content |
| 主轴空间伸缩 | 如flex-grow、flex-shrink、flex-basis |
| 子项间距 | 如gap / row-gap / column-gap |
| 换行控制 | 如flex-wrap |

> **说明：**
>
> 上表仅为典型示例，**不是完整清单**。只要属性属于flex容器对正常流子项的布局计算范畴，对position: absolute元素均不生效。absolute元素只受left / top / right / bottom及定位参照物控制。

> **注意：**
>
> 若需要元素参与flex布局，请保持默认static定位。

