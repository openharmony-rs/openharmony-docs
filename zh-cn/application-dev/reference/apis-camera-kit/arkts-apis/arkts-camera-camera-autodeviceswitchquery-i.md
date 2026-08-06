# AutoDeviceSwitchQuery

自动切换镜头查询类，用于查询设备是否支持自动切换镜头。 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_仅支持折叠屏设备使用，如需使能该能力请参考 [enableAutoDeviceSwitch]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-camera-interface AutoDeviceSwitchQuery--><!--Device-camera-interface AutoDeviceSwitchQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isAutoDeviceSwitchSupported

```TypeScript
isAutoDeviceSwitchSupported(): boolean
```

查询设备是否支持自动切换镜头能力。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

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
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 13 - 17 |

