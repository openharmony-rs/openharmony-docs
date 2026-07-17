# @ohos.enterprise.deviceInfo

本模块提供企业设备信息管理能力，包括获取设备序列号、设备名称等。

> **说明：**  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace deviceInfo--><!--Device-unnamed-declare namespace deviceInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getDeviceInfo](arkts-mdm-deviceinfo-getdeviceinfo-f.md#getdeviceinfo-1) | 获取设备信息。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f-sys.md#getdevicename-1) | 获取设备名称，使用callback异步回调。 |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f-sys.md#getdevicename-2) | 获取设备名称，使用Promise异步回调。 |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f-sys.md#getdeviceserial-1) | 获取设备序列号，使用callback异步回调。 |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f-sys.md#getdeviceserial-2) | 获取设备序列号，使用Promise异步回调。 |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f-sys.md#getdisplayversion-1) | 获取设备版本号，使用callback异步回调。 |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f-sys.md#getdisplayversion-2) | 获取设备版本号，使用Promise异步回调。 |
<!--DelEnd-->

