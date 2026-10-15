# ScrollSnapOffsetProvider

```TypeScript
declare interface ScrollSnapOffsetProvider
```

提供可滚动组件两阶段滚动限位偏移量。

偏移量单位为vp，速度单位为vp/s。回调在UI线程同步调用，且必须是纯计算。不提供布局快照；自定义提供方需要自行维护或推导item几何信息。velocity为逻辑内容滚动偏移量对时间的导数，向内容末端为正；组件负责归一化反向布局和RTL方向。decayOffset为自然摩擦衰减距离的非负幅值。

**起始版本：** 26.2.0

<!--Device-unnamed-declare interface ScrollSnapOffsetProvider--><!--Device-unnamed-declare interface ScrollSnapOffsetProvider-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## calculateApproachOffset

```TypeScript
calculateApproachOffset(velocity: number, decayOffset: number): number
```

每次惯性滚动期间仅调用一次，用于计算趋近偏移量。

返回值为非负有限距离幅值，可以大于或等于decayOffset。返回非有限值、负数或回调异常时回退到自然衰减偏移量。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-ScrollSnapOffsetProvider-calculateApproachOffset(velocity: number, decayOffset: number): number--><!--Device-ScrollSnapOffsetProvider-calculateApproachOffset(velocity: number, decayOffset: number): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | 当前惯性滚动速度，向内容末端为正，单位vp/s。 |
| decayOffset | number | 是 | 自然摩擦衰减距离的非负幅值，单位vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 趋近偏移量大小，单位vp。 |

## calculateSnapOffset

```TypeScript
calculateSnapOffset(velocity: number): number
```

每次趋近运动切换到最终限位动画时仅调用一次，用于计算目标偏移量。

返回值为绝对内容滚动目标，0是合法目标；有限目标超出合法滚动范围时会被限制到范围内。返回非有限值或回调异常时，使用组件的兜底目标。Grid自定义策略保持在趋近阶段结束位置，不返回手势起始位置。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-ScrollSnapOffsetProvider-calculateSnapOffset(velocity: number): number--><!--Device-ScrollSnapOffsetProvider-calculateSnapOffset(velocity: number): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | 本次趋近阶段开始时的速度，向内容末端为正，单位vp/s。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 目标滚动绝对偏移量，单位vp。 |
