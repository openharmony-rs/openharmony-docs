# @ohos.enterprise.deviceControl

本模块提供设备控制能力，用于企业设备管理场景。管理员可以通过本模块远程控制设备，包括设备重启、关机、锁屏、恢复出厂设置等操作，帮助企业实现设备统一管理和安全管控。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare namespace deviceControl--><!--Device-unnamed-declare namespace deviceControl-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [lockScreen](arkts-mdm-devicecontrol-lockscreen-f.md#lockscreen) | 使设备屏幕锁定。设置之后设备立即锁屏。 |
| [operateDevice](arkts-mdm-devicecontrol-operatedevice-f.md#operatedevice) | 允许管理员对设备执行恢复出厂设置、重启、关机、锁屏等操作，例如在企业设备管理场景下，管理员可远程控制员工设备执行恢复出厂设置、重启、关机或锁屏等操作。 |
| [operateDevice](arkts-mdm-devicecontrol-operatedevice-f.md#operatedevice-1) | 允许管理员操作设备，例如在企业设备管理场景下，管理员可远程控制员工设备执行磁盘擦除、恢复出厂设置、重启、关机、锁屏、锁定设备或解锁设备等操作。 |
| [reboot](arkts-mdm-devicecontrol-reboot-f.md#reboot) | 使设备重启。 |
| [resetFactory](arkts-mdm-devicecontrol-resetfactory-f.md#resetfactory) | 使设备恢复出厂设置。使用callback异步回调。 |
| [resetFactory](arkts-mdm-devicecontrol-resetfactory-f.md#resetfactory-1) | 使设备恢复出厂设置。使用Promise异步回调。 |
| [shutdown](arkts-mdm-devicecontrol-shutdown-f.md#shutdown) | 使设备关机。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Operation](arkts-mdm-devicecontrol-operation-e.md) | 设备操作。 |

