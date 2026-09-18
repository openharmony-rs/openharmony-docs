# DistributedOptions

Describes options for cross-device notifications. Not supported currently.

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

## isDistributed

```TypeScript
isDistributed?: boolean
```

Whether cross-device notifications are supported. The default value is **true**.

- **true**: cross-device notifications are supported.  
- **false**: cross-device notifications are not supported.

**Type:** boolean

**Default:** true

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

## supportDisplayDevices

```TypeScript
supportDisplayDevices?: Array<string>
```

List of the devices to which the notification can be synchronized.

**Type:** Array&lt;string&gt;

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

## supportOperateDevices

```TypeScript
supportOperateDevices?: Array<string>
```

List of the devices on which the notification can be opened.

**Type:** Array&lt;string&gt;

**Since:** 8

**System capability:** SystemCapability.Notification.Notification
