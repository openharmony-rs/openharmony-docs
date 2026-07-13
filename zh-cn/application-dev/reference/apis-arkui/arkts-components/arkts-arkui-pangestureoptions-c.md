# PanGestureOptions

定义PanGesture配置参数选项。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value?: { fingers?: number; direction?: PanDirection; distance?: number })
```

创建滑动手势配置参数对象。通过PanGestureOptions对象接口可以动态修改滑动手势的属性，从而避免通过状态变量修改属性（状态变量修改会导致UI刷新）。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { fingers?: number; direction?: PanDirection; distance?: number } | 否 | 滑动手势配置参数对象。<br/>fingers用于指定触发滑动的最少手指数，最小为1指， 最大取值为10指。<br/>默认值：1 <br/>direction用于指定触发滑动的手势方向，此枚举值支持逻辑与(&)和逻辑或（\|）运算。<br/>默认值：PanDirection.All<br/>distance用于指定触发滑动手势事件的最小滑动距离，单位为vp。<br/>手写笔默认值：8，其余输入源默认值：5<br/>**说明：**<br/>[Tabs](arkts-arkui-tabs.md)组件滑动与该滑动手势事件同时存在时，可将distance值设为1，使滑动更灵敏，避免造成事件错乱。<br/>当设定的值小于0时，按默认值处理。<br/>建议设置合理的滑动距离，滑动距离设置过大时会导致滑动不跟手（响应时延慢）的问题。<br/>当组件应用了[scale](arkts-arkui-commonmethod-c.md#scale-1)缩放变换时，distance的实际识别距离会按照scale比例进行缩放。 |

## getDirection

```TypeScript
getDirection(): PanDirection
```

获取滑动方向。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PanDirection | 滑动方向。 |

## getDistance

```TypeScript
getDistance(): number
```

获取触发滑动手势事件的最小滑动距离，单位为vp。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 滑动手势事件的最小滑动距离。 |

## setDirection

```TypeScript
setDirection(value: PanDirection)
```

设置滑动方向。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PanDirection | 是 | 用于指定触发滑动的手势方向，此枚举值支持逻辑与(&)和逻辑或（\|）运算。<br/>默认值：PanDirection.All |

## setDistance

```TypeScript
setDistance(value: number)
```

设置触发滑动手势事件的最小滑动距离，单位为vp。距离值不宜设置过大，避免因滑动脱手、响应时延过大等问题导致性能劣化，最佳实践请参考：
[减小拖动识别距离](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-application-latency-optimization-cases#section1116134115286)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 触发滑动手势事件的最小滑动距离，单位为vp。<br/>手写笔默认值：8，其余输入源默认值：5<br/>**说明：**<br/>[Tabs组件](arkts-arkui-tabs.md)滑动与该滑动手势事件同时存在时，可将distance值设为1，使滑动更灵敏，避免造成事件错乱。<br/>当设定的值小于0时，按默认值处理。<br/>建议设置合理的滑动距离，滑动距离设置过大时会导致滑动不跟手（响应时延慢）的问题。<br/>当组件应用了[scale](arkts-arkui-commonmethod-c.md#scale-1)缩放变换时，distance的实际识别距离会按照scale比例进行缩放。 |

## setFingers

```TypeScript
setFingers(value: number)
```

设置触发滑动的最少手指数。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 触发滑动的最少手指数，最小为1指， 最大取值为10指。<br/>默认值：1 |

