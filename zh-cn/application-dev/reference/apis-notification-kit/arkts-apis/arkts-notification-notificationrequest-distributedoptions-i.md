# DistributedOptions

描述跨设备协同选项。预留能力，暂未支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface DistributedOptions--><!--Device-unnamed-export interface DistributedOptions-End-->

**系统能力：** SystemCapability.Notification.Notification

## isDistributed

```TypeScript
isDistributed?: boolean
```

是否支持跨设备协同通知。默认为true。 - true：支持跨设备协同通知。 - false：不支持跨设备协同通知。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DistributedOptions-isDistributed?: boolean--><!--Device-DistributedOptions-isDistributed?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## supportDisplayDevices

```TypeScript
supportDisplayDevices?: Array<string>
```

可以同步通知到的设备列表。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DistributedOptions-supportDisplayDevices?: Array<string>--><!--Device-DistributedOptions-supportDisplayDevices?: Array<string>-End-->

**系统能力：** SystemCapability.Notification.Notification

## supportOperateDevices

```TypeScript
supportOperateDevices?: Array<string>
```

可以打开通知的设备列表。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DistributedOptions-supportOperateDevices?: Array<string>--><!--Device-DistributedOptions-supportOperateDevices?: Array<string>-End-->

**系统能力：** SystemCapability.Notification.Notification

