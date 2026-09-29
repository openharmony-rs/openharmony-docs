# DistributedOptions

```TypeScript
export interface DistributedOptions
```

Describes options for cross-device notifications. Not supported currently.

**Since:** 8

<!--Device-unnamed-export interface DistributedOptions--><!--Device-unnamed-export interface DistributedOptions-End-->

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

<!--Device-DistributedOptions-isDistributed?: boolean--><!--Device-DistributedOptions-isDistributed?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## supportDisplayDevices

```TypeScript
supportDisplayDevices?: Array<string>
```

List of the devices to which the notification can be synchronized.

**Type:** Array&lt;string&gt;

**Since:** 8

<!--Device-DistributedOptions-supportDisplayDevices?: Array<string>--><!--Device-DistributedOptions-supportDisplayDevices?: Array<string>-End-->

**System capability:** SystemCapability.Notification.Notification

## supportOperateDevices

```TypeScript
supportOperateDevices?: Array<string>
```

List of the devices on which the notification can be opened.

**Type:** Array&lt;string&gt;

**Since:** 8

<!--Device-DistributedOptions-supportOperateDevices?: Array<string>--><!--Device-DistributedOptions-supportOperateDevices?: Array<string>-End-->

**System capability:** SystemCapability.Notification.Notification
