# CommonEventSubscribeInfo

用于表示公共事件订阅者的信息，支持配置订阅的公共事件类型、发布者权限、 发布者设备ID、用户ID、订阅优先级等参数，适用于应用需要订阅系统公共事件 或自定义公共事件并精细化控制事件来源的场景。 > **说明：** > > 订阅自定义公共事件后，任意应用都可以向订阅者发送潜在的恶意公共事件。通过本模块的publisherPermission和publisherBundleName参数，可以限制公共事件发布者的范围。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface CommonEventSubscribeInfo--><!--Device-unnamed-export interface CommonEventSubscribeInfo-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## events

```TypeScript
events: Array<string>
```

表示要订阅的公共事件列表。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-events: Array<string>--><!--Device-CommonEventSubscribeInfo-events: Array<string>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## priority

```TypeScript
priority?: int
```

表示订阅者的优先级，数值越大，订阅者优先级越高，越优先接收到有序公共事件。 取值范围是-100到1000，超过上下限的优先级将被设置为对应的上下限值，默认优先级为0。

**类型：** int

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-priority?: int--><!--Device-CommonEventSubscribeInfo-priority?: int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## publisherBundleName

```TypeScript
publisherBundleName?: string
```

表示要订阅的发布者的bundleName，用于限制订阅方只接收该bundleName的发布者 发布的公共事件。不设置时，可接收所有应用发布的公共事件。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-publisherBundleName?: string--><!--Device-CommonEventSubscribeInfo-publisherBundleName?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## publisherDeviceId

```TypeScript
publisherDeviceId?: string
```

表示设备ID，用于限制订阅者只接收来自指定设备发布的公共事件。 通过[@ohos.deviceInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取udid，作为 发布者的设备ID。预留能力，暂不支持。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-publisherDeviceId?: string--><!--Device-CommonEventSubscribeInfo-publisherDeviceId?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## publisherPermission

```TypeScript
publisherPermission?: string
```

表示发布者的权限，取值为系统已定义的权限名。用于限制订阅方只接收具有该 权限的发布方发布的公共事件。不设置时，可接收所有发布方发布的公共事件。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-publisherPermission?: string--><!--Device-CommonEventSubscribeInfo-publisherPermission?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## userId

```TypeScript
userId?: int
```

表示用户ID，用于限制订阅者只接收指定用户ID相关的公共事件。此参数是可选的， 默认值为当前用户的ID。如果指定了此参数，则该值必须是系统中现有的用户ID。通过 [getOsAccountLocalId]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 获取系统用户ID，作为发布者的用户ID。

**类型：** int

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventSubscribeInfo-userId?: int--><!--Device-CommonEventSubscribeInfo-userId?: int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

