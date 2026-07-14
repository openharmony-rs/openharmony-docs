# NotificationRequest

描述通知的请求。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## agentBundle

```TypeScript
readonly agentBundle?: BundleOption
```

创建通知的代理包信息。默认为空。

**类型：** BundleOption

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## appInstanceKey

```TypeScript
readonly appInstanceKey?: string
```

应用实例键值。默认为空。

**类型：** string

**起始版本：** 15

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## classification

```TypeScript
classification?: string
```

通知分类。
预留能力，暂未支持。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## creatorInstanceKey

```TypeScript
readonly creatorInstanceKey?: number
```

创建者实例键值。

从API version 12开始支持，从API version 15开始废弃，建议使用appInstanceKey替代。。

**类型：** number

**起始版本：** 12

**废弃版本：** 15

**替代接口：** [appInstanceKey](arkts-notification-notificationrequest-i-sys.md#appinstancekey)

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
readonly deviceId?: string
```

通知源的deviceId。
预留能力，暂未支持。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## extendInfo

```TypeScript
extendInfo?: Record<string, Object>
```

系统应用发布通知时的自定义扩展参数。默认为空。

**类型：** Record<string, Object>

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## forceDistributed

```TypeScript
forceDistributed?: boolean
```

通知是否强制进行全场景跨设备协同显示。

**说明**:

仅当应用在跨设备协同管控名单中且notDistributed为false时，该字段才会生效。通过读取notification_config.json文件（文件配置路径见：
[notification_config_parse.h](https://gitcode.com/openharmony/notification_distributed_notification_service/blob/master/services/ans/include/notification_config_parse.h)
中的NOTIFICATION_CONFIG_FILE属性）中的collaborationFilter字段，查看是否包含应用的UID或包名。如果包含，说明是在应用跨设备协同管控名单中。

- 设置为true时：通知将在所有协同设备上显示。

- 设置为false时：通知将按照协同管控名单显示。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## groupInfo

```TypeScript
groupInfo?: GroupInfo
```

组通知定制信息。默认为空。

26.0.0

**类型：** GroupInfo

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## isRemoveAllowed

```TypeScript
isRemoveAllowed?: boolean
```

通知是否能被移除（点击通知下方删除按钮无法删除，左滑不出现删除按钮）。

- true：是。
- false：否。

ohos.permission.SET_UNREMOVABLE_NOTIFICATION

**类型：** boolean

**默认值：** true

**起始版本：** 8

**需要权限：** 
- API版本11+：ohos.permission.SET_UNREMOVABLE_NOTIFICATION

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## notDistributed

```TypeScript
notDistributed?: boolean
```

通知是否不进行全场景跨设备协同显示。

**说明**:

该字段与forceDistributed字段互斥，当两者同时为true时，仅notDistributed字段生效。

- 设置为true时：通知仅在本设备上显示。

- 设置为false时：通知将在所有协同设备上显示。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## notificationControlFlags

```TypeScript
notificationControlFlags?: number
```

通知提醒方式管控。默认值为0。

可以通过此接口减少当前通知的提醒方式。与
[NotificationControlFlagStatus](arkts-notification-notificationcontrolflagstatus-e-sys.md)的
枚举进行按位或运算得到该参数。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## overlayIcon

```TypeScript
overlayIcon?: image.PixelMap
```

通知重叠图标，默认为空。图像像素的总字节数不超过192KB（图标像素的总字节数通过
[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md#getpixelbytesnumber-1)获取）。

此接口只在[notificationSlotType](arkts-notification-notificationrequest-i.md)类型设置为SOCIAL_COMMUNICATION时生效。建议图标像素长宽为128*128。实际显示效果依赖于设备能力和通
知中心UI样式。

**类型：** image.PixelMap

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## representativeBundle

```TypeScript
representativeBundle?: BundleOption
```

被代理的包信息。默认为空。

**类型：** BundleOption

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## source

```TypeScript
readonly source?: number
```

通知源。
预留能力，暂未支持。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## trigger

```TypeScript
trigger?:Trigger
```

条件对象。默认为空。

**类型：** Trigger

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## unifiedGroupInfo

```TypeScript
unifiedGroupInfo?: UnifiedGroupInfo
```

消息智能聚合信息字段。默认为空。

**类型：** UnifiedGroupInfo

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

