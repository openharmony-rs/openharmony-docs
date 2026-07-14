# Stepper

步骤导航器组件，适用于引导用户按照步骤完成任务的导航场景。

> **说明：**

> - 从API version 8开始支持，从API version 22开始废弃，建议使用[Swiper]{@link swiper}替代。详细示例请参考
> [示例2](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-stepper.md#示例2使用swiper替代stepper)。


## Stepper

```TypeScript
Stepper(value?: { index?: number })
```

Called when the stepper component is used.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** <!--SUBSTITUTE_API-->Swiper.SwiperAttribute#index<!--/SUBSTITUTE_API-->

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { index?: number } | 否 | Index of the **StepperItem** that is currently displayed.<br>Default value: **0**<br>Since API version 10, this parameter supports two-way binding through[$$](docroot://ui/state-management/arkts-two-way-sync.md). |

## 汇总

