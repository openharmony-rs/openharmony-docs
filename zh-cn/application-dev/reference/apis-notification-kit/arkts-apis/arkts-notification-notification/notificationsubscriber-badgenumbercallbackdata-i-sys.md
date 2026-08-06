# BadgeNumberCallbackData（系统接口）

应用角标数量变化的回调函数类型。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface BadgeNumberCallbackData--><!--Device-unnamed-export interface BadgeNumberCallbackData-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## appInstanceKey

```TypeScript
readonly appInstanceKey?: string
```

应用实例键值。

**类型：** string

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-BadgeNumberCallbackData-readonly appInstanceKey?: string--><!--Device-BadgeNumberCallbackData-readonly appInstanceKey?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## badgeNumber

```TypeScript
readonly badgeNumber: int
```

角标个数。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-BadgeNumberCallbackData-readonly badgeNumber: int--><!--Device-BadgeNumberCallbackData-readonly badgeNumber: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## bundle

```TypeScript
readonly bundle: string
```

应用的包名。

**类型：** string

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-BadgeNumberCallbackData-readonly bundle: string--><!--Device-BadgeNumberCallbackData-readonly bundle: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## instanceKey

```TypeScript
readonly instanceKey?: number
```

应用实例键值。从API version 12开始支持，从API version 15开始废弃，建议使用appInstanceKey替代。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** 15

**替代接口：** [BadgeNumberCallbackData#appInstanceKey](notificationsubscriber-badgenumbercallbackdata-i-sys.md#appinstancekey)

<!--Device-BadgeNumberCallbackData-readonly instanceKey?: number--><!--Device-BadgeNumberCallbackData-readonly instanceKey?: number-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
readonly uid: int
```

应用的uid。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-BadgeNumberCallbackData-readonly uid: int--><!--Device-BadgeNumberCallbackData-readonly uid: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

