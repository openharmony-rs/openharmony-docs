# StaticSubscriberExtensionAbility（系统接口）

StaticSubscriberExtensionAbilityģ���ṩ��̬������ExtensionAbility����������

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onReceiveEvent

```TypeScript
onReceiveEvent(event: CommonEventData): void
```

��̬������ͨ���¼��ص���

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | CommonEventData | 是 | ��̬������ͨ���¼��ص��� |

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

�����ġ�

**类型：** StaticSubscriberExtensionContext

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

