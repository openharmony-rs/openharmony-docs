# AutoDeviceSwitchQuery

自动切换镜头查询类，用于查询设备是否支持自动切换镜头。 [自动切换镜头能力](../../../media/camera/camera-auto-switch.md)仅支持折叠屏设备使用，如需使能该能力请参考 [enableAutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#enableAutoDeviceSwitch)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface AutoDeviceSwitchQuery--><!--Device-camera-interface AutoDeviceSwitchQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isAutoDeviceSwitchSupported

```TypeScript
isAutoDeviceSwitchSupported(): boolean
```

查询设备是否支持自动切换镜头能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoDeviceSwitchQuery-isAutoDeviceSwitchSupported(): boolean--><!--Device-AutoDeviceSwitchQuery-isAutoDeviceSwitchSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持自动切换镜头，true为支持，false为不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage.<br>**适用版本：** 13 - 17 |

