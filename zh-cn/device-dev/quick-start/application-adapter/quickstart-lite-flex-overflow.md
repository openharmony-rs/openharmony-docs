# overflow CSS能力开发指南

## 概述

overflow用于设置flex容器内**子元素超出容器边界时的显示行为**：超出部分可见或被裁剪隐藏。裁剪区域为容器的padding box（content + padding，不含border）。

## 能力范围

### 支持的值（CSS）

| 值 | 含义 |
| --- | --- |
| visible（默认值） | 子元素超出容器部分正常显示，不做裁剪 |
| hidden | 子元素超出容器padding box的部分被裁剪隐藏 |

不设置overflow时，容器按默认值visible处理。

### Native接口

JS应用的overflow CSS属性，在引擎层对应ui_lite的UIView::SetOverflow接口。Native（C++）开发可直接使用以下接口控制溢出行为：

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| UIView::SetOverflow | OverflowMode mode：OVERFLOW_VISIBLE（默认）/ OVERFLOW_HIDDEN | 无（void） | 设置子元素超出容器时的显示行为。调用后会触发容器重绘以刷新裁剪区域 |
| UIView::GetOverflow | 无 | OverflowMode | 获取当前溢出模式 |

OverflowMode取值枚举（`components/ui_view.h`，类型为uint8_t）：

| 常量 | 数值 | 含义 |
| --- | --- | --- |
| OVERFLOW_VISIBLE | 0 | 超出部分可见（对应CSS visible） |
| OVERFLOW_HIDDEN | 1 | 超出部分裁剪（对应CSS hidden） |

涉及的头文件：

```cpp
#include "components/ui_view.h"   // OHOS::UIView / OverflowMode
```

### 与其他属性的关系

- overflow作用于容器本身，影响容器内所有子视图的绘制范围；
- 设置overflow: hidden后，子元素超出容器padding box的部分不可见，但子元素的实际位置和尺寸不受影响。

## 使用示例

### JS使用示例

#### visible超出可见（默认）

```html
<!-- index.hml -->
<div class="container">
    <div class="item item-red"></div>
</div>
```

```css
/* index.css */
.container {
    width: 200px;
    height: 100px;
    overflow: visible; /* 默认值，可不写 */
}

.item {
    width: 300px;
    height: 60px;
}

.item-red {
    background-color: #e74c3c;
}
```

预期效果：红色色块宽度300px超出容器200px，右侧溢出部分仍然可见。

![visible超出可见效果](../figures/flex-overflow-visible.png)

#### hidden超出裁剪

```css
.container {
    width: 200px;
    height: 100px;
    overflow: hidden; /* 超出部分被裁剪 */
}
```

预期效果：红色色块右侧超出容器padding box的部分被裁剪，只显示容器内的200px宽。

![hidden超出裁剪效果](../figures/flex-overflow-hidden.png)

### Native接口使用示例

#### visible超出可见（默认）

```cpp
#include "components/ui_view.h"
#include "components/ui_view_group.h"
#include "gfx_utils/color.h"

// 创建容器视图
OHOS::UIViewGroup* container = new OHOS::UIViewGroup();
container->SetPosition(0, 0, 200, 100);         // 容器大小 200x100
container->SetOverflow(OHOS::OVERFLOW_VISIBLE); // 默认值，可不写

// 创建子视图（宽度超出容器）
OHOS::UIView* child = new OHOS::UIView();
child->SetPosition(0, 0, 300, 60);              // 子视图宽 300px，超出容器
child->SetStyle(STYLE_BACKGROUND_COLOR, OHOS::Color::Red().full);

container->Add(child);
container->Invalidate(); // 触发重绘
```

预期效果：子视图右侧超出容器的部分正常显示。

![visible超出可见效果](../figures/flex-overflow-visible.png)

#### hidden超出裁剪

```cpp
container->SetOverflow(OHOS::OVERFLOW_HIDDEN); // 超出部分裁剪
container->Invalidate();
```

预期效果：子视图右侧超出容器padding box的部分被裁剪，仅容器内区域可见。

![hidden超出裁剪效果](../figures/flex-overflow-hidden.png)

## 约束

### 特性开关约束

overflow CSS能力需在config.json中打开ui_lite_enable_flex_layout_config（对应ui_lite）和ace_engine_lite_enable_flex_layout_config（对应ace_engine_lite）两个特性开关后编译生效。宏关闭时CSS属性不生效。

### 裁剪区域约束

overflow: hidden的裁剪区域为容器的 **padding box**（content区域 + padding区域），不包含border。即子元素超出padding box的部分会被裁剪，但在border范围内且处于padding box之外的部分也会被裁剪。
