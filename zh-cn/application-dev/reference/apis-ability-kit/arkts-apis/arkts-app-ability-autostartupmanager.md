# @ohos.app.ability.autoStartupManager

aautoStartupManager模块提供获取自身应用的开机自启状态以及检查设备是否支持开机自启动的能力。

**起始版本：** 23

<!--Device-unnamed-declare namespace autoStartupManager--><!--Device-unnamed-declare namespace autoStartupManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAutoStartupStatusForSelf](arkts-ability-autostartupmanager-getautostartupstatusforself-f.md) | 获取当前应用的开机自启动状态。使用Promise异步回调。 该接口仅在Phone、PC/2in1、Tablet和Wearable设备中可正常调用，在其他设备中返回801错误码。 |
| [isAutoStartupSupported](arkts-ability-autostartupmanager-isautostartupsupported-f.md) | 检查当前设备是否支持开机自启动。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cancelApplicationAutoStartup](arkts-ability-autostartupmanager-cancelapplicationautostartup-f-sys.md) | 取消应用组件开机自启动。使用callback异步回调。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [cancelApplicationAutoStartup](arkts-ability-autostartupmanager-cancelapplicationautostartup-f-sys.md) | 取消应用组件开机自启动。使用Promise异步回调。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [offSystemAutoStartup](arkts-ability-autostartupmanager-offsystemautostartup-f-sys.md) | 注销监听应用组件开机自启动状态变化的回调函数。 |
| [off_systemAutoStartup](arkts-ability-autostartupmanager-offsystemautostartup-f-sys.md) | 注销监听应用组件开机自启动状态变化的回调函数。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [onSystemAutoStartup](arkts-ability-autostartupmanager-onsystemautostartup-f-sys.md) | 注册监听应用组件开机自启动状态变化的回调函数。 |
| [on_systemAutoStartup](arkts-ability-autostartupmanager-onsystemautostartup-f-sys.md) | 注册监听应用组件开机自启动状态变化的回调函数。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [queryAllAutoStartupApplications](arkts-ability-autostartupmanager-queryallautostartupapplications-f-sys.md) | 查询自启动应用组件信息。使用callback异步回调。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [queryAllAutoStartupApplications](arkts-ability-autostartupmanager-queryallautostartupapplications-f-sys.md) | 查询自启动应用组件信息。使用Promise异步回调。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [setApplicationAutoStartup](arkts-ability-autostartupmanager-setapplicationautostartup-f-sys.md) | 设置应用组件开机自启动。使用callback异步回调。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [setApplicationAutoStartup](arkts-ability-autostartupmanager-setapplicationautostartup-f-sys.md) | 设置应用组件开机自启动。使用Promise异步回调。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
<!--DelEnd-->

