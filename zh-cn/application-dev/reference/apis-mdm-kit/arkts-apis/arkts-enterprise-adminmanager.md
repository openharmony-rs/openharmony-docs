# @ohos.enterprise.adminManager

本模块为企业MDM应用提供admin权限管理能力，包括激活/解除激活admin权限、事件订阅、委托授权等。 > **说明：** > > 本模块接口仅对设备管理应用开放，具体请参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace adminManager--><!--Device-unnamed-declare namespace adminManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [authorizeAdmin](arkts-mdm-adminmanager-authorizeadmin-f.md#authorizeadmin) | 授予指定应用管理员权限。使用callback异步回调。 |
| [authorizeAdmin](arkts-mdm-adminmanager-authorizeadmin-f.md#authorizeadmin-1) | 授予指定应用管理员权限。使用Promise异步回调。 |
| [disableAdmin](arkts-mdm-adminmanager-disableadmin-f.md#disableadmin) | 将当前用户下指定的普通设备管理应用解除激活。使用callback异步回调。 |
| [disableAdmin](arkts-mdm-adminmanager-disableadmin-f.md#disableadmin-1) | 将指定用户（通过userId指定）下指定的普通管理应用解除激活。使用callback异步回调。 |
| [disableAdmin](arkts-mdm-adminmanager-disableadmin-f.md#disableadmin-2) | 解除激活指定用户的设备管理应用。使用Promise异步回调。调用成功后，指定的设备管理应用将被解除激活，不再具备设备管理能力。 |
| [disableDeviceAdmin](arkts-mdm-adminmanager-disabledeviceadmin-f.md#disabledeviceadmin) | \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_应用通过该接口可以解除激活其他 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_应用，使用Promise异步回调。调用成功后，指定的DA应用将被解除激活，不再具备设备管理能力。该接口仅支持超级设 备管理应用调用。 |
| [disableSuperAdmin](arkts-mdm-adminmanager-disablesuperadmin-f.md#disablesuperadmin) | 根据bundleName将超级设备管理应用解除激活。使用callback异步回调。 |
| [disableSuperAdmin](arkts-mdm-adminmanager-disablesuperadmin-f.md#disablesuperadmin-1) | 根据bundleName将超级设备管理应用解除激活。使用Promise异步回调。 |
| [enableAdmin](arkts-mdm-adminmanager-enableadmin-f.md#enableadmin) | 激活指定的设备管理应用。超级设备管理应用仅在首用户（u100）下可激活。激活后，应用不可卸载，其 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_组件将开机自启并在用户切换后自启。使用callback异步回 调。 |
| [enableAdmin](arkts-mdm-adminmanager-enableadmin-f.md#enableadmin-1) | 激活指定用户（通过userId指定）下指定的设备管理应用，其中超级管理应用仅能在首用户（u100）下被激活。使用callback异步回调。 |
| [enableAdmin](arkts-mdm-adminmanager-enableadmin-f.md#enableadmin-2) | 激活当前/指定用户下指定的设备管理应用，其中超级管理应用仅能在首用户（u100）下被激活。使用Promise异步回调。 |
| [enableDeviceAdmin](arkts-mdm-adminmanager-enabledeviceadmin-f.md#enabledeviceadmin) | \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_应用通过该接口可以激活其他 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_应用，使用Promise异步回调。调用成功后，指定的DA应用将被激活并具备设备管理能力。该接口仅支持超级设备管理应 用调用。 |
| [enableSelfDeviceAdmin](arkts-mdm-adminmanager-enableselfdeviceadmin-f.md#enableselfdeviceadmin) | 在企业设备中，MDM应用没有预置激活的场景下，MDM应用可以通过该接口实现自激活。该接口仅支持激活MDM应用自身，不支持激活其他MDM应用；支持的激活类型包括超级设备管理应用和普通设备管理应用。 |
| [getAdmins](arkts-mdm-adminmanager-getadmins-f.md#getadmins) | 查询当前用户下的所有设备管理应用。使用Promise异步回调。 |
| [getDelegatedBundleNames](arkts-mdm-adminmanager-getdelegatedbundlenames-f.md#getdelegatedbundlenames) | 查询可以访问某个委托策略的被委托应用，输出被委托应用列表。 |
| [getDelegatedPolicies](arkts-mdm-adminmanager-getdelegatedpolicies-f.md#getdelegatedpolicies) | 查询被委托应用可访问的策略列表。 |
| [getEnterpriseInfo](arkts-mdm-adminmanager-getenterpriseinfo-f.md#getenterpriseinfo) | 获取设备管理应用的企业信息。使用callback异步回调。 |
| [getEnterpriseInfo](arkts-mdm-adminmanager-getenterpriseinfo-f.md#getenterpriseinfo-1) | 获取设备管理应用的企业信息，使用Promise异步回调。 |
| [getEnterpriseManagedTips](arkts-mdm-adminmanager-getenterprisemanagedtips-f.md#getenterprisemanagedtips) | 查询企业定制信息 |
| [getSuperAdmin](arkts-mdm-adminmanager-getsuperadmin-f.md#getsuperadmin) | 查询首用户（u100）下的超级设备管理应用。使用Promise异步回调。 |
| [isAdminEnabled](arkts-mdm-adminmanager-isadminenabled-f.md#isadminenabled) | 查询当前用户下指定的设备管理应用是否被激活。使用callback异步回调。 |
| [isAdminEnabled](arkts-mdm-adminmanager-isadminenabled-f.md#isadminenabled-1) | 查询指定用户（通过userId指定）下指定的设备管理应用是否被激活。使用callback异步回调。 |
| [isAdminEnabled](arkts-mdm-adminmanager-isadminenabled-f.md#isadminenabled-2) | 查询当前/指定用户下指定的设备管理应用是否被激活。使用Promise异步回调。 |
| [isByodAdmin](arkts-mdm-adminmanager-isbyodadmin-f.md#isbyodadmin) | 根据企业设备管理扩展组件查询当前应用是否被激活为BYOD设备管理应用。 |
| [isSuperAdmin](arkts-mdm-adminmanager-issuperadmin-f.md#issuperadmin) | 根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用callback异步回调。 |
| [isSuperAdmin](arkts-mdm-adminmanager-issuperadmin-f.md#issuperadmin-1) | 根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用Promise异步回调。 |
| [replaceSuperAdmin](arkts-mdm-adminmanager-replacesuperadmin-f.md#replacesuperadmin) | 将指定应用替换成超级设备管理应用。 |
| [setAdminRunningMode](arkts-mdm-adminmanager-setadminrunningmode-f.md#setadminrunningmode) | 设置设备管理应用的运行模式。 |
| [setDelegatedPolicies](arkts-mdm-adminmanager-setdelegatedpolicies-f.md#setdelegatedpolicies) | 委托其他应用来设置设备的管控策略。被委托的其他应用需申请委托策略对应接口所需权限。 |
| [setDelegatedPolicies](arkts-mdm-adminmanager-setdelegatedpolicies-f.md#setdelegatedpolicies-1) | 委托其他应用来设置设备的管控策略。被委托的其他应用需申请委托策略对应接口所需权限。 |
| [setEnterpriseInfo](arkts-mdm-adminmanager-setenterpriseinfo-f.md#setenterpriseinfo) | 设置设备管理应用的企业信息。使用callback异步回调。 |
| [setEnterpriseInfo](arkts-mdm-adminmanager-setenterpriseinfo-f.md#setenterpriseinfo-1) | 设置设备管理应用的企业信息。使用Promise异步回调。 |
| [startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startadminprovision) | 设备管理应用拉起BYOD管理员激活页面进行激活。 |
| [subscribeManagedEvent](arkts-mdm-adminmanager-subscribemanagedevent-f.md#subscribemanagedevent) | 订阅系统管理事件。使用callback异步回调。 |
| [subscribeManagedEvent](arkts-mdm-adminmanager-subscribemanagedevent-f.md#subscribemanagedevent-1) | 订阅系统管理事件。使用Promise异步回调。 |
| [subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribemanagedeventsync) | 订阅系统管理事件。调用成功后，当已订阅的系统管理事件发生时，设备管理应用将收到相应的通知。 从API版本26.0.0开始，非超级设备管理应用调用该接口订阅[MANAGED\_\_\_ESCAPED\_UNDERSCORE\_\_\_EVENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_POLICIES\_\_\_ESCAPED\_UNDERSCORE\_\_\_CHANGED]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_事件时返回9200002错误码。 |
| [unsubscribeManagedEvent](arkts-mdm-adminmanager-unsubscribemanagedevent-f.md#unsubscribemanagedevent) | 取消订阅系统管理事件。使用callback异步回调。 |
| [unsubscribeManagedEvent](arkts-mdm-adminmanager-unsubscribemanagedevent-f.md#unsubscribemanagedevent-1) | 取消订阅系统管理事件。使用Promise异步回调。 |
| [unsubscribeManagedEventSync](arkts-mdm-adminmanager-unsubscribemanagedeventsync-f.md#unsubscribemanagedeventsync) | 取消订阅系统管理事件。调用成功后，将不再收到已取消订阅的系统管理事件通知。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EnterpriseInfo](arkts-mdm-adminmanager-enterpriseinfo-i.md) | 设备管理应用的企业信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AdminType](arkts-mdm-adminmanager-admintype-e.md) | 设备管理应用的类型。 |
| [ManagedEvent](arkts-mdm-adminmanager-managedevent-e.md) | 可订阅的系统管理事件。 |
| [Policy](arkts-mdm-adminmanager-policy-e.md) | 允许或禁用名单的策略类型。 |
| [RunningMode](arkts-mdm-adminmanager-runningmode-e.md) | 设备管理的运行模式。 |

