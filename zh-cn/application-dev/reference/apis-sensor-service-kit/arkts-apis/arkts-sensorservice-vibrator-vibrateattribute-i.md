# VibrateAttribute

马达振动属性。用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 接口的attribute参数，指定马达ID、设备ID和振动使用场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-interface VibrateAttribute--><!--Device-vibrator-interface VibrateAttribute-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## deviceId

```TypeScript
deviceId?: int
```

设备ID。默认值：-1，表示本地设备。使用场景：在多设备场景下需指定远程设备时设置此参数；不填写时默认控制本地设备。从API version 19开始，设备ID可以使用 [getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md#getVibratorInfoSync)或on查询。 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-VibrateAttribute-deviceId?: int--><!--Device-VibrateAttribute-deviceId?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## id

```TypeScript
id?: int
```

马达ID。默认值：0。使用场景：当设备存在多个马达时，可通过指定不同的马达ID来选择特定马达触发振动。马达ID可以通过 [getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md#getVibratorInfoSync)查询。不填写时默认使用马达ID为0的马达。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VibrateAttribute-id?: int--><!--Device-VibrateAttribute-id?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## usage

```TypeScript
usage: Usage
```

马达振动的使用场景。默认值：'unknown'。取值范围只允许在[Usage](arkts-sensorservice-vibrator-usage-t.md#Usage)提供的类型中选取。不同usage值对应不同的系统振动开关管控规则，开发者需根据实际业务场景选择合适的 usage值。 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [Usage](arkts-sensorservice-vibrator-usage-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VibrateAttribute-usage: Usage--><!--Device-VibrateAttribute-usage: Usage-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

