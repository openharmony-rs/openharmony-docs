# GnssGeofenceRequest

GNSS地理围栏请求参数。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
```

## fenceExtensionAbilityName

```TypeScript
fenceExtensionAbilityName?: string
```

FenceExtensionAbility名称，参见 [FenceExtensionAbility](arkts-location-app-ability-fenceextensionability-fenceextensionability-c.md)。后台拉起需要申请后台定位权限，权限申请方 式参见[申请位置权限开发指导](../../../device/location/location-permission-guidelines.md#开发步骤)。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Location.Location.Geofence

## geofence

```TypeScript
geofence: Geofence
```

表示地理围栏信息，包含圆形围栏圆心坐标、半径等信息。

**类型：** Geofence

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence

## geofenceTransitionCallback

```TypeScript
geofenceTransitionCallback: AsyncCallback<GeofenceTransition>
```

表示用于接收地理围栏事件的回调函数。

**类型：** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md)&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence

## loiterTimeMs

```TypeScript
loiterTimeMs?: number
```

徘徊时间，单位为毫秒，需关注GEOFENCE_TRANSITION_DWELL事件。若设备在多边形围栏内徘徊时间达到该值，则上报GEOFENCE_TRANSITION_DWELL事件。徘徊状态检测周期为10000毫秒。例如：设 置15000，将在驻留超过20000毫秒时上报驻留状态；设置5000，将在驻留超过10000毫秒时上报驻留状态。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Location.Location.Geofence

## monitorTransitionEvents

```TypeScript
monitorTransitionEvents: Array<GeofenceTransitionEvent>
```

表示APP监听的地理围栏事件列表。数组长度不超过3。

**类型：** Array&lt;[GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md)&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence

## notifications

```TypeScript
notifications?: Array<NotificationRequest>
```

表示地理围栏事件发生后弹出的通知对象列表。monitorTransitionEvents与notifications中的顺序要一一对应，例如monitorTransitionEvents[0]为 [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md).GEOFENCE_TRANSITION_EVENT_ENTER，那 notifications[0]中就需要填入用户进入围栏时需要弹出的通知对象。默认值为空数组。

**类型：** Array&lt;[NotificationRequest](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md)&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence
