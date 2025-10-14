# @ohos.app.ability.FenceExtensionAbility (FenceExtensionAbility)
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @liu-binjun-->
<!--Designer: @liu-binjun-->
<!--Tester: @mhy123456789-->
<!--Adviser: @RayShih-->

The **FenceExtensionAbility** class provides geofence-related capabilities. It is inherited from the **ExtensionAbility** class.

> **NOTE**
>
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model. 

## Modules to Import

```ts
import { FenceExtensionAbility } from '@kit.LocationKit';
```

## FenceExtensionAbility

Provides geofence-related capabilities. It is inherited from the **ExtensionAbility** class.

### Attributes

**System capability**: SystemCapability.Location.Location.Geofence

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [FenceExtensionContext](js-apis-app-ability-FenceExtensionContext.md) | No| No| Context of the Geofence service.|

### onFenceStatusChange

onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record&lt;string, string&gt;): void;

Represents the callback triggered when a geofence status change event is received. Service processing is then performed based on the event type and data.

**System capability**: SystemCapability.Location.Location.Geofence

**Parameters**
| Name|  Type| Mandatory | Description |
| ------------ | ------------ | ------------ | ------------ |
| transition |  [geoLocationManager.GeofenceTransition](js-apis-geoLocationManager.md#geofencetransition12) |  Yes| Geofence transition information, including the geofence ID and geofence event. |
| additions  | Record&lt;string, string&gt;  | Yes | Additional information. |

**Example**

```ts
import { FenceExtensionAbility, geoLocationManager } from '@kit.LocationKit';
import { notificationManager } from '@kit.NotificationKit';
import { Want, wantAgent } from '@kit.AbilityKit';

export class MyFenceExtensionAbility extends FenceExtensionAbility {
  onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void {
    // Receive the geofence status change event and process the service logic.
    console.info(`on geofence transition,id:${transition.geofenceId},event:${transition.transitionEvent},additions:${JSON.stringify(additions)}`);

    // Send a geofence notification.
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility',
          parameters:
          {
            "geofenceId": transition?.geofenceId,
            "transitionEvent": transition?.transitionEvent,
          }
        } as Want
      ],
      actionType: wantAgent.OperationType.START_ABILITY,
      requestCode: 100
    };
    wantAgent.getWantAgent(wantAgentInfo).then((wantAgentMy) => {
      let notificationRequest: notificationManager.NotificationRequest = {
        id: 1,
        content: {
          notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
          normal: {
            title: "Geofence Notification",
            text: `on geofence transition,id:${transition.geofenceId},event:${transition.transitionEvent},additions:${JSON.stringify(additions)}`,
          }
        },
        notificationSlotType: notificationManager.SlotType.SOCIAL_COMMUNICATION,
        wantAgent: wantAgentMy
      };
      notificationManager.publish(notificationRequest);
    });
  }
}
```
### onDestroy

onDestroy(): void;

Represents the callback triggered when a **FenceExtensionAbility** destruction event is received.

**System capability**: SystemCapability.Location.Location.Geofence

**Example**

```ts
import { FenceExtensionAbility } from '@kit.LocationKit';

class MyFenceExtensionAbility extends FenceExtensionAbility {
  onDestroy(): void {
    // Process the FenceExtensionAbility destruction event.
    console.info(`on ability destroy`);
  }
}

```
