# ItemState

步骤导航器nextLabel的显示状态。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** Swiper

<!--Device-unnamed-declare enum ItemState--><!--Device-unnamed-declare enum ItemState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

正常状态，右侧文本按钮正常显示，可点击进入下一个StepperItem。

**说明：**

从API version 8开始支持，从API version 22开始废弃，建议使用[index](SwiperAttribute#index)替代。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** index

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ItemState-Normal--><!--Device-ItemState-Normal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Disabled

```TypeScript
Disabled
```

不可用状态，右侧文本按钮灰度显示，不可点击进入下一个StepperItem。

**说明：**

从API version 8开始支持，从API version 22开始废弃，建议使用[indicatorInteractive](SwiperAttribute#indicatorInteractive)替代。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** indicatorInteractive

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ItemState-Disabled--><!--Device-ItemState-Disabled-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Waiting

```TypeScript
Waiting
```

等待状态，右侧文本按钮不显示，显示等待进度条，不可点击进入下一个StepperItem。

**说明：**

从API version 8开始支持，从API version 22开始废弃，建议使用[Swiper](arkts-arkui-swiper.md)替代。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** Swiper

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ItemState-Waiting--><!--Device-ItemState-Waiting-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Skip

```TypeScript
Skip
```

跳过状态，右侧文本按钮默认显示“跳过”，此时可在Stepper的onSkip回调中自定义相关逻辑。

**说明：**

从API version 8开始支持，从API version 22开始废弃，建议使用[index](SwiperAttribute#index)替代。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** index

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ItemState-Skip--><!--Device-ItemState-Skip-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

