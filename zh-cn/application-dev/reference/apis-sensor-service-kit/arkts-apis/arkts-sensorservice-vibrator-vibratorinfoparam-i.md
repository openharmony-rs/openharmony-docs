# VibratorInfoParam

设备上马达的参数。用于指定需要查询或控制的设备和马达信息。默认情况下，VibratorInfoParam默认为查询或控制本地全部马达。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface VibratorInfoParam--><!--Device-vibrator-interface VibratorInfoParam-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## deviceId

```TypeScript
deviceId?: int
```

设备的ID。默认值：-1，表示本地设备。使用场景：在多设备场景下需指定远程设备时设置此参数；不填此参数时默认控制本地设备。从API version 19开始，设备ID可通过 [getVibratorInfoSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或[on]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_查询获取。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorInfoParam-deviceId?: int--><!--Device-VibratorInfoParam-deviceId?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## vibratorId

```TypeScript
vibratorId?: int
```

马达ID。默认值：0，表示该设备的全部马达。使用场景：在多马达设备上需指定特定马达时设置此参数；不填此参数时默认控制该设备的全部马达。从API version 19开始，马达ID可通过 [getVibratorInfoSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或[on]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_查询获取。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VibratorInfoParam-vibratorId?: int--><!--Device-VibratorInfoParam-vibratorId?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

