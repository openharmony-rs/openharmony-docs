# @ohos.continuation.continuationManager

continuationManager模块提供了流转/协同入口管理服务能力，包括连接/取消流转管理服务，注册/解注册设备连接变化监听，拉起设备选择模块，更新连接状态。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 22

**替代接口：** [distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributeddevicemanager.md#@ohos.distributedDeviceManager)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace continuationManager--><!--Device-unnamed-declare namespace continuationManager-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off_deviceConnect](arkts-ability-continuationmanager-offdeviceconnect-f.md#off_deviceConnect) | 异步方法，取消监听设备连接状态，使用Callback形式返回连接的设备信息。 |
| [off_deviceDisconnect](arkts-ability-continuationmanager-offdevicedisconnect-f.md#off_deviceDisconnect) | 异步方法，取消监听设备断开状态，使用Callback形式返回连接的设备信息。 |
| [off_deviceSelected](arkts-ability-continuationmanager-offdeviceselected-f.md#off_deviceSelected) | 取消监听设备连接状态。 |
| [off_deviceUnselected](arkts-ability-continuationmanager-offdeviceunselected-f.md#off_deviceUnselected) | 取消监听设备断开状态。 |
| [on_deviceConnect](arkts-ability-continuationmanager-ondeviceconnect-f.md#on_deviceConnect) | 异步方法，监听设备连接状态，使用Callback形式返回连接的设备信息。 |
| [on_deviceDisconnect](arkts-ability-continuationmanager-ondevicedisconnect-f.md#on_deviceDisconnect) | 异步方法，监听设备断开状态，使用Callback形式返回断开的设备信息。 |
| [on_deviceSelected](arkts-ability-continuationmanager-ondeviceselected-f.md#on_deviceSelected) | 异步方法，监听设备连接状态，使用Callback形式返回连接的设备信息。 |
| [on_deviceUnselected](arkts-ability-continuationmanager-ondeviceunselected-f.md#on_deviceUnselected) | 异步方法，监听设备断开状态，使用Callback形式返回断开的设备信息。 |
| [register](arkts-ability-continuationmanager-register-f.md#register) | 注册流转管理服务，并获取对应的注册token，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [register](arkts-ability-continuationmanager-register-f.md#register) | 连接流转管理服务，并获取对应的注册token，使用AsyncCallback方式作为异步方法。 |
| [register](arkts-ability-continuationmanager-register-f.md#register) | 连接流转管理服务，并获取对应的注册token，使用Promise方式作为异步方法。 |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md#registerContinuation) | 注册流转管理服务，并获取对应的注册token，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md#registerContinuation) | 连接流转管理服务，并获取对应的注册token，使用AsyncCallback方式作为异步方法。 |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md#registerContinuation) | 连接流转管理服务，并获取对应的注册token，使用Promise方式作为异步方法。 |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md#startContinuationDeviceManager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md#startContinuationDeviceManager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用AsyncCallback方式作为异步方法。 |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md#startContinuationDeviceManager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用Promise方式作为异步方法。 |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md#startDeviceManager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，无过滤条件，使用AsyncCallback方式作为异步方法。 |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md#startDeviceManager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用AsyncCallback方式作为异步方法。 |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md#startDeviceManager) | 拉起设备选择模块，可显示组网内可选择设备列表信息，使用Promise方式作为异步方法。 |
| [unregister](arkts-ability-continuationmanager-unregister-f.md#unregister) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用AsyncCallback方式作为异步方法。 |
| [unregister](arkts-ability-continuationmanager-unregister-f.md#unregister) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用Promise方式作为异步方法。 |
| [unregisterContinuation](arkts-ability-continuationmanager-unregistercontinuation-f.md#unregisterContinuation) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用AsyncCallback方式作为异步方法。 |
| [unregisterContinuation](arkts-ability-continuationmanager-unregistercontinuation-f.md#unregisterContinuation) | 解注册流转管理服务，传入注册时获取的token进行解注册，使用Promise方式作为异步方法。 |
| [updateConnectStatus](arkts-ability-continuationmanager-updateconnectstatus-f.md#updateConnectStatus) | 通知设备选择模块，更新当前的连接状态，使用AsyncCallback方式作为异步方法。 |
| [updateConnectStatus](arkts-ability-continuationmanager-updateconnectstatus-f.md#updateConnectStatus) | 通知设备选择模块，更新当前的连接状态，使用Promise方式作为异步方法。 |
| [updateContinuationState](arkts-ability-continuationmanager-updatecontinuationstate-f.md#updateContinuationState) | 通知设备选择模块，更新当前的连接状态，使用AsyncCallback方式作为异步方法。 |
| [updateContinuationState](arkts-ability-continuationmanager-updatecontinuationstate-f.md#updateContinuationState) | 通知设备选择模块，更新当前的连接状态，使用Promise方式作为异步方法。 |

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

