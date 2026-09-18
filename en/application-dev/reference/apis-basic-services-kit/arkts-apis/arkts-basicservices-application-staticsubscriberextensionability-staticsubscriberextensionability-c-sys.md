# StaticSubscriberExtensionAbility (System API)

This module provides extension abilities of Basic Services Kit for static subscribers, which can be used to subscribe to common events in static mode. Static subscription enables receiving common events without keeping the app running in the background. This ability is applicable to scenarios where system services or system apps need to perform background processing when specific common events occur.

**StaticSubscriberExtensionAbility** provides the **onReceiveEvent** method and the **context** attribute. The **context** attribute is of the **StaticSubscriberExtensionContext** type, which is the running context of the extension ability. It is inherited from **ExtensionContext** and provides **startAbility** to start other abilities in the same app during event processing.

**APIs used in combination**

The typical process of this module is as follows: Inherit the base class, override **onReceiveEvent**, start a callback, read the event data, and start the target ability. Note that **context.startAbility** can start only the abilities that belong to the same app as the current **StaticSubscriberExtensionAbility**.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { StaticSubscriberExtensionAbility } from '@kit.BasicServicesKit';
```

## onReceiveEvent

```TypeScript
onReceiveEvent(event: CommonEventData): void
```

Defines a callback to be invoked when a common event is triggered in static mode.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [CommonEventData](arkts-basicservices-commoneventdata-commoneventdata-i.md) | Yes | Common event data received through static subscription. |

**Examples**

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

Context of the extension ability subscribed to in static mode.

**Type:** [StaticSubscriberExtensionContext](arkts-basicservices-application-staticsubscriberextensioncontext-staticsubscriberextensioncontext-c-sys.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
