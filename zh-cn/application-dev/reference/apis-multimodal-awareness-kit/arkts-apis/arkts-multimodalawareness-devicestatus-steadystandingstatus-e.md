# SteadyStandingStatus

设备静止姿态感知状态（支架态）。 设备进入支架态指设备静止，且屏幕与水平面角度处于45度-135度。折叠屏手机需处于折叠状态或者完全展开状态。系统通过传感器检测设备的运动状态和角度变化，判断设备是否满足支架态条件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-deviceStatus-export enum SteadyStandingStatus--><!--Device-deviceStatus-export enum SteadyStandingStatus-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

## STATUS_EXIT

```TypeScript
STATUS_EXIT = 0
```

表示设备退出支架态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SteadyStandingStatus-STATUS_EXIT = 0--><!--Device-SteadyStandingStatus-STATUS_EXIT = 0-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

## STATUS_ENTER

```TypeScript
STATUS_ENTER = 1
```

表示设备进入支架态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SteadyStandingStatus-STATUS_ENTER = 1--><!--Device-SteadyStandingStatus-STATUS_ENTER = 1-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

