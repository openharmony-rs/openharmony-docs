# EventInfo

界面变更事件。

**起始版本：** 7

<!--Device-accessibility-class EventInfo--><!--Device-accessibility-class EventInfo-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## constructor

```TypeScript
constructor(jsonObject: Object)
```

构造函数，通过JSON对象构造EventInfo实例。

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-constructor(jsonObject: Object)--><!--Device-EventInfo-constructor(jsonObject: Object)-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jsonObject | Object | 是 | 包含 type、bundleName 和 triggerAction 三个字段的 JSON对象，详见示例。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

```

## constructor

```TypeScript
constructor(type: EventType, bundleName: string, triggerAction: Action)
```

构造函数，通过独立参数构造EventInfo实例。

**起始版本：** 11

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-constructor(type: EventType, bundleName: string, triggerAction: Action)--><!--Device-EventInfo-constructor(type: EventType, bundleName: string, triggerAction: Action)-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [EventType](../../apis-arkts/arkts-apis/arkts-arkts-xml-eventtype-e.md) | 是 | 无障碍事件类型。 |
| bundleName | string | 是 | 目标应用名。 |
| triggerAction | [Action](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-action-e.md) | 是 | 触发事件的 Action。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo = new accessibility.EventInfo('click', 'com.example.MyApplication', 'click');

```

## beginIndex

```TypeScript
beginIndex?: number
```

画面显示条目的开始序号，默认值为0。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-beginIndex?: int--><!--Device-EventInfo-beginIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## bundleName

```TypeScript
bundleName: string
```

目标应用名；不可缺省。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-bundleName: string--><!--Device-EventInfo-bundleName: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
componentType?: string
```

应与事件源组件类型对应，默认值为空。

例如：

- 按钮Button类型->'Button'。  
- 图片Image类型->'Image'。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-componentType?: string--><!--Device-EventInfo-componentType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## contents

```TypeScript
contents?: Array<string>
```

内容列表，根据实际场景设置，无特殊限制，默认值为空。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-contents?: Array<string>--><!--Device-EventInfo-contents?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## currentIndex

```TypeScript
currentIndex?: number
```

当前条目序号，默认值为0。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-currentIndex?: int--><!--Device-EventInfo-currentIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## customId

```TypeScript
customId?: string
```

主动聚焦的组件ID，默认值为空。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-customId?: string--><!--Device-EventInfo-customId?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## description

```TypeScript
description?: string
```

事件描述，根据实际场景设置，无特殊限制，默认值为空。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-description?: string--><!--Device-EventInfo-description?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## elementId

```TypeScript
elementId?: number
```

组件elementId，默认值为0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-elementId?: int--><!--Device-EventInfo-elementId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## endIndex

```TypeScript
endIndex?: number
```

画面显示条目的结束序号，默认值为0。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-endIndex?: int--><!--Device-EventInfo-endIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## itemCount

```TypeScript
itemCount?: number
```

条目总数，默认值为0。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-itemCount?: int--><!--Device-EventInfo-itemCount?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## lastContent

```TypeScript
lastContent?: string
```

最新内容，根据实际场景设置，无特殊限制，默认值为空。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-lastContent?: string--><!--Device-EventInfo-lastContent?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
pageId ?: number
```

事件源的页面ID，默认值为0。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-pageId ?: int--><!--Device-EventInfo-pageId ?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textAnnouncedForAccessibility

```TypeScript
textAnnouncedForAccessibility?: string
```

主动播报的内容。当应用需要主动播报时，根据实际场景设置播报内容，无特殊限制，默认值为空。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-textAnnouncedForAccessibility?: string--><!--Device-EventInfo-textAnnouncedForAccessibility?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textMoveUnit

```TypeScript
textMoveUnit?: TextMoveUnit
```

文本移动粒度，默认值为char。

**类型：** TextMoveUnit

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-textMoveUnit?: TextMoveUnit--><!--Device-EventInfo-textMoveUnit?: TextMoveUnit-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textResourceAnnouncedForAccessibility

```TypeScript
textResourceAnnouncedForAccessibility?: Resource
```

主动播报的内容支持传入Resource类型，且只能传入string。

**类型：** Resource

**起始版本：** 18

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-textResourceAnnouncedForAccessibility?: Resource--><!--Device-EventInfo-textResourceAnnouncedForAccessibility?: Resource-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## triggerAction

```TypeScript
triggerAction: Action
```

触发事件的Action，不可缺省。

**类型：** Action

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-triggerAction: Action--><!--Device-EventInfo-triggerAction: Action-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## type

```TypeScript
type: EventType
```

无障碍事件类型，不可缺省。

**类型：** EventType

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-type: EventType--><!--Device-EventInfo-type: EventType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## windowUpdateType

```TypeScript
windowUpdateType?: WindowUpdateType
```

窗口变化类型。

**类型：** WindowUpdateType

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-windowUpdateType?: WindowUpdateType--><!--Device-EventInfo-windowUpdateType?: WindowUpdateType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

