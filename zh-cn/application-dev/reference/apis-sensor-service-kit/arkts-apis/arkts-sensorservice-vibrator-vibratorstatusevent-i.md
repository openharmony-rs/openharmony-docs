# VibratorStatusEvent

振动设备上线、下线状态事件信息。当马达设备上线或下线时，通过[vibrator.on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_回调传递此对象。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface VibratorStatusEvent--><!--Device-vibrator-interface VibratorStatusEvent-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## deviceId

```TypeScript
deviceId: int
```

设备的ID。可用于 [startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 和[stopVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_等接口指定目标设备。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorStatusEvent-deviceId: int--><!--Device-VibratorStatusEvent-deviceId: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## isVibratorOnline

```TypeScript
isVibratorOnline: boolean
```

指示设备的上线和下线状态。true表示设备上线，可用于触发振动；false表示设备下线，此时该设备的振动不可用。

**类型：** boolean

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorStatusEvent-isVibratorOnline: boolean--><!--Device-VibratorStatusEvent-isVibratorOnline: boolean-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## timestamp

```TypeScript
timestamp: long
```

报告事件的时间戳。单位：ms。

**类型：** long

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorStatusEvent-timestamp: long--><!--Device-VibratorStatusEvent-timestamp: long-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## vibratorCount

```TypeScript
vibratorCount: int
```

设备上的马达的数量。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorStatusEvent-vibratorCount: int--><!--Device-VibratorStatusEvent-vibratorCount: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

