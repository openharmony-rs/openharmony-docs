# Button组件开发指导

## 功能概述

本模块面向Native侧应用开发。开发者可按需控制按钮按下时的缩放动效行为，并扩大按钮的触摸命中区域以提升小尺寸按钮的易点性。

| 维度     | Button组件能力                          |
| -------- | --------------------------------------------------- |
| 作用对象 | UIButton的点击动效与触摸命中区域                |
| 典型场景 | 按钮点击缩放重复播放、小按钮热区外扩、关闭点击动效 |
| 核心类   | UIButton、UIView                               |

本模块在此基础上提供轻量、可验证的Native API，覆盖 **3 类能力**：

1. 动画重复次数：控制按钮按下时缩放动效播放的次数，0 表示不播放。
2. 热区扩展：向上下左右四个方向扩展按钮的触摸命中区域，不改变布局与绘制区域。
3. 动画效果：支持关闭动效或保留默认缩放动效。

未配置时保持现有默认行为：默认启用缩放动效，默认播放 1 次，默认热区不扩展。

## 功能接口

| 接口 | 参数 | 返回值 | 说明 |
| --- | --- | --- | --- |
| SetAnimationRepeatCount(uint16_t repeatCount) | repeatCount：重复次数 | 无 | 设置动效重复次数；0 表示不播放动效；默认值为 1 |
| GetAnimationRepeatCount() const | 无 | uint16_t | 获取重复次数 |
| SetTouchExpand(int16_t left, int16_t top, int16_t right, int16_t bottom) | left、right：左右扩展值（px）；top、bottom：上下扩展值（px） | 无 | 设置热区扩展值；小于 0、左右扩展值大于屏幕宽度或上下扩展值大于屏幕高度时，对应方向恢复默认值 0；默认四个方向均为 0 |
| GetTouchExpand(int16_t& left, int16_t& top, int16_t& right, int16_t& bottom) const | left、top、right、bottom：用于返回四个方向扩展值的引用参数 | 无 | 获取当前热区扩展配置 |
| GetTouchableRect() const | 无 | Rect | 获取应用热区扩展后的按钮触摸区域 |
| SetAnimationEffect(ButtonAnimationEffect effect) | effect：动画效果 | 无 | 设置动画效果；非法值恢复为BUTTON_ANIMATION_SCALE；默认值为BUTTON_ANIMATION_SCALE |
| GetAnimationEffect() const | 无 | ButtonAnimationEffect | 获取当前动画效果 |
| EnableButtonAnimation(bool enable) | enable：是否启用按钮动画 | 无 | 启用或关闭按钮动画；true使用BUTTON_ANIMATION_SCALE，false使用BUTTON_ANIMATION_NONE；默认值为true |
| GetEnableButtonAnimation() const | 无 | bool | 查询按钮动画是否启用 |

## 功能示例

[示例工程](https://gitcode.com/openharmony/applications_sample_camera/tree/master/graphic)

### 热区扩展、动画重复次数与动画效果

```cpp
#include "components/ui_label_button.h"

void SetupButton()
{
    UILabelButton button;
    button.SetPosition(70, 25, 100, 30);
    button.SetText("SCALE");

    button.SetTouchExpand(10, 10, 10, 10);

    button.SetAnimationRepeatCount(3);

    button.SetAnimationEffect(UIButton::BUTTON_ANIMATION_SCALE);
}
```

<img src="../figures/ui_button_animation_effect.gif" alt="Button扩展热区并连续播放 3 次缩放动效" style="display: block; margin: 0;">

## 特性开关控制

当前功能使用宏开关隔离，ui_lite仓使用ui_lite_enable_button_animation_touch_extend_config，目前只在hispark_taurus_linux_ex打开。

`/vendor/hisilicon/hispark_taurus_linux_ex/config.json`

```json
{
  "subsystem": "arkui",
  "components": [
    {
      "component": "ui_lite",
      "features": [
        "ui_lite_enable_button_animation_touch_extend_config = true"
      ]
    }
  ]
}
```
