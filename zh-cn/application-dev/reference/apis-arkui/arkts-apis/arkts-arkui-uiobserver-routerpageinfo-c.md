# RouterPageInfo

RouterPageInfo包含的信息，由系统返回给开发者。

**起始版本：** 11

<!--Device-uiObserver-export class RouterPageInfo--><!--Device-uiObserver-export class RouterPageInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## context

```TypeScript
context: UIAbilityContext | UIContext
```

触发生命周期的routerPage页面对应的上下文信息。

**类型：** UIAbilityContext | UIContext

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RouterPageInfo-context: UIAbilityContext | UIContext--><!--Device-RouterPageInfo-context: UIAbilityContext | UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

触发生命周期的routerPage页面对应的上下文信息。取值应≥0。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RouterPageInfo-index: number--><!--Device-RouterPageInfo-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

触发生命周期的routerPage页面的名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RouterPageInfo-name: string--><!--Device-RouterPageInfo-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pageId

```TypeScript
pageId: string
```

触发生命周期的routerPage页面的唯一标识。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RouterPageInfo-pageId: string--><!--Device-RouterPageInfo-pageId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

触发生命周期的routerPage页面的路径。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RouterPageInfo-path: string--><!--Device-RouterPageInfo-path: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Size
```

routerPage页面的大小，单位是vp。

**类型：** Size

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RouterPageInfo-size?: Size--><!--Device-RouterPageInfo-size?: Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: RouterPageState
```

触发生命周期的routerPage页面的状态。

**类型：** RouterPageState

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RouterPageInfo-state: RouterPageState--><!--Device-RouterPageInfo-state: RouterPageState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

