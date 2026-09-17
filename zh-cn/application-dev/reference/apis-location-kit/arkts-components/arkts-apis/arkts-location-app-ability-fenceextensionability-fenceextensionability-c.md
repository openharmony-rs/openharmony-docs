# FenceExtensionAbility

FenceExtensionAbility为开发者提供的地理围栏相关的能力。

**起始版本：** 14

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
import { FenceExtensionAbility } from '@kit.LocationKit';
```

## onDestroy

```TypeScript
onDestroy(): void
```

接收FenceExtensionAbility的销毁事件并处理，会在FenceExtensionAbility销毁前回调。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**示例**

```TypeScript
import { FenceExtensionAbility } from '@kit.LocationKit';

class MyFenceExtensionAbility extends FenceExtensionAbility {
  onDestroy(): void {
    // 处理ability销毁事件
    console.info(`on ability destroy`);
  }
}
```

## onFenceStatusChange

```TypeScript
onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void
```

接收系统通知的地理围栏事件，根据围栏事件类型和数据进行相应处理。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | [geoLocationManager.GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md) | 是 | 地理围栏事件信息；包含地理围栏ID和具体的地理围栏事件。 |
| additions | Record&lt;string, string&gt; | 是 | 附加信息 |

**示例**

```TypeScript
import { FenceExtensionAbility, geoLocationManager } from '@kit.LocationKit';
import { notificationManager } from '@kit.NotificationKit';
import { Want, wantAgent } from '@kit.AbilityKit';

export class MyFenceExtensionAbility extends FenceExtensionAbility {
  onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void {
    // 接受围栏状态变化事件，处理业务逻辑
    console.info(`on geofence transition,id:${transition.geofenceId},event:${transition.transitionEvent},additions:${JSON.stringify(additions)}`);

    // 可以发送围栏业务通知
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility',
          parameters:
          {
            'geofenceId': transition?.geofenceId,
            'transitionEvent': transition?.transitionEvent,
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
            title: `围栏通知`,
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

表示围栏的的上下文环境。

**类型：** [FenceExtensionContext](arkts-location-app-ability-fenceextensioncontext-fenceextensioncontext-c-sys.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence
