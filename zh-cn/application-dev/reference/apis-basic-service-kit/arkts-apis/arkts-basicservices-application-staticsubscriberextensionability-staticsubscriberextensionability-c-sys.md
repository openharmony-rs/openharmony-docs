# StaticSubscriberExtensionAbility（系统接口）

StaticSubscriberExtensionAbility模块提供静态订阅者ExtensionAbility类别的能力。

**起始版本：** 9

<!--Device-unnamed-declare class StaticSubscriberExtensionAbility--><!--Device-unnamed-declare class StaticSubscriberExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { StaticSubscriberExtensionAbility } from '@kit.BasicServicesKit';
```

<a id="onreceiveevent"></a>
## onReceiveEvent

```TypeScript
onReceiveEvent(event: CommonEventData): void
```

静态订阅者通用事件回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StaticSubscriberExtensionAbility-onReceiveEvent(event: CommonEventData): void--><!--Device-StaticSubscriberExtensionAbility-onReceiveEvent(event: CommonEventData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [CommonEventData](arkts-basicservices-commoneventdata-commoneventdata-i.md) | 是 | 静态订阅者通用事件回调。 |

**示例：**

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';

class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
  onReceiveEvent(event: commonEventManager.CommonEventData) {
    console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
  }
}

```

## context

```TypeScript
context: StaticSubscriberExtensionContext
```

上下文。

**类型：** StaticSubscriberExtensionContext

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StaticSubscriberExtensionAbility-context: StaticSubscriberExtensionContext--><!--Device-StaticSubscriberExtensionAbility-context: StaticSubscriberExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

