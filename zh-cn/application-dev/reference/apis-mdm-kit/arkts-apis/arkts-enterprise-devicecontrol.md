# @ohos.enterprise.deviceControl

本模块提供设备控制能力。

> **说明**：  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](docroot://mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace deviceControl--><!--Device-unnamed-declare namespace deviceControl-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { deviceControl } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [operateDevice](arkts-mdm-devicecontrol-operatedevice-f.md#operatedevice) | 允许管理员操作设备。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [lockScreen](arkts-mdm-devicecontrol-lockscreen-f-sys.md#lockscreen) | 使设备屏幕锁定。设置之后设备立即锁屏。 |
| [reboot](arkts-mdm-devicecontrol-reboot-f-sys.md#reboot) | 使设备重启。 |
| [resetFactory](arkts-mdm-devicecontrol-resetfactory-f-sys.md#resetfactory) | 使设备恢复出厂设置。使用callback异步回调。 |
| [resetFactory](arkts-mdm-devicecontrol-resetfactory-f-sys.md#resetfactory-1) | 使设备恢复出厂设置。使用Promise异步回调。 |
| [shutdown](arkts-mdm-devicecontrol-shutdown-f-sys.md#shutdown) | 使设备关机。 |
<!--DelEnd-->

