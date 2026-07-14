# Refresh

可以进行页面下拉操作并显示刷新动效的容器组件。

> **说明：**
>
> - 该组件从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 该组件从API version 12开始支持与垂直滚动的[Swiper]{@link swiper}和
> [Web](docroot://reference/apis-arkui/arkui-js/js-components-basic-web.md)的联动。当[Swiper]{@link swiper}设置
> [loop]{@link SwiperAttribute#loop}属性为true时，Refresh无法和[Swiper]{@link swiper}产生联动。
>
> - Refresh和内容大小小于组件自身的[List]{@link list}组件嵌套使用并且中间还有其他组件时，手势可能会被中间组件响应，导致Refresh未产生下拉刷新效果，可以将
> [alwaysEnabled]{@link EdgeEffectOptions}参数设为true，此时[List]{@link list}会响应手势并通过嵌套滚动带动Refresh组件产生下拉刷新效果，具体可以参考
> [示例9（不满一屏场景实现下拉刷新）](docroot://reference/apis-arkui/arkui-ts/ts-container-refresh.md#示例9不满一屏场景实现下拉刷新)。
>
> - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link common}进行处理。
>
> - 组件无法通过鼠标按下拖动操作进行下拉刷新。


## Refresh

```TypeScript
Refresh(value: RefreshOptions)
```

创建Refresh容器。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RefreshOptions | 是 | 刷新组件参数。 |

## 汇总

- [RefreshOptions](arkts-arkui-refresh-refreshoptions-i.md)
- [RefreshStatus](arkts-arkui-refresh-refreshstatus-e.md)
