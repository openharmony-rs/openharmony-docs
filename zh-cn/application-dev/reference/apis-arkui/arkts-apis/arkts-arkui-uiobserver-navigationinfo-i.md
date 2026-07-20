# NavigationInfo

Navigation组件信息。

**起始版本：** 12

<!--Device-uiObserver-export interface NavigationInfo--><!--Device-uiObserver-export interface NavigationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## navigationId

```TypeScript
navigationId: string
```

Navigation组件的id。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInfo-navigationId: string--><!--Device-NavigationInfo-navigationId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pathStack

```TypeScript
pathStack: NavPathStack
```

Navigation组件的导航控制器。

**类型：** NavPathStack

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInfo-pathStack: NavPathStack--><!--Device-NavigationInfo-pathStack: NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId?: number
```

Navigation组件的uniqueId，可以通过[queryNavigationInfo](../arkts-components/arkts-arkui-basecustomcomponent-c.md#querynavigationinfo-1)获取。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInfo-uniqueId?: number--><!--Device-NavigationInfo-uniqueId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

