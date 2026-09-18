# NotificationFilter (System API)

Describes the filter criteria for querying the live view.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## bundle

```TypeScript
bundle: BundleOption
```

Bundle information of the live view.

**Type:** [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## extraInfoKeys

```TypeScript
extraInfoKeys?: Array<string>
```

List of extra keys. If this parameter is left empty, all extra information is included.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## notificationKey

```TypeScript
notificationKey: notificationSubscribe.NotificationKey
```

Notification information, including the notification ID and label.

**Type:** [notificationSubscribe.NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
