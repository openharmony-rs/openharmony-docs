# @ohos.enterprise.deviceInfo

本模块提供企业设备信息管理能力，支持获取设备序列号、设备名称、SIM卡信息等。企业管理员可通过此模块查询设备详细信息，实现设备资产的统一管理和追踪。 **使用场景：** - 设备资产管理与追踪 - 企业设备合规性检查 - 设备信息采集与统计 - 故障诊断与设备识别 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare namespace deviceInfo--><!--Device-unnamed-declare namespace deviceInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getDeviceInfo](arkts-mdm-deviceinfo-getdeviceinfo-f.md#getdeviceinfo) | 获取设备信息。 |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f.md#getdevicename) | 获取设备名称，使用callback异步回调。 |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f.md#getdevicename-1) | 获取设备名称，使用Promise异步回调。 |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f.md#getdeviceserial) | 获取设备序列号，使用callback异步回调。 |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f.md#getdeviceserial-1) | 获取设备序列号，使用Promise异步回调。 |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f.md#getdisplayversion) | 获取设备版本号，使用callback异步回调。 |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f.md#getdisplayversion-1) | 获取设备版本号，使用Promise异步回调。 |

