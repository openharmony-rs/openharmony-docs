# CommonOptions

CommonOptions定义了Counter的通用属性和事件。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onHoverDecrease

```TypeScript
onHoverDecrease?: (isHover: boolean) => void
```

鼠标进入或退出Counter组件的减少按钮时触发该回调。使用场景：当鼠标悬浮在减少按钮上，需要执行自定义操作（如改变按钮样式、显示提示信息等）时传入此回调。isHover：表示鼠标是否悬浮在减少按钮上，鼠标进入时为true，退出时为false。默认值：不触发鼠标进入或退出Counter组件的减少按钮时的回调。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isHover | boolean | 是 |  |

## onHoverIncrease

```TypeScript
onHoverIncrease?: (isHover: boolean) => void
```

鼠标进入或退出Counter组件的增加按钮时触发该回调。使用场景：当鼠标悬浮在增加按钮上，需要执行自定义操作（如改变按钮样式、显示提示信息等）时传入此回调。isHover：表示鼠标是否悬浮在增加按钮上，鼠标进入时为true，退出时为false。默认值：不触发鼠标进入或退出Counter组件的增加按钮时的回调。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isHover | boolean | 是 |  |

## focusable

```TypeScript
focusable?: boolean
```

设置Counter是否可获焦。  
**说明：**该属性对列表型和紧凑型Counter生效，对数值内联型和日期内联型Counter不生效。默认值：true true：Counter可获焦（当需要通过键盘或焦点导航操作Counter时选择）；false：Counter不可获焦（当不需要焦点交互时选择）。值为undefined时，按默认值处理。

**类型：** boolean

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

设置Counter的步长。当需要快速调整数值时（如设置大于默认值1的步长），或需要精确控制每次变化量时使用。取值范围：大于等于1的整数。默认值：1超出取值范围按默认值处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
