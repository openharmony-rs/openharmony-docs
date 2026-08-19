# Refresh

Refresh是提供下拉刷新交互的容器组件，适用于列表数据刷新、页面内容更新等需要用户触发数据更新的场景。它支持自定义刷新区域显示内容和文本、设置下拉偏移量和跟手系数、控制最大下拉距离等，可灵活适配不同应用的下拉刷新需求，提供一致且流 畅的刷新体验。 > **说明：** > > - 该组件从API version 12开始支持与垂直滚动的Swiper和 > [Web](../../../reference/apis-arkui/arkui-js/js-components-basic-web.md)的联动。当Swiper设置 > loop属性为true时，Refresh无法和Swiper产生联动。 > > - Refresh和内容大小小于组件自身的List组件嵌套使用并且中间还有其他组件时，手势可能会被中间组件响应，导致Refresh未产生下拉刷新效果。此时可以将 > alwaysEnabled参数设为true，List会响应手势并通过嵌套滚动带动Refresh组件产生下拉刷新效果。具体可以参考 > [示例9（不满一屏场景实现下拉刷新）](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#示例9不满一屏场景实现下拉刷新)。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。 > > - 组件无法通过鼠标按下拖动操作进行下拉刷新。

## 子组件 支持单个子组件。 从API version 11开始，Refresh子组件会跟随手势下拉而下移。

## Refresh

```TypeScript
Refresh(value: RefreshOptions)
```

创建Refresh容器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshInterface-(value: RefreshOptions): RefreshAttribute--><!--Device-RefreshInterface-(value: RefreshOptions): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RefreshOptions](arkts-arkui-refreshoptions-i.md) | 是 | 刷新组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RefreshOptions](arkts-arkui-refreshoptions-i.md) | 用于设置Refresh组件参数。 > **补充说明：** > > - 当未设置builder或refreshingContent时，是通过更新子组件的translate属性实现的下拉 > 位移效果。下拉位移过程中不会触发子组件的 > onAreaChange事件。子组件设置 > translate属性时不会生效。 > > - 当设置了builder或refreshingContent时，是通过更新子组件相对于Refresh组件的位置实现的下拉位移效果。下拉位移过程中可以触发子组件的 > onAreaChange事件。子组件设置 > position属性时会固定子组件相对于Refresh组件的位置，导致子组件不会跟手进行下拉位移。 > > - 通过builder参数设置的自定义组件在未指定宽度和高度时，其尺寸将自适应子组件，在指定宽度而未指定高度时，其高度将自适应下拉距离。通过refreshingContent参数设置的自定义组件若未指定高度，其高度同样会自适应下拉 > 距离。当自定义组件高度自适应下拉距离时，随着下拉距离的增加，该组件的高度亦随之增加；当自定义组件的高度设定为固定值或自适应至最大高度时，随着下拉距离的增加，自定义组件与Refresh组件上边界之间的间距亦会随之增加。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RefreshStatus](arkts-arkui-refreshstatus-e.md) | RefreshStatus刷新状态枚举。 |

