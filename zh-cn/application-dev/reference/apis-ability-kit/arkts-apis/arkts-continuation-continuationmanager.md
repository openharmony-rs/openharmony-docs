# @ohos.continuation.continuationManager

continuationManager模块提供了流转/协同入口管理服务能力，包括连接/取消流转管理服务，注册/解注册设备连接变化监听，拉起设备选择模块，更新连接状态。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** [distributedDeviceManager:distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributeddevicemanager.md)

<!--Device-unnamed-declare namespace continuationManager--><!--Device-unnamed-declare namespace continuationManager-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

## 导入模块

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off](arkts-ability-continuationmanager-off-f.md#off) | 取消监听设备连接状态。 |
| [off](arkts-ability-continuationmanager-off-f.md#off-1) | 取消监听设备断开状态。 |
| [off](arkts-ability-continuationmanager-off-f.md#off-2) | 异步方法，取消监听设备连接状态，使用Callback形式返回连接的设备信息。 |
| [off](arkts-ability-continuationmanager-off-f.md#off-3) | 异步方法，取消监听设备断开状态，使用Callback形式返回连接的设备信息。 |
| [on](arkts-ability-continuationmanager-on-f.md#on) | 异步方法，监听设备连接状态，使用Callback形式返回连接的设备信息。 |
| [on](arkts-ability-continuationmanager-on-f.md#on-1) | 异步方法，监听设备断开状态，使用Callback形式返回断开的设备信息。 |
| [on](arkts-ability-continuationmanager-on-f.md#on-2) | 异步方法，监听设备连接状态，使用Callback形式返回连接的设备信息。 |
| [on](arkts-ability-continuationmanager-on-f.md#on-3) | 异步方法，监听设备断开状态，使用Callback形式返回断开的设备信息。 |
| [register](arkts-ability-continuationmanager-register-f.md#register) | 注册流转管理服务，并获取对应的注册token，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [register](arkts-ability-continuationmanager-register-f.md#register-1) | 连接流转管理服务，并获取对应的注册token，使用AsyncCallback方式作为异步方法。 |
| [register](arkts-ability-continuationmanager-register-f.md#register-2) | 连接流转管理服务，并获取对应的注册token，使用Promise方式作为异步方法。 |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md#registercontinuation) | 注册流转管理服务，并获取对应的注册token，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md#registercontinuation-1) | 连接流转管理服务，并获取对应的注册token，使用AsyncCallback方式作为异步方法。 |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md#registercontinuation-2) | 连接流转管理服务，并获取对应的注册token，使用Promise方式作为异步方法。 |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md#startcontinuationdevicemanager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md#startcontinuationdevicemanager-1) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用AsyncCallback方式作为异步方法。 |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md#startcontinuationdevicemanager-2) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用Promise方式作为异步方法。 |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md#startdevicemanager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md#startdevicemanager-1) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用AsyncCallback方式作为异步方法。 |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md#startdevicemanager-2) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用Promise方式作为异步方法。 |
| [unregister](arkts-ability-continuationmanager-unregister-f.md#unregister) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用AsyncCallback方式作为异步方法。 |
| [unregister](arkts-ability-continuationmanager-unregister-f.md#unregister-1) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用Promise方式作为异步方法。 |
| [unregisterContinuation](arkts-ability-continuationmanager-unregistercontinuation-f.md#unregistercontinuation) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用AsyncCallback方式作为异步方法。 |
| [unregisterContinuation](arkts-ability-continuationmanager-unregistercontinuation-f.md#unregistercontinuation-1) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用Promise方式作为异步方法。 |
| [updateConnectStatus](arkts-ability-continuationmanager-updateconnectstatus-f.md#updateconnectstatus) | 通知设备选择模块，更新当前的连接状态，使用AsyncCallback方式作为异步方法。 |
| [updateConnectStatus](arkts-ability-continuationmanager-updateconnectstatus-f.md#updateconnectstatus-1) | 通知设备选择模块，更新当前的连接状态，使用Promise方式作为异步方法。 |
| [updateContinuationState](arkts-ability-continuationmanager-updatecontinuationstate-f.md#updatecontinuationstate) | 通知设备选择模块，更新当前的连接状态，使用AsyncCallback方式作为异步方法。 |
| [updateContinuationState](arkts-ability-continuationmanager-updatecontinuationstate-f.md#updatecontinuationstate-1) | 通知设备选择模块，更新当前的连接状态，使用Promise方式作为异步方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContinuationMode](arkts-ability-continuationmanager-continuationmode-e.md) | 设备选择模块连接模式。 |
| [DeviceConnectState](arkts-ability-continuationmanager-deviceconnectstate-e.md) | 设备连接状态。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ContinuationExtraParams](arkts-ability-continuationmanager-continuationextraparams-t.md) | 流转管理入口中设备选择模块所需的过滤参数。 |
| [ContinuationResult](arkts-ability-continuationmanager-continuationresult-t.md) | 流转管理入口返回的设备信息。 |

