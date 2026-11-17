# @ohos.app.ability.launchServiceManager

该模块提供了对LaunchService进行管理的能力。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace launchServiceManager--><!--Device-unnamed-declare namespace launchServiceManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [connectService](arkts-ability-launchservicemanager-connectservice-f.md#connectservice-1) | 连接LaunchService进程，用于IPC通信。目标LaunchService必须已声明IPC服务。若该LaunchService进程尚未运行，系统会在建立连接前自动将其启动。目标服务和调用者必须属于同一个开发者。连接结果通过callback中的回调下发。 |
| [disconnectService](arkts-ability-launchservicemanager-disconnectservice-f.md#disconnectservice-1) | 断开与LaunchService进程的连接。 |
| [getInformation](arkts-ability-launchservicemanager-getinformation-f.md#getinformation-1) | 获取指定LaunchService的信息。如果应用程序已安装，但LaunchService未注册，返回的状态为NOT_REGISTERED，pid为0。 |
| [register](arkts-ability-launchservicemanager-register-f.md#register-1) | 注册LaunchService。在module.json5配置文件中将runAtLoad设置为true，且服务注册成功，状态为ENABLED，系统将自动启动LaunchService进程。仅允许包含该LaunchService的应用自身进行注册，且需根据应用类型申请对应权限：  - 普通应用（非MDM应用）：需申请ohos.permission.REGISTER_DAEMON_SERVICE权限。  - MDM应用：需申请ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE权限。 |
| [start](arkts-ability-launchservicemanager-start-f.md#start-1) | 启动LaunchService进程。调用此接口前，必须确保LaunchService已完成注册且处于启动（ENABLED）状态。 |
| [stop](arkts-ability-launchservicemanager-stop-f.md#stop-1) | 停止LaunchService进程。 |
| [unregister](arkts-ability-launchservicemanager-unregister-f.md#unregister-1) | 注销LaunchService。若LaunchService进程正在运行，注销时系统将停止该进程。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllRegisteredInformation](arkts-ability-launchservicemanager-getallregisteredinformation-f-sys.md#getallregisteredinformation-1) | 获取所有已注册的LaunchService信息。 |
| [offLaunchServiceObserver](arkts-ability-launchservicemanager-offlaunchserviceobserver-f-sys.md#offlaunchserviceobserver-1) | 注销用于监听LaunchService状态和进程状态更改的观察者。 |
| [onLaunchServiceObserver](arkts-ability-launchservicemanager-onlaunchserviceobserver-f-sys.md#onlaunchserviceobserver-1) | 注册一个观察者来监听LaunchService状态和进程状态的变化。 |
| [setLaunchServicesEnabled](arkts-ability-launchservicemanager-setlaunchservicesenabled-f-sys.md#setlaunchservicesenabled-1) | 设置应用LaunchService的启用状态。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [LaunchServiceConnectCallback](arkts-ability-launchservicemanager-launchserviceconnectcallback-t.md) | 定义在LaunchService连接回调。 |
| [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | 定义LaunchService的描述符。 |
| [LaunchServiceInformation](arkts-ability-launchservicemanager-launchserviceinformation-t.md) | 定义LaunchService信息结构体。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LaunchServiceObserver](arkts-ability-launchservicemanager-launchserviceobserver-t-sys.md) | 定义LaunchService状态和进程状态变化的观察者。 |
| [LaunchServiceProcessStateData](arkts-ability-launchservicemanager-launchserviceprocessstatedata-t-sys.md) | 定义LaunchService进程状态变化数据结构体。 |
| [LaunchServiceStateData](arkts-ability-launchservicemanager-launchservicestatedata-t-sys.md) | 定义LaunchService状态变化数据结构体。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LaunchServiceState](arkts-ability-launchservicemanager-launchservicestate-e.md) | 定义LaunchService状态的枚举类型，用于[LaunchServiceInformation](arkts-ability-launchserviceinformation-i.md)。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LaunchServiceProcessState](arkts-ability-launchservicemanager-launchserviceprocessstate-e-sys.md) | 定义LaunchService进程状态的枚举类型，用于[LaunchServiceProcessState](arkts-ability-launchserviceprocessstatedata-i-sys.md)。 |
<!--DelEnd-->
