# @ohos.enterprise.deviceInfo

本模块提供企业设备信息管理能力，支持获取设备序列号、设备名称、SIM卡信息等。企业管理员可通过此模块查询设备详细信息，实现设备资产的统一管理和追踪。 **使用场景：** - 设备资产管理与追踪 - 企业设备合规性检查 - 设备信息采集与统计 - 故障诊断与设备识别 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare namespace deviceInfo--><!--Device-unnamed-declare namespace deviceInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getDeviceInfo](arkts-mdm-deviceinfo-getdeviceinfo-f.md#getDeviceInfo) | 获取设备信息。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f-sys.md#getDeviceName) | 获取设备名称，使用callback异步回调。 |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f-sys.md#getDeviceName（系统接口）) | 获取设备名称，使用Promise异步回调。 |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f-sys.md#getDeviceSerial) | 获取设备序列号，使用callback异步回调。 |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f-sys.md#getDeviceSerial（系统接口）) | 获取设备序列号，使用Promise异步回调。 |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f-sys.md#getDisplayVersion) | 获取设备版本号，使用callback异步回调。 |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f-sys.md#getDisplayVersion（系统接口）) | 获取设备版本号，使用Promise异步回调。 |
<!--DelEnd-->

