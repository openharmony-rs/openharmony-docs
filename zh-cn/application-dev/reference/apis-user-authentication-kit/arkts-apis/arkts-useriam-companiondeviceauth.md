# @ohos.userIAM.companionDeviceAuth

**companionDeviceAuth**模块是OpenHarmony用户身份认证体系（UserIAM）的重要组成部分，专门用于伴随设备认证管理。该模块为系统应用提供伴随设备查询、订阅和服务范围管理等能力。

该模块主要用于以下场景：

- 管理伴随设备与主设备之间的认证关系。  
- 查询和订阅伴随设备的状态变化。  
- 管理伴随设备支持的业务范围。  
- 实现持续认证功能。  
- 处理设备选择和注册。

**起始版本：** 23

<!--Device-unnamed-declare namespace companionDeviceAuth--><!--Device-unnamed-declare namespace companionDeviceAuth-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getStatusMonitor](arkts-userauthentication-companiondeviceauth-getstatusmonitor-f-sys.md#getstatusmonitor-1) | 获取状态监听器。用于获取指定用户的状态监听器对象，通过该对象可查询和订阅伴随设备的模板状态、持续认证状态、可添加设备状态等信息。 |
| [registerDeviceSelectCallback](arkts-userauthentication-companiondeviceauth-registerdeviceselectcallback-f-sys.md#registerdeviceselectcallback-1) | 注册伴随设备选择回调。当系统需要用户选择伴随设备时，会调用此回调，应用需在回调中返回用户选择的设备信息。通过此回调，应用可以实现自定义的设备选择逻辑，如弹出设备选择界面让用户选择。 |
| [unregisterDeviceSelectCallback](arkts-userauthentication-companiondeviceauth-unregisterdeviceselectcallback-f-sys.md#unregisterdeviceselectcallback-1) | 取消注册伴随设备选择回调。取消后，系统将不再调用应用注册的设备选择回调，设备选择将回退到系统默认行为。 |
| [updateEnabledBusinessIds](arkts-userauthentication-companiondeviceauth-updateenabledbusinessids-f-sys.md#updateenabledbusinessids-1) | 更新指定伴随设备模板支持的业务范围。用于修改已注册模板的启用业务ID列表，从而控制该模板可参与的业务场景。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContinuousAuthParam](arkts-userauthentication-companiondeviceauth-continuousauthparam-i-sys.md) | 持续认证参数。用于配置订阅持续认证状态时的相关参数，如指定订阅的目标模板。 |
| [DeviceKey](arkts-userauthentication-companiondeviceauth-devicekey-i-sys.md) | 设备业务标识。用于唯一标识一个设备及其用户，包含设备ID类型、设备ID和设备用户ID等信息。 |
| [DeviceSelectResult](arkts-userauthentication-companiondeviceauth-deviceselectresult-i-sys.md) | 伴随设备选择回调的返回结果。用于在设备选择回调中返回用户选择的设备信息和扩展上下文。 |
| [DeviceStatus](arkts-userauthentication-companiondeviceauth-devicestatus-i-sys.md) | 设备状态信息。用于描述伴随设备的当前状态，包括设备业务标识、用户名、型号信息、设备名、在线状态以及支持的业务ID列表等。 |
| [StatusMonitor](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md) | 状态监听器对象。用于监听或获取模板状态、持续认证状态、可添加设备状态等信息。通过[getStatusMonitor](arkts-userauthentication-companiondeviceauth-getstatusmonitor-f-sys.md#getstatusmonitor-1)获取此对象。 |
| [TemplateStatus](arkts-userauthentication-companiondeviceauth-templatestatus-i-sys.md) | 用于描述已注册的伴随设备认证模板的完整状态信息，包括模板ID、数据确认状态、有效性、用户ID、添加时间、支持的业务范围以及关联的设备状态等。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BusinessId](arkts-userauthentication-companiondeviceauth-businessid-e-sys.md) | 业务ID枚举。业务ID是伴随设备支持的某个业务场景的唯一标识。不同的伴随设备由于认证安全性差异，支持的业务场景范围也不同，例如免解锁执行语音指令。不同业务ID的伴随设备关系是独立的，互不干扰，可以独立添加、删除、认证。当前伴随设备模块的业务有：OH默认业务、锁屏解锁、解锁应用锁以及语音指令在锁屏执行前的身份鉴权等。业务的添加对于服务端设备支持的场景有要求，如多屏协同业务，要求服务端设备支持委托认证场景。 |
| [DeviceIdType](arkts-userauthentication-companiondeviceauth-deviceidtype-e-sys.md) | 设备ID类型枚举。用于定义设备业务标识的类型，支持系统预设类型和厂商自定义扩展类型。 |
| [SelectPurpose](arkts-userauthentication-companiondeviceauth-selectpurpose-e-sys.md) | 选择伴随设备的目的。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | 回调函数，用于接收可添加的设备列表变化通知。当可添加的伴随设备列表发生变化（如新设备上线、设备离线等）时，系统会通过此回调通知应用。 |
| [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | 回调函数，用于接收持续认证状态变化通知。当伴随设备的认证状态发生变化时，系统会通过此回调通知应用当前的认证结果和认证可信等级。 |
| [DeviceSelectCallback](arkts-userauthentication-companiondeviceauth-deviceselectcallback-t-sys.md) | 伴随设备选择回调函数类型。当系统需要用户选择伴随设备时（如添加模板或执行认证），会调用此回调，应用需返回用户选择的设备信息。 |
| [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | 回调函数，用于接收模板状态变化通知。当模板状态发生变化（如添加、删除、有效性变更等）时，系统会通过此回调通知应用。 |
<!--DelEnd-->

