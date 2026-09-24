# NavDestinationSwitchInfo

```TypeScript
export interface NavDestinationSwitchInfo
```

Navigation组件页面切换的信息。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## context

```TypeScript
context: UIAbilityContext | UIContext
```

触发页面切换的Navigation对应的上下文信息。

**类型：** [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: NavDestinationInfo | NavBar
```

页面切换的源页面。

**类型：** [NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md) &#124; NavBar

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operation

```TypeScript
operation: NavigationOperation
```

页面切换操作类型。

**类型：** NavigationOperation

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: NavDestinationInfo | NavBar
```

页面切换的目的页面。

**类型：** [NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md) &#124; NavBar

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
