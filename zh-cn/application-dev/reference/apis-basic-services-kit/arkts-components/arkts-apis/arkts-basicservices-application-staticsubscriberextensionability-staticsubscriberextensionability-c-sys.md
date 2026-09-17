# StaticSubscriberExtensionAbility（系统接口）

本模块是 BasicServicesKit 提供的静态订阅扩展能力基类，用于实现静态公共事件订阅。静态订阅是一种无需应用常驻运行即可接收公共事件的订阅方式。该能力适用于系统服务或系统应用需要在特定公共事件发生时执行后台处理的场景。

`StaticSubscriberExtensionAbility`基类提供两个关键成员：`onReceiveEvent`方法与`context`属性。`context`属性类型为 StaticSubscriberExtensionContext，是扩展能力的运行上下文，继承自`ExtensionContext`，提供`startAbility`方法用于在事件处理过程中拉起同应用内的其他 Ability。

**API 组合使用关系说明：**

本模块典型使用流程为"继承基类 → 重写`onReceiveEvent` → 系统拉起回调 → 读取事件数据 → 拉起目标 Ability"。需注意，`context.startAbility`仅能拉起与当前`StaticSubscriberExtensionAbility`属于同一应用的 Ability。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { StaticSubscriberExtensionAbility } from '@kit.BasicServicesKit';
```

## onReceiveEvent

```TypeScript
onReceiveEvent(event: CommonEventData): void
```

静态订阅公共事件的回调函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [CommonEventData](arkts-basicservices-commoneventdata-commoneventdata-i.md) | 是 | 静态订阅接收到的公共事件数据。 |

**示例**

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

静态订阅ExtensionAbility的上下文。

**类型：** [StaticSubscriberExtensionContext](arkts-basicservices-application-staticsubscriberextensioncontext-staticsubscriberextensioncontext-c-sys.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
