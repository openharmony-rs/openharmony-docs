# Refresh

Refresh是提供下拉刷新交互的容器组件，适用于列表数据刷新、页面内容更新等需要用户触发数据更新的场景。它支持自定义刷新区域显示内容和文本、设置下拉偏移量和跟手系数、控制最大下拉距离等，可灵活适配不同应用的下拉刷新需求，提供一致且流 畅的刷新体验。 > **说明：** > > - 该组件从API version 12开始支持与垂直滚动的Swiper和 > [Web](../../../reference/apis-arkui/arkui-js/js-components-basic-web.md)的联动。当Swiper设置 > loop属性为true时，Refresh无法和Swiper产生联动。 > > - Refresh和内容大小小于组件自身的List组件嵌套使用并且中间还有其他组件时，手势可能会被中间组件响应，导致Refresh未产生下拉刷新效果。此时可以将 > alwaysEnabled参数设为true，List会响应手势并通过嵌套滚动带动Refresh组件产生下拉刷新效果。具体可以参考 > [示例9（不满一屏场景实现下拉刷新）](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#示例9不满一屏场景实现下拉刷新)。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。 > > - 组件无法通过鼠标按下拖动操作进行下拉刷新。

## 子组件 支持单个子组件。 从API version 11开始，Refresh子组件会跟随手势下拉而下移。

## Refresh

```TypeScript
Refresh(value: RefreshOptions)
```

创建Refresh容器。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshInterface-(value: RefreshOptions): RefreshAttribute--><!--Device-RefreshInterface-(value: RefreshOptions): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RefreshOptions](arkts-arkui-refreshoptions-i.md) | 是 | 刷新组件参数。 |

## 汇总

- [RefreshOptions](arkts-arkui-refreshoptions-i.md)
- [RefreshStatus](arkts-arkui-refreshstatus-e.md)
