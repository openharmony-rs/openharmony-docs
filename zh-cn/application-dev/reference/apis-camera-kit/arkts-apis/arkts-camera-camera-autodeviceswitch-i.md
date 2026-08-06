# AutoDeviceSwitch

自动切换镜头类，继承自[AutoDeviceSwitchQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，用于使能或去使能自动切换镜头。自动切换镜头能力仅支持折叠屏设备使用，详细开发指导请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 使用建议：自动切换镜头功能由系统自动完成输入设备切换、会话配置和参数接续。如系统发现镜头切换时，两颗镜头的变焦范围不一致，则会通过 [AutoDeviceSwitchStatus]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中的isDeviceCapabilityChanged字段告知应用，但仍需要应用自己处理UX的变更（如变焦范 围的调整，需要重新通过[getZoomRatioRange]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口获取数据并更新UX），因此更适用于极简UX交互的场景。

**继承/实现关系：** AutoDeviceSwitch extends [AutoDeviceSwitchQuery](arkts-camera-camera-autodeviceswitchquery-i.md)

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-camera-interface AutoDeviceSwitch extends AutoDeviceSwitchQuery--><!--Device-camera-interface AutoDeviceSwitch extends AutoDeviceSwitchQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## enableAutoDeviceSwitch

```TypeScript
enableAutoDeviceSwitch(enabled: boolean): void
```

使能或去使能自动切换镜头。可以先通过[isAutoDeviceSwitchSupported]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取 当前设备是否支持自动切换镜头。 > **说明：** > > 该接口仅用于有多个前置镜头的折叠设备，在不同的折叠状态下可自动切换到当前可使用的前置镜头。无法实现前后置镜头的切换。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoDeviceSwitch-enableAutoDeviceSwitch(enabled: boolean): void--><!--Device-AutoDeviceSwitch-enableAutoDeviceSwitch(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 使能或去使能自动切换镜头。true表示使能，false表示不使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameters verification failed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 19+ |

