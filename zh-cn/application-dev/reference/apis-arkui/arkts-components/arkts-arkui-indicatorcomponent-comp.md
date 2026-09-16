# IndicatorComponent

Defines IndicatorComponent.

## IndicatorComponent

```TypeScript
IndicatorComponent(controller?: IndicatorComponentController)
```

Called when a indicator is set.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md) | 否 | indicator component controller. |

## 汇总

## 示例

```TypeScript
### 示例1（圆点单独导航点与Swiper绑定使用）

该示例通过[Swiper](ts-container-swiper.md)组件的[indicator](ts-container-swiper.md#indicator)接口与[IndicatorComponent](#indicatorcomponent)的构造函数绑定同一[IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md)对象，实现了圆点单独导航点与Swiper的交互。


```

```TypeScript
### 示例2（数字单独导航点与Swiper绑定使用）

该示例通过[Swiper](ts-container-swiper.md)组件的[indicator](ts-container-swiper.md#indicator)接口与[IndicatorComponent](#indicatorcomponent)的构造函数绑定同一[IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md)对象，实现了数字单独导航点与Swiper的交互。
```
