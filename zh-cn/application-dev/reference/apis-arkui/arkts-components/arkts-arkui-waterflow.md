# WaterFlow

瀑布流容器，由“行”和“列”分割的单元格所组成，通过容器自身的排列规则，将不同大小的“项目”自上而下，如瀑布般紧密布局。

> **说明：**
>
> 该组件从API version 9 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> WaterFlow组件支持展示瀑布流布局，不支持编辑模式和子元素拖动功能。
>
> 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link common}进行处理。


## WaterFlow

```TypeScript
WaterFlow(options?: WaterFlowOptions)
```

创建瀑布流容器。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | WaterFlowOptions | 否 | 瀑布流组件参数。 |

## 汇总

- [UIWaterFlowEvent](arkts-arkui-waterflow-uiwaterflowevent-i.md)
- [WaterFlowOptions](arkts-arkui-waterflow-waterflowoptions-i.md)
- [GetItemMainSizeByIndex](arkts-arkui-waterflow-getitemmainsizebyindex-t.md)
- [OnWaterFlowScrollIndexCallback](arkts-arkui-waterflow-onwaterflowscrollindexcallback-t.md)
- [WaterFlowLayoutMode](arkts-arkui-waterflow-waterflowlayoutmode-e.md)
