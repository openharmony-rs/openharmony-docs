# GridRowColumnOption

栅格在不同宽度设备类型下的栅格列数配置。 API version 20之前，仅配置部分断点下GridRow组件的栅格列数，取已配置的相邻较小断点（如md的相邻较小断点为sm）的栅格列数补全未配置的栅格列数。若未配置相邻较小断点的栅格列数，以默认栅格列数12补全未配置的栅格列 数。 &lt;!--code_no_check--&gt; API version 20及以后，仅配置部分断点下GridRow组件的栅格列数，取已配置的相邻较小断点的栅格列数补全未配置的栅格列数。若未配置相邻较小断点的栅格列数，取已配置的更大断点的栅格列数补全未配置的栅格列数。 &lt;!--code_no_check--&gt; 建议手动配置不同断点下GridRow组件的栅格列数，避免默认补全的栅格列数的布局效果不符合预期。 每列栅格的宽度为GridRow的内容区大小减去栅格子组件的间距gutter，再除以总的栅格列数。比如，宽800vp的GridRow设置columns为12，gutter设置为10vp，padding设置为20vp，那么每列栅格的宽度为 (800 - 20 * 2 - 10 * 11) / 12。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare interface GridRowColumnOption--><!--Device-unnamed-declare interface GridRowColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lg

```TypeScript
lg?: number
```

在大宽度类型设备上，栅格容器组件的栅格列数。取值为大于0的整数。 - API version 20之前：默认值为12。 - API version 20及之后：默认值为12。 非法值：按默认值处理。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowColumnOption-lg?: number--><!--Device-GridRowColumnOption-lg?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## md

```TypeScript
md?: number
```

在中等宽度类型设备上，栅格容器组件的栅格列数。取值为大于0的整数。 - API version 20之前：默认值为12。 - API version 20及之后：默认值为8。 非法值：按默认值处理。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowColumnOption-md?: number--><!--Device-GridRowColumnOption-md?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sm

```TypeScript
sm?: number
```

在小宽度类型设备上，栅格容器组件的栅格列数。取值为大于0的整数。 - API version 20之前：默认值为12。 - API version 20及之后：默认值为4。 非法值：按默认值处理。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowColumnOption-sm?: number--><!--Device-GridRowColumnOption-sm?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xl

```TypeScript
xl?: number
```

在特大宽度类型设备上，栅格容器组件的栅格列数。取值为大于0的整数。 - API version 20之前：默认值为12。 - API version 20及之后：默认值为12。 非法值：按默认值处理。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowColumnOption-xl?: number--><!--Device-GridRowColumnOption-xl?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xs

```TypeScript
xs?: number
```

在最小宽度类型设备上，栅格容器组件的栅格列数。取值为大于0的整数。 - API version 20之前：默认值为12。 - API version 20及之后：默认值为2。 非法值：按默认值处理。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowColumnOption-xs?: number--><!--Device-GridRowColumnOption-xs?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xxl

```TypeScript
xxl?: number
```

在超大宽度类型设备上，栅格容器组件的栅格列数。取值为大于0的整数。 - API version 20之前：默认值为12。 - API version 20及之后：默认值为12。 非法值：按默认值处理。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowColumnOption-xxl?: number--><!--Device-GridRowColumnOption-xxl?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

