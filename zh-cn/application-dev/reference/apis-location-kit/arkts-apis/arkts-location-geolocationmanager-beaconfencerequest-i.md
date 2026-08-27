# BeaconFenceRequest

beacon围栏请求参数。transitionCallback与fenceExtensionAbilityName任选其一，都不填则参数无效。

**起始版本：** 20

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
```

## beacon

```TypeScript
beacon: BeaconFence
```

beacon围栏的参数配置。

**类型：** [BeaconFence](arkts-location-geolocationmanager-beaconfence-i.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence

## fenceExtensionAbilityName

```TypeScript
fenceExtensionAbilityName?: string
```

[FenceExtensionAbility](arkts-location-app-ability-fenceextensionability-fenceextensionability-c.md)名称。默认值为空字符串。

**类型：** string

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence

## transitionCallback

```TypeScript
transitionCallback?: Callback<GeofenceTransition>
```

beacon围栏事件信息。默认值为undefined。仅支持前台回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md)&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence
