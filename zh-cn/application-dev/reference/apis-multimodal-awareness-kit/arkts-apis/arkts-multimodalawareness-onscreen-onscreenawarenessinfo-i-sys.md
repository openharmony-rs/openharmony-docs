# OnscreenAwarenessInfo（系统接口）

屏上感知返回信息列表。

**起始版本：** 23

<!--Device-onScreen-export interface OnscreenAwarenessInfo--><!--Device-onScreen-export interface OnscreenAwarenessInfo-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## appIndex

```TypeScript
appIndex?: int
```

应用索引。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-appIndex?: int--><!--Device-OnscreenAwarenessInfo-appIndex?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## appName

```TypeScript
appName?: string
```

应用名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-appName?: string--><!--Device-OnscreenAwarenessInfo-appName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

应用包名。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-bundleName?: string--><!--Device-OnscreenAwarenessInfo-bundleName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## collectStrategy

```TypeScript
collectStrategy?: int
```

页面采集策略，是 [CollectStrategy](arkts-multimodalawareness-onscreen-collectstrategy-e-sys.md) 的按位或运算组合。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-collectStrategy?: int--><!--Device-OnscreenAwarenessInfo-collectStrategy?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## displayId

```TypeScript
displayId?: long
```

屏幕ID。

**类型：** long

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-displayId?: long--><!--Device-OnscreenAwarenessInfo-displayId?: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## entityInfo

```TypeScript
entityInfo?: EntityInfo[]
```

实体信息。

**类型：** EntityInfo[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-entityInfo?: EntityInfo[]--><!--Device-OnscreenAwarenessInfo-entityInfo?: EntityInfo[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## items

```TypeScript
items?: AwarenessItem[]
```

数据项信息。

**类型：** [AwarenessItem](arkts-multimodalawareness-onscreen-awarenessitem-i-sys.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-items?: AwarenessItem[]--><!--Device-OnscreenAwarenessInfo-items?: AwarenessItem[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## languageInfo

```TypeScript
languageInfo?: string
```

页面语言信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-languageInfo?: string--><!--Device-OnscreenAwarenessInfo-languageInfo?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## miniProgramId

```TypeScript
miniProgramId?: string
```

小程序ID，如微信、支付宝等三方应用小程序ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-miniProgramId?: string--><!--Device-OnscreenAwarenessInfo-miniProgramId?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## miniProgramName

```TypeScript
miniProgramName?: string
```

小程序名称，三方应用小程序名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-miniProgramName?: string--><!--Device-OnscreenAwarenessInfo-miniProgramName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## pageId

```TypeScript
pageId?: string
```

应用页面ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-pageId?: string--><!--Device-OnscreenAwarenessInfo-pageId?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## pageTags

```TypeScript
pageTags?: string[]
```

页面标签信息。

**类型：** string[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-pageTags?: string[]--><!--Device-OnscreenAwarenessInfo-pageTags?: string[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## resultCode

```TypeScript
resultCode: int
```

返回码，默认0 表示成功。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-resultCode: int--><!--Device-OnscreenAwarenessInfo-resultCode: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## sampleId

```TypeScript
sampleId?: string
```

采集记录ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-sampleId?: string--><!--Device-OnscreenAwarenessInfo-sampleId?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp: long
```

表示进入特定页面的时间戳，单位：ms。

**类型：** long

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-timestamp: long--><!--Device-OnscreenAwarenessInfo-timestamp: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid?: string
```

表示应用UID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-uid?: string--><!--Device-OnscreenAwarenessInfo-uid?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId?: int
```

窗口ID。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessInfo-windowId?: int--><!--Device-OnscreenAwarenessInfo-windowId?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

