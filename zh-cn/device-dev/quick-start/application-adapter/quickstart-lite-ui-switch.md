# Switch组件开发指导

## 功能概述

本模块面向Native侧应用开发。开发者可分别配置选中态与非选中态的滑块尺寸、滑块颜色以及滑块边框颜色，从而让同一个Switch在不同状态下呈现不同的视觉效果。

| 维度     | Switch组件能力                                             |
| -------- | ---------------------------------------------------------- |
| 作用对象 | UIToggleButton的滑块                                       |
| 典型场景 | 开关选中时高亮滑块、非选中时置灰滑块；不同状态使用不同边框 |
| 核心类   | UIToggleButton                                             |

本模块在此基础上提供轻量、可验证的Native API，覆盖 **3 类能力**：

1. 独立滑块尺寸：分别设置选中态与非选中态的滑块半径。
2. 独立滑块颜色：分别设置选中态与非选中态的滑块填充颜色。
3. 独立边框颜色：分别设置选中态与非选中态的滑块外边框颜色。

未配置时保持现有默认效果：滑块颜色默认白色，边框默认不显示，滑块尺寸继续使用CalculateSize() 推导出的默认radius_。

## 功能接口

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| SetOnThumbSize(uint16_t radius) | radius：选中态滑块半径，单位px | 无 | 设置选中态滑块半径；radius为 0 或大于组件圆角corner_ 时恢复默认绘制半径；默认未配置，绘制时使用CalculateSize() 推导出的radius_ |
| SetOffThumbSize(uint16_t radius) | radius：非选中态滑块半径，单位px | 无 | 设置非选中态滑块半径；radius为 0 或大于组件圆角corner_ 时恢复默认绘制半径；默认未配置，绘制时使用CalculateSize() 推导出的radius_ |
| GetOnThumbSize() const | 无 | uint16_t | 获取选中态滑块半径配置 |
| GetOffThumbSize() const | 无 | uint16_t | 获取非选中态滑块半径配置 |
| SetOnThumbColor(ColorType color) | color：选中态滑块颜色 | 无 | 设置选中态滑块颜色；默认值为Color::White() |
| SetOffThumbColor(ColorType color) | color：非选中态滑块颜色 | 无 | 设置非选中态滑块颜色；默认值为Color::White() |
| GetOnThumbColor() const | 无 | ColorType | 获取选中态滑块颜色配置 |
| GetOffThumbColor() const | 无 | ColorType | 获取非选中态滑块颜色配置 |
| SetOnBorderColor(ColorType color) | color：选中态滑块边框颜色 | 无 | 设置选中态滑块边框颜色；默认未配置，不绘制边框 |
| SetOffBorderColor(ColorType color) | color：非选中态滑块边框颜色 | 无 | 设置非选中态滑块边框颜色；默认未配置，不绘制边框 |
| GetOnBorderColor() const | 无 | ColorType | 获取选中态边框颜色配置 |
| GetOffBorderColor() const | 无 | ColorType | 获取非选中态边框颜色配置 |

## 功能示例

[示例工程](https://gitcode.com/openharmony/applications_sample_camera/tree/master/graphic)

### 独立滑块尺寸

```cpp
#include "components/ui_toggle_button.h"

void SetupSwitchThumbSize()
{
    UIToggleButton toggleButton;
    toggleButton.Resize(92, 46);
    toggleButton.SetState(true);

    toggleButton.SetOnThumbSize(10);
    toggleButton.SetOffThumbSize(8);
}
```

<img src="../figures/ui_switch_thumb_size.gif" alt="Switch在OFF状态使用 8 px滑块、在ON状态使用 10 px滑块" style="display: block; margin: 0;">

### 独立滑块颜色

```cpp
#include "components/ui_toggle_button.h"

void SetupSwitchThumbColor()
{
    UIToggleButton toggleButton;
    toggleButton.Resize(92, 46);

    toggleButton.SetOnThumbColor(Color::Red());
    toggleButton.SetOffThumbColor(Color::Green());
}
```

<img src="../figures/ui_switch_thumb_color.gif" alt="Switch在OFF状态使用绿色滑块、在ON状态使用红色滑块" style="display: block; margin: 0;">

### 独立滑块边框颜色

```cpp
#include "components/ui_toggle_button.h"

void SetupSwitchBorderColor()
{
    UIToggleButton toggleButton;
    toggleButton.Resize(92, 46);

    toggleButton.SetOnBorderColor(Color::Green());
    toggleButton.SetOffBorderColor(Color::Red());
}
```

<img src="../figures/ui_switch_border_color.gif" alt="Switch在OFF状态使用红色边框、在ON状态使用绿色边框" style="display: block; margin: 0;">

## 特性开关控制

当前功能使用宏开关隔离，ui_lite仓使用ui_lite_enable_switch_config，目前只在hispark_taurus_linux_ex打开。

`/vendor/hisilicon/hispark_taurus_linux_ex/config.json`

```json
{
  "subsystem": "arkui",
  "components": [
    {
      "component": "ui_lite",
      "features": [
        "ui_lite_enable_switch_config = true"
      ]
    }
  ]
}
```
