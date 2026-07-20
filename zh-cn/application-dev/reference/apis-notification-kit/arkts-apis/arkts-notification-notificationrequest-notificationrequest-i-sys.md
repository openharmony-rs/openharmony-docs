# NotificationRequest

定义了通知请求的数据结构，用于描述一条通知的全部信息，包括通知内容、标识、展示样式、交互行为等。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationRequest--><!--Device-unnamed-export interface NotificationRequest-End-->

**系统能力：** SystemCapability.Notification.Notification

## agentBundle

```TypeScript
readonly agentBundle?: BundleOption
```

创建通知的代理包信息。默认为空。

**类型：** BundleOption

**起始版本：** 12

<!--Device-NotificationRequest-readonly agentBundle?: BundleOption--><!--Device-NotificationRequest-readonly agentBundle?: BundleOption-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## appInstanceKey

```TypeScript
readonly appInstanceKey?: string
```

应用实例键值。默认为空。

**类型：** string

**起始版本：** 15

<!--Device-NotificationRequest-readonly appInstanceKey?: string--><!--Device-NotificationRequest-readonly appInstanceKey?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## classification

```TypeScript
classification?: string
```

通知分类。预留能力，暂未支持。

**类型：** string

**起始版本：** 7

<!--Device-NotificationRequest-classification?: string--><!--Device-NotificationRequest-classification?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## creatorInstanceKey

```TypeScript
readonly creatorInstanceKey?: number
```

创建者实例键值。

从API version 12开始支持，从API version 15开始废弃，建议使用appInstanceKey替代。

**类型：** number

**起始版本：** 12

**废弃版本：** 15

**替代接口：** [appInstanceKey](arkts-notification-notificationrequest-notificationrequest-i-sys.md#appinstancekey)

<!--Device-NotificationRequest-readonly creatorInstanceKey?: number--><!--Device-NotificationRequest-readonly creatorInstanceKey?: number-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
readonly deviceId?: string
```

通知源的deviceId。预留能力，暂未支持。

**类型：** string

**起始版本：** 8

<!--Device-NotificationRequest-readonly deviceId?: string--><!--Device-NotificationRequest-readonly deviceId?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## extendInfo

```TypeScript
extendInfo?: Record<string, Object>
```

系统应用发布通知时的自定义扩展参数。默认为空。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 20

<!--Device-NotificationRequest-extendInfo?: Record<string, Object>--><!--Device-NotificationRequest-extendInfo?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## forceDistributed

```TypeScript
forceDistributed?: boolean
```

通知是否强制进行全场景跨设备协同显示，默认为false。

**说明**:

仅当应用在跨设备协同管控名单中且notDistributed为false时，该字段才会生效。通过读取notification_config.json文件（文件配置路径见：[notification_config_parse.h](https://gitcode.com/openharmony/notification_distributed_notification_service/blob/master/services/ans/include/notification_config_parse.h)中的NOTIFICATION_CONFIG_FILE属性）中的collaborationFilter字段，查看是否包含应用的UID或包名。如果包含，说明是在应用跨设备协同管控名单中。

- 设置为true时：通知将在所有协同设备上显示。

- 设置为false时：通知将按照协同管控名单显示。

**类型：** boolean

**默认值：** false

**起始版本：** 18

<!--Device-NotificationRequest-forceDistributed?: boolean--><!--Device-NotificationRequest-forceDistributed?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## groupInfo

```TypeScript
groupInfo?: GroupInfo
```

组通知定制信息。默认为空。

**类型：** GroupInfo

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationRequest-groupInfo?: GroupInfo--><!--Device-NotificationRequest-groupInfo?: GroupInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## isRemoveAllowed

```TypeScript
isRemoveAllowed?: boolean
```

通知是否能被移除（点击通知下方删除按钮无法删除，左滑不出现删除按钮）。默认为true。

- true：是。  
- false：否。

**类型：** boolean

**默认值：** true

**起始版本：** 8

**需要权限：** 
- API版本11+：ohos.permission.SET_UNREMOVABLE_NOTIFICATION

<!--Device-NotificationRequest-isRemoveAllowed?: boolean--><!--Device-NotificationRequest-isRemoveAllowed?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## notDistributed

```TypeScript
notDistributed?: boolean
```

通知是否不进行全场景跨设备协同显示，默认为false。

**说明**:

该字段与forceDistributed字段互斥，当两者同时为true时，仅notDistributed字段生效。

- 设置为true时：通知仅在本设备上显示。

- 设置为false时：通知将在所有协同设备上显示。

**类型：** boolean

**默认值：** false

**起始版本：** 18

<!--Device-NotificationRequest-notDistributed?: boolean--><!--Device-NotificationRequest-notDistributed?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## notificationControlFlags

```TypeScript
notificationControlFlags?: number
```

通知提醒方式管控。默认值为0。

可以通过此接口减少当前通知的提醒方式。与[NotificationControlFlagStatus](arkts-notification-notificationmanager-notificationcontrolflagstatus-e-sys.md)的枚举进行按位或运算得到该参数。

**类型：** number

**起始版本：** 12

<!--Device-NotificationRequest-notificationControlFlags?: long--><!--Device-NotificationRequest-notificationControlFlags?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## overlayIcon

```TypeScript
overlayIcon?: image.PixelMap
```

通知重叠图标，默认为空。图像像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1)获取）。

此接口只在[notificationSlotType](arkts-notification-notificationrequest-notificationrequest-i.md)类型设置为SOCIAL_COMMUNICATION时生效。建议图标像素长宽为128*128。实际显示效果依赖于设备能力和通知中心UI样式。

**类型：** image.PixelMap

**起始版本：** 23

<!--Device-NotificationRequest-overlayIcon?: image.PixelMap--><!--Device-NotificationRequest-overlayIcon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## representativeBundle

```TypeScript
representativeBundle?: BundleOption
```

被代理的包信息。默认为空。

**类型：** BundleOption

**起始版本：** 12

<!--Device-NotificationRequest-representativeBundle?: BundleOption--><!--Device-NotificationRequest-representativeBundle?: BundleOption-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## source

```TypeScript
readonly source?: number
```

通知源。预留能力，暂未支持。

**类型：** number

**起始版本：** 8

<!--Device-NotificationRequest-readonly source?: int--><!--Device-NotificationRequest-readonly source?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## trigger

```TypeScript
trigger?:Trigger
```

条件对象。默认为空。

**类型：** Trigger

**起始版本：** 23

<!--Device-NotificationRequest-trigger?:Trigger--><!--Device-NotificationRequest-trigger?:Trigger-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## unifiedGroupInfo

```TypeScript
unifiedGroupInfo?: UnifiedGroupInfo
```

消息智能聚合信息字段。默认为空。

**类型：** UnifiedGroupInfo

**起始版本：** 12

<!--Device-NotificationRequest-unifiedGroupInfo?: UnifiedGroupInfo--><!--Device-NotificationRequest-unifiedGroupInfo?: UnifiedGroupInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

