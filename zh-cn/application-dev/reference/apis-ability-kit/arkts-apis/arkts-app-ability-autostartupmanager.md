# @ohos.app.ability.autoStartupManager

autoStartupManager模块提供获取自身应用的开机自启状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace autoStartupManager--><!--Device-unnamed-declare namespace autoStartupManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelApplicationAutoStartup](arkts-ability-autostartupmanager-cancelapplicationautostartup-f.md#cancelapplicationautostartup) | 取消应用组件开机自启动。使用callback异步回调。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [cancelApplicationAutoStartup](arkts-ability-autostartupmanager-cancelapplicationautostartup-f.md#cancelapplicationautostartup-1) | 取消应用组件开机自启动。使用Promise异步回调。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [getAutoStartupStatusForSelf](arkts-ability-autostartupmanager-getautostartupstatusforself-f.md#getautostartupstatusforself) | 获取当前应用的开机自启动状态。使用Promise异步回调。 该接口仅在Phone、PC/2in1、Tablet和Wearable设备中可正常调用，在其他设备中返回801错误码。 |
| [isAutoStartupSupported](arkts-ability-autostartupmanager-isautostartupsupported-f.md#isautostartupsupported) | 检查当前设备是否支持开机自启动。 |
| [off](arkts-ability-autostartupmanager-off-f.md#off) | 注销监听应用组件开机自启动状态变化的回调函数。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [offSystemAutoStartup](arkts-ability-autostartupmanager-offsystemautostartup-f.md#offsystemautostartup) | 注销监听应用组件开机自启动状态变化的回调函数。 |
| [on](arkts-ability-autostartupmanager-on-f.md#on) | 注册监听应用组件开机自启动状态变化的回调函数。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [onSystemAutoStartup](arkts-ability-autostartupmanager-onsystemautostartup-f.md#onsystemautostartup) | 注册监听应用组件开机自启动状态变化的回调函数。 |
| [queryAllAutoStartupApplications](arkts-ability-autostartupmanager-queryallautostartupapplications-f.md#queryallautostartupapplications) | 查询自启动应用组件信息。使用callback异步回调。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [queryAllAutoStartupApplications](arkts-ability-autostartupmanager-queryallautostartupapplications-f.md#queryallautostartupapplications-1) | 查询自启动应用组件信息。使用Promise异步回调。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [setApplicationAutoStartup](arkts-ability-autostartupmanager-setapplicationautostartup-f.md#setapplicationautostartup) | 设置应用组件开机自启动。使用callback异步回调。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |
| [setApplicationAutoStartup](arkts-ability-autostartupmanager-setapplicationautostartup-f.md#setapplicationautostartup-1) | 设置应用组件开机自启动。使用Promise异步回调。 从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。 |

