# TabContentInfo

TabContent页面的切换信息。

**起始版本：** 12

<!--Device-uiObserver-export interface TabContentInfo--><!--Device-uiObserver-export interface TabContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## id

```TypeScript
id: string
```

Tabs组件的id。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInfo-id: string--><!--Device-TabContentInfo-id: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

TabContent组件的下标索引。索引从0开始。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInfo-index: number--><!--Device-TabContentInfo-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lastIndex

```TypeScript
lastIndex?: number
```

最近一次聚焦的TabsContent组件的下标索引。索引从0开始。仅在 [on('tabChange')](arkts-arkui-arkui-uicontext-uiobserver-c.md#on-23)的回调函数中存在。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInfo-lastIndex?: number--><!--Device-TabContentInfo-lastIndex?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: TabContentState
```

TabContent组件的状态。

**类型：** TabContentState

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInfo-state: TabContentState--><!--Device-TabContentInfo-state: TabContentState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabContentId

```TypeScript
tabContentId: string
```

TabContent id.

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInfo-tabContentId: string--><!--Device-TabContentInfo-tabContentId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabContentUniqueId

```TypeScript
tabContentUniqueId: number
```

TabContent uniqueId.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInfo-tabContentUniqueId: number--><!--Device-TabContentInfo-tabContentUniqueId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId: number
```

Tabs组件的uniqueId。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInfo-uniqueId: number--><!--Device-TabContentInfo-uniqueId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

