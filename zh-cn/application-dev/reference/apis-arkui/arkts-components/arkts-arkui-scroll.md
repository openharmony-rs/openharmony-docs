# Scroll

可滚动的容器组件，当子组件的布局尺寸超过父组件的尺寸时，内容可以滚动。支持设置滚动方向、滚动条、边缘效果、嵌套滚动以及自由滚动缩放等能力，适用于内容超出显示区域或需要复杂滚动交互的场景。 > **说明：** > > - 该组件嵌套List子组件滚动时，若List不设置宽高，则默认全部加载。在对性能有要求的场景下，开发者应指定List的宽高，以避免默认全部加载影响性能。 > > - 该组件滚动的前提是主轴方向大小小于内容大小。 > > - Scroll组件通用属性[clip]{@link CommonMethod#clip(value: boolean)}的默认值为true。 > > - Scroll组件的高度超出屏幕显示范围时，可以通过设置通用属性[layoutWeight]{@link CommonMethod#layoutWeight}让Scroll高度适应主轴的剩余空间。 > > - 手指触摸屏幕时，会停止当前触摸范围内所有滚动组件的滚动动画（[scrollTo]{@link Scroller#scrollTo}和[scrollToIndex]{@link Scroller#scrollToIndex}接口 > 触发的滚动动画除外），包括边缘回弹动画。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link ./common}进行处理。

## 子组件 支持单个子组件。 > 从API version 21开始，Scroll单个子组件的宽高最大为16777216px；API version 20及之前，Scroll单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## Scroll

```TypeScript
Scroll(scroller?: Scroller)
```

创建Scroll滚动容器。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollInterface-(scroller?: Scroller): ScrollAttribute--><!--Device-ScrollInterface-(scroller?: Scroller): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

## 汇总

