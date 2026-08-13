# @ohos.resourceschedule.deviceStandby

当设备长时间未被使用，或通过按键操作时，可以使设备进入待机模式。待机模式不影响应用使用，还可以延长电池续航时间。通过本模块接口，可查询设备或应用是否为待机模式，以及为应用申请或取消待机资源管控。 > **说明：**: > > 本模块接口为系统接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace deviceStandby--><!--Device-unnamed-declare namespace deviceStandby-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getExemptedApps](arkts-backgroundtasks-devicestandby-getexemptedapps-f-sys.md#getExemptedApps) | 获取进入待机模式的应用名单，使用Callback异步回调。 |
| [getExemptedApps](arkts-backgroundtasks-devicestandby-getexemptedapps-f-sys.md#getExemptedApps（系统接口）) | 获取进入待机模式的应用名单，使用Promise异步回调。 |
| [releaseExemptionResource](arkts-backgroundtasks-devicestandby-releaseexemptionresource-f-sys.md#releaseExemptionResource) | 取消应用订阅申请豁免。 |
| [requestExemptionResource](arkts-backgroundtasks-devicestandby-requestexemptionresource-f-sys.md#requestExemptionResource) | 应用订阅申请豁免，使应用临时不进入待机管控。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExemptedAppInfo](arkts-backgroundtasks-devicestandby-exemptedappinfo-i-sys.md) | 豁免应用信息，未进入待机管控的应用信息。 |
| [ResourceRequest](arkts-backgroundtasks-devicestandby-resourcerequest-i-sys.md) | 待机资源请求体。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ResourceType](arkts-backgroundtasks-devicestandby-resourcetype-e-sys.md) | 非待机应用资源枚举。 |
<!--DelEnd-->

