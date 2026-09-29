# BadgeNumberCallbackData (System API)

```TypeScript
export interface BadgeNumberCallbackData
```

Returns the changes of the application badge number.

**Since:** 10

<!--Device-unnamed-export interface BadgeNumberCallbackData--><!--Device-unnamed-export interface BadgeNumberCallbackData-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## appInstanceKey

```TypeScript
readonly appInstanceKey?: string
```

Key value of an application instance.

**Type:** string

**Since:** 15

<!--Device-BadgeNumberCallbackData-readonly appInstanceKey?: string--><!--Device-BadgeNumberCallbackData-readonly appInstanceKey?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## badgeNumber

```TypeScript
readonly badgeNumber: number
```

Number of notifications displayed on the application icon.

**Type:** number

**Since:** 10

<!--Device-BadgeNumberCallbackData-readonly badgeNumber: int--><!--Device-BadgeNumberCallbackData-readonly badgeNumber: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## bundle

```TypeScript
readonly bundle: string
```

Bundle name of the application.

**Type:** string

**Since:** 10

<!--Device-BadgeNumberCallbackData-readonly bundle: string--><!--Device-BadgeNumberCallbackData-readonly bundle: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## uid

```TypeScript
readonly uid: number
```

UID of the application.

**Type:** number

**Since:** 10

<!--Device-BadgeNumberCallbackData-readonly uid: int--><!--Device-BadgeNumberCallbackData-readonly uid: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## instanceKey

```TypeScript
readonly instanceKey?: number
```

Key value of an application instance.

**Type:** number

**Since:** 12

**Deprecated since:** 15

**Substitutes:** [appInstanceKey](#appinstancekey)

<!--Device-BadgeNumberCallbackData-readonly instanceKey?: number--><!--Device-BadgeNumberCallbackData-readonly instanceKey?: number-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
