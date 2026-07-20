# CommonEventSubscribeInfo

用于表示订阅者的信息。

> **说明：**  
>  
> 订阅自定义公共事件后，任意应用都可以向订阅者发送潜在的恶意公共事件。通过本模块的publisherPermission和publisherBundleName参数，可以限制公共事件发布方的范围。

**起始版本：** 7

<!--Device-unnamed-export interface CommonEventSubscribeInfo--><!--Device-unnamed-export interface CommonEventSubscribeInfo-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## events

```TypeScript
events: Array<string>
```

表示要订阅的公共事件。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-events: Array<string>--><!--Device-CommonEventSubscribeInfo-events: Array<string>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## priority

```TypeScript
priority?: number
```

表示订阅者的优先级。值的范围是-100到1000，超过上下限的优先级将被设置为上下限值。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-priority?: int--><!--Device-CommonEventSubscribeInfo-priority?: int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## publisherBundleName

```TypeScript
publisherBundleName?: string
```

表示要订阅的发布者的bundleName。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-publisherBundleName?: string--><!--Device-CommonEventSubscribeInfo-publisherBundleName?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## publisherDeviceId

```TypeScript
publisherDeviceId?: string
```

表示设备ID。通过[@ohos.deviceInfo](arkts-deviceinfo.md)获取udid，作为订阅者的设备ID。预留能力，暂不支持。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-publisherDeviceId?: string--><!--Device-CommonEventSubscribeInfo-publisherDeviceId?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## publisherPermission

```TypeScript
publisherPermission?: string
```

表示发布者的权限，订阅方将只能接收到具有该权限的发送方发布的事件。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-publisherPermission?: string--><!--Device-CommonEventSubscribeInfo-publisherPermission?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## userId

```TypeScript
userId?: number
```

表示用户ID。此参数是可选的，默认值当前用户的ID。如果指定了此参数，则该值必须是系统中现有的用户ID。通过[getOsAccountLocalId](arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取系统账号ID，作为订阅者的用户ID。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-userId?: int--><!--Device-CommonEventSubscribeInfo-userId?: int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

