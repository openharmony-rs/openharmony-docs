# @ohos.enterprise.adminManager

本模块为企业MDM应用提供admin权限管理能力，包括激活/解除激活admin权限、事件订阅、委托授权等。 > **说明：** > > 本模块接口仅对设备管理应用开放，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 23

<!--Device-unnamed-declare namespace adminManager--><!--Device-unnamed-declare namespace adminManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [disableAdmin](arkts-mdm-adminmanager-disableadmin-f.md) | 解除激活指定用户的设备管理应用。使用Promise异步回调。调用成功后，指定的设备管理应用将被解除激活，不再具备设备管理能力。 |
| [disableDeviceAdmin](arkts-mdm-adminmanager-disabledeviceadmin-f.md) | [SDA](../../../mdm/mdm-kit-term.md#super-device-admin-sda超级设备管理员)应用通过该接口可以解除激活其他 [DA](../../../mdm/mdm-kit-term.md#device-admin-da普通设备管理员)应用，使用Promise异步回调。调用成功后，指定的DA应用将被解除激活，不再具备设备管理能力。该接口仅支持超级设 备管理应用调用。 |
| [enableDeviceAdmin](arkts-mdm-adminmanager-enabledeviceadmin-f.md) | [SDA](../../../mdm/mdm-kit-term.md#super-device-admin-sda超级设备管理员)应用通过该接口可以激活其他 [DA](../../../mdm/mdm-kit-term.md#device-admin-da普通设备管理员)应用，使用Promise异步回调。调用成功后，指定的DA应用将被激活并具备设备管理能力。该接口仅支持超级设备管理应 用调用。 |
| [enableSelfDeviceAdmin](arkts-mdm-adminmanager-enableselfdeviceadmin-f.md) | 在企业设备中，MDM应用没有预置激活的场景下，MDM应用可以通过该接口实现自激活。该接口仅支持激活MDM应用自身，不支持激活其他MDM应用；支持的激活类型包括超级设备管理应用和普通设备管理应用。 |
| [getDelegatedBundleNames](arkts-mdm-adminmanager-getdelegatedbundlenames-f.md) | 查询可以访问某个委托策略的被委托应用，输出被委托应用列表。 |
| [getDelegatedPolicies](arkts-mdm-adminmanager-getdelegatedpolicies-f.md) | 查询被委托应用可访问的策略列表。 |
| [isByodAdmin](arkts-mdm-adminmanager-isbyodadmin-f.md) | 根据企业设备管理扩展组件查询当前应用是否被激活为BYOD设备管理应用。 |
| [setDelegatedPolicies](arkts-mdm-adminmanager-setdelegatedpolicies-f.md) | 委托其他应用来设置设备的管控策略。被委托的其他应用需申请委托策略对应接口所需权限。 |
| [startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md) | 设备管理应用拉起BYOD管理员激活页面进行激活。 |
| [subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md) | 订阅系统管理事件。调用成功后，当已订阅的系统管理事件发生时，设备管理应用将收到相应的通知。 从API版本26.0.0开始，非超级设备管理应用调用该接口订阅[MANAGED_EVENT_POLICIES_CHANGED](arkts-mdm-adminmanager-managedevent-e.md)事件时返回9200002错误码。 |
| [unsubscribeManagedEventSync](arkts-mdm-adminmanager-unsubscribemanagedeventsync-f.md) | 取消订阅系统管理事件。调用成功后，将不再收到已取消订阅的系统管理事件通知。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [authorizeAdmin](arkts-mdm-adminmanager-authorizeadmin-f-sys.md) | 授予指定应用管理员权限。使用callback异步回调。 |
| [authorizeAdmin](arkts-mdm-adminmanager-authorizeadmin-f-sys.md) | 授予指定应用管理员权限。使用Promise异步回调。 |
| [disableAdmin](arkts-mdm-adminmanager-disableadmin-f-sys.md) | 将当前用户下指定的普通设备管理应用解除激活。使用callback异步回调。 |
| [disableAdmin](arkts-mdm-adminmanager-disableadmin-f-sys.md) | 将指定用户（通过userId指定）下指定的普通管理应用解除激活。使用callback异步回调。 |
| [disableSuperAdmin](arkts-mdm-adminmanager-disablesuperadmin-f-sys.md) | 根据bundleName将超级设备管理应用解除激活。使用callback异步回调。 |
| [disableSuperAdmin](arkts-mdm-adminmanager-disablesuperadmin-f-sys.md) | 根据bundleName将超级设备管理应用解除激活。使用Promise异步回调。 |
| [enableAdmin](arkts-mdm-adminmanager-enableadmin-f-sys.md) | 激活指定的设备管理应用。超级设备管理应用仅在首用户（u100）下可激活。激活后，应用不可卸载，其 [企业设备管理扩展能力](../../../mdm/mdm-kit-term.md#enterpriseadminextensionability企业设备管理扩展能力)组件将开机自启并在用户切换后自启。使用callback异步回 调。 |
| [enableAdmin](arkts-mdm-adminmanager-enableadmin-f-sys.md) | 激活指定用户（通过userId指定）下指定的设备管理应用，其中超级管理应用仅能在首用户（u100）下被激活。使用callback异步回调。 |
| [enableAdmin](arkts-mdm-adminmanager-enableadmin-f-sys.md) | 激活当前/指定用户下指定的设备管理应用，其中超级管理应用仅能在首用户（u100）下被激活。使用Promise异步回调。 |
| [getAdmins](arkts-mdm-adminmanager-getadmins-f-sys.md) | 查询当前用户下的所有设备管理应用。使用Promise异步回调。 |
| [getEnterpriseInfo](arkts-mdm-adminmanager-getenterpriseinfo-f-sys.md) | 获取设备管理应用的企业信息。使用callback异步回调。 |
| [getEnterpriseInfo](arkts-mdm-adminmanager-getenterpriseinfo-f-sys.md) | 获取设备管理应用的企业信息，使用Promise异步回调。 |
| [getEnterpriseManagedTips](arkts-mdm-adminmanager-getenterprisemanagedtips-f-sys.md) | 查询企业定制信息 |
| [getSuperAdmin](arkts-mdm-adminmanager-getsuperadmin-f-sys.md) | 查询首用户（u100）下的超级设备管理应用。使用Promise异步回调。 |
| [isAdminEnabled](arkts-mdm-adminmanager-isadminenabled-f-sys.md) | 查询当前用户下指定的设备管理应用是否被激活。使用callback异步回调。 |
| [isAdminEnabled](arkts-mdm-adminmanager-isadminenabled-f-sys.md) | 查询指定用户（通过userId指定）下指定的设备管理应用是否被激活。使用callback异步回调。 |
| [isAdminEnabled](arkts-mdm-adminmanager-isadminenabled-f-sys.md) | 查询当前/指定用户下指定的设备管理应用是否被激活。使用Promise异步回调。 |
| [isSuperAdmin](arkts-mdm-adminmanager-issuperadmin-f-sys.md) | 根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用callback异步回调。 |
| [isSuperAdmin](arkts-mdm-adminmanager-issuperadmin-f-sys.md) | 根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用Promise异步回调。 |
| [replaceSuperAdmin](arkts-mdm-adminmanager-replacesuperadmin-f-sys.md) | 将指定应用替换成超级设备管理应用。 |
| [setAdminRunningMode](arkts-mdm-adminmanager-setadminrunningmode-f-sys.md) | 设置设备管理应用的运行模式。 |
| [setDelegatedPolicies](arkts-mdm-adminmanager-setdelegatedpolicies-f-sys.md) | 委托其他应用来设置设备的管控策略。被委托的其他应用需申请委托策略对应接口所需权限。 |
| [setEnterpriseInfo](arkts-mdm-adminmanager-setenterpriseinfo-f-sys.md) | 设置设备管理应用的企业信息。使用callback异步回调。 |
| [setEnterpriseInfo](arkts-mdm-adminmanager-setenterpriseinfo-f-sys.md) | 设置设备管理应用的企业信息。使用Promise异步回调。 |
| [subscribeManagedEvent](arkts-mdm-adminmanager-subscribemanagedevent-f-sys.md) | 订阅系统管理事件。使用callback异步回调。 |
| [subscribeManagedEvent](arkts-mdm-adminmanager-subscribemanagedevent-f-sys.md) | 订阅系统管理事件。使用Promise异步回调。 |
| [unsubscribeManagedEvent](arkts-mdm-adminmanager-unsubscribemanagedevent-f-sys.md) | 取消订阅系统管理事件。使用callback异步回调。 |
| [unsubscribeManagedEvent](arkts-mdm-adminmanager-unsubscribemanagedevent-f-sys.md) | 取消订阅系统管理事件。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EnterpriseInfo](arkts-mdm-adminmanager-enterpriseinfo-i-sys.md) | 设备管理应用的企业信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AdminType](arkts-mdm-adminmanager-admintype-e.md) | 设备管理应用的类型。 |
| [ManagedEvent](arkts-mdm-adminmanager-managedevent-e.md) | 可订阅的系统管理事件。 |
| [Policy](arkts-mdm-adminmanager-policy-e.md) | 允许或禁用名单的策略类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AdminType](arkts-mdm-adminmanager-admintype-e-sys.md) | 设备管理应用的类型。 |
| [RunningMode](arkts-mdm-adminmanager-runningmode-e-sys.md) | 设备管理的运行模式。 |
<!--DelEnd-->

