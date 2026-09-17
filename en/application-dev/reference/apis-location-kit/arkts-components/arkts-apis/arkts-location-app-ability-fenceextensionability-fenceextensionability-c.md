# FenceExtensionAbility

Class of fence extension ability.

**Since:** 14

**System capability:** SystemCapability.Location.Location.Geofence

## Modules to Import

```TypeScript
import { FenceExtensionAbility } from '@kit.LocationKit';
```

## onDestroy

```TypeScript
onDestroy(): void
```

Called back before a fence extension is destroyed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Geofence

**Examples**

```TypeScript
import { FenceExtensionAbility } from '@kit.LocationKit';

class MyFenceExtensionAbility extends FenceExtensionAbility {
  onDestroy(): void {
    // Process the FenceExtensionAbility destruction event.
    console.info(`on ability destroy`);
  }
}
```

## onFenceStatusChange

```TypeScript
onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void
```

Called back when geofence status is change.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Geofence

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [geoLocationManager.GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md) | Yes | Geofence transition status |
| additions | Record&lt;string, string&gt; | Yes | Indicates additional information |

**Examples**

```TypeScript
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

## context

```TypeScript
context: FenceExtensionContext
```

Indicates the fence extension context.

**Type:** [FenceExtensionContext](arkts-location-app-ability-fenceextensioncontext-fenceextensioncontext-c-sys.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Geofence
