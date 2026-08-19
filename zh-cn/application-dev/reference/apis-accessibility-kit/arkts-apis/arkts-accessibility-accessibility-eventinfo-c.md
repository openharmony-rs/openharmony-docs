# EventInfo

无障碍事件信息，用于描述界面变更或交互事件，作为[sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md)的参数定义事件的类型和触发动作。发送的无障碍事 件将被系统分发到已注册且匹配事件类型的辅助应用进行响应，详见[sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md)。

**起始版本：** 23

<!--Device-accessibility-class EventInfo--><!--Device-accessibility-class EventInfo-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
import { GesturePath } from '@kit.AccessibilityKit';
import { GesturePoint } from '@kit.AccessibilityKit';
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
| jsonObject | Object | 是 | 包含type、bundleName和triggerAction三个字段的JSON对象，详见示例。 |

**示例**

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
constructor()
```

A constructor used to create a EventInfo object.

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-constructor()--><!--Device-EventInfo-constructor()-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**示例**

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

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-constructor(type: EventType, bundleName: string, triggerAction: Action)--><!--Device-EventInfo-constructor(type: EventType, bundleName: string, triggerAction: Action)-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | EventType | 是 | 无障碍事件类型。 |
| bundleName | string | 是 | 目标应用的Bundle名称。 |
| triggerAction | Action | 是 | 触发事件的Action。 |

**示例**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

// 参数依次为：type、bundleName、triggerAction。
let eventInfo = new accessibility.EventInfo('click', 'com.example.MyApplication', 'click');
```

## beginIndex

```TypeScript
beginIndex?: int
```

画面显示条目的开始序号，默认值为0。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-beginIndex?: int--><!--Device-EventInfo-beginIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## bundleName

```TypeScript
bundleName: string
```

目标应用的Bundle名称；不可缺省。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-bundleName: string--><!--Device-EventInfo-bundleName: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
componentType?: string
```

应与事件源组件类型对应，默认值为空。 例如： - 按钮Button类型->'Button'。 - 图片Image类型->'Image'。

**类型：** string

**起始版本：** 23

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

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-contents?: Array<string>--><!--Device-EventInfo-contents?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## currentIndex

```TypeScript
currentIndex?: int
```

当前条目序号，默认值为0。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-currentIndex?: int--><!--Device-EventInfo-currentIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## customId

```TypeScript
customId?: string
```

主动聚焦的组件ID，当应用需要主动聚焦时根据实际场景设置，默认值为空。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-customId?: string--><!--Device-EventInfo-customId?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## description

```TypeScript
description?: string
```

事件描述，由开发者根据业务需要自定义描述内容，无特殊限制，默认值为空。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-description?: string--><!--Device-EventInfo-description?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## elementId

```TypeScript
elementId?: int
```

组件elementId，默认值为0。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-elementId?: int--><!--Device-EventInfo-elementId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## endIndex

```TypeScript
endIndex?: int
```

画面显示条目的结束序号，默认值为0。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-endIndex?: int--><!--Device-EventInfo-endIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## itemCount

```TypeScript
itemCount?: int
```

条目总数，默认值为0。

**类型：** int

**起始版本：** 23

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

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-lastContent?: string--><!--Device-EventInfo-lastContent?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
pageId ?: int
```

事件源的页面ID，默认值为0。

**类型：** int

**起始版本：** 23

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

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-textAnnouncedForAccessibility?: string--><!--Device-EventInfo-textAnnouncedForAccessibility?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textMoveUnit

```TypeScript
textMoveUnit?: TextMoveUnit
```

文本移动粒度，默认值为char。

**类型：** [TextMoveUnit](arkts-accessibility-accessibility-textmoveunit-t.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-textMoveUnit?: TextMoveUnit--><!--Device-EventInfo-textMoveUnit?: TextMoveUnit-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textResourceAnnouncedForAccessibility

```TypeScript
textResourceAnnouncedForAccessibility?: Resource
```

主动播报的内容支持传入Resource类型，且Resource只能引用string类型资源（如\$r('app.string.xxx')）。

**类型：** Resource

**起始版本：** 23

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

**起始版本：** 23

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

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-type: EventType--><!--Device-EventInfo-type: EventType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## windowUpdateType

```TypeScript
windowUpdateType?: WindowUpdateType
```

窗口变化类型。

**类型：** [WindowUpdateType](arkts-accessibility-accessibility-windowupdatetype-t.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EventInfo-windowUpdateType?: WindowUpdateType--><!--Device-EventInfo-windowUpdateType?: WindowUpdateType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

