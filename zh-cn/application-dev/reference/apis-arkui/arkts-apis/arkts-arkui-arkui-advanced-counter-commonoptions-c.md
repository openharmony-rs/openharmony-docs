# CommonOptions

CommonOptions定义了Counter的共通属性和事件。

**起始版本：** 11

<!--Device-unnamed-declare class CommonOptions--><!--Device-unnamed-declare class CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterType, DateData, CounterComponent, CounterOptions } from '@kit.ArkUI';
```

## focusable

```TypeScript
focusable?: boolean
```

设置Counter是否可获焦。

**说明：**

该属性对列表型和紧凑型Counter生效。

默认值：true

true：Counter可获焦；false：Counter不可获焦。

值为undefined时，按默认值处理。

**类型：** boolean

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-focusable?: boolean--><!--Device-CommonOptions-focusable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverDecrease

```TypeScript
onHoverDecrease?: (isHover: boolean) => void
```

鼠标进入或退出Counter组件的减小按钮时触发该回调。

isHover：表示鼠标是否悬浮在组件上，进入时为true，离开时为false。

默认值：不触发鼠标进入或退出Counter组件的减小按钮时的回调。

值为undefined时，按默认值处理。

**类型：** (isHover: boolean) =&gt; void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-onHoverDecrease?: (isHover: boolean) => void--><!--Device-CommonOptions-onHoverDecrease?: (isHover: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverIncrease

```TypeScript
onHoverIncrease?: (isHover: boolean) => void
```

鼠标进入或退出Counter组件的增加按钮时触发该回调。

isHover：表示鼠标是否悬浮在组件上，鼠标进入时为true，退出时为false。

默认值：不触发鼠标进入或退出Counter组件的增加按钮时的回调。

值为undefined时，按默认值处理。

**类型：** (isHover: boolean) =&gt; void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-onHoverIncrease?: (isHover: boolean) => void--><!--Device-CommonOptions-onHoverIncrease?: (isHover: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

设置Counter的步长。

取值范围：大于等于1的整数。

默认值：1

超出取值范围按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-step?: number--><!--Device-CommonOptions-step?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

