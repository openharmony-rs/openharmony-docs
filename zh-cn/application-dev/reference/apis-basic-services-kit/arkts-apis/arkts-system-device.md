# @system.device

本模块提供当前设备的信息，通过读取系统配置获取设备品牌、型号、生产商、屏幕参数等基础信息，供开发者进行设备适配和功能判断。
 > **说明：**
 >
 > - 模块维护策略
 > >
 > >    \- 对于Lite Wearable设备类型，该模块长期维护，正常使用。
 > >
 > >    \- 对于支持该模块的其他设备类型，该模块从API Version 6开始不再维护，推荐使用新接口[@ohos.deviceInfo](arkts-deviceinfo.md)进行设备信息查
 > 询。
 > - 本模块首批接口从API version 3开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```TypeScript
import { Device, DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Device](arkts-basicservices-system-device-device-c.md) | getInfo interface |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DeviceResponse](arkts-basicservices-system-device-deviceresponse-i.md) | 定义设备信息获取的参数选项。 |
| [GetDeviceOptions](arkts-basicservices-system-device-getdeviceoptions-i.md) | 定义设备信息获取的参数选项。 |
