# SlotType

通知渠道类型。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

## UNKNOWN_TYPE

```TypeScript
UNKNOWN_TYPE = 0
```

未知类型。该类型对应[SlotLevel](arkts-notification-slotlevel-e.md)为LEVEL_MIN。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Notification

## SOCIAL_COMMUNICATION

```TypeScript
SOCIAL_COMMUNICATION = 1
```

社交通信。该类型对应[SlotLevel](arkts-notification-slotlevel-e.md)为LEVEL_HIGH。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Notification

## SERVICE_INFORMATION

```TypeScript
SERVICE_INFORMATION = 2
```

服务提醒。该类型对应[SlotLevel](arkts-notification-slotlevel-e.md)为LEVEL_HIGH。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Notification

## CONTENT_INFORMATION

```TypeScript
CONTENT_INFORMATION = 3
```

内容资讯。该类型对应[SlotLevel](arkts-notification-slotlevel-e.md)为LEVEL_MIN。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Notification

## LIVE_VIEW

```TypeScript
LIVE_VIEW = 4
```

实况窗。不支持三方应用直接创建该渠道类型通知，可以由系统代理创建后，三方应用发布同ID的通知来更新指定内容。该类型对应[SlotLevel](arkts-notification-slotlevel-e.md)为
LEVEL_DEFAULT。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Notification

## CUSTOMER_SERVICE

```TypeScript
CUSTOMER_SERVICE = 5
```

客服消息。该类型用于用户与商家之间的客服消息，需由用户主动发起。该类型对应[SlotLevel](arkts-notification-slotlevel-e.md)为LEVEL_DEFAULT。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Notification

## OTHER_TYPES

```TypeScript
OTHER_TYPES = 0xFFFF
```

其他。该类型对应[SlotLevel](arkts-notification-slotlevel-e.md)为LEVEL_MIN。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Notification

