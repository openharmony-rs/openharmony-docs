# VibratorInfo

表示查询的马达信息。通过[vibrator.getVibratorInfoSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_返回此对象，用于获取设备马达能力和选择合适的马达触发振动。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface VibratorInfo--><!--Device-vibrator-interface VibratorInfo-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## deviceId

```TypeScript
deviceId: int
```

设备ID。可用于 [startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 和[stopVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_等接口指定目标设备。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorInfo-deviceId: int--><!--Device-VibratorInfo-deviceId: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## deviceName

```TypeScript
deviceName: string
```

设备名称。

**类型：** string

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorInfo-deviceName: string--><!--Device-VibratorInfo-deviceName: string-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## isHdHapticSupported

```TypeScript
isHdHapticSupported: boolean
```

是否支持高清振动。true表示支持高清振动，可使用VibrateFromFile和VibrateFromPattern类型触发振动；false表示不支持，使用自定义振动类型可能效果不佳。

**类型：** boolean

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorInfo-isHdHapticSupported: boolean--><!--Device-VibratorInfo-isHdHapticSupported: boolean-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## isLocalVibrator

```TypeScript
isLocalVibrator: boolean
```

是否为本地设备。true表示本地设备，可直接触发振动；false表示远程设备，需在分布式场景下使用。

**类型：** boolean

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorInfo-isLocalVibrator: boolean--><!--Device-VibratorInfo-isLocalVibrator: boolean-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## vibratorId

```TypeScript
vibratorId: int
```

马达ID。可用于 [startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 和[stopVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_等接口指定目标马达。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorInfo-vibratorId: int--><!--Device-VibratorInfo-vibratorId: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

