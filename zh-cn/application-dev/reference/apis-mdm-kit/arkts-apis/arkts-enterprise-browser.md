# @ohos.enterprise.browser

本模块提供浏览器管理能力，包括设置/取消浏览器策略、获取浏览器策略等。适用于企业设备管理、员工上网行为管控、安全合规审计等场景。 浏览器策略指通过配置或管理浏览器行为的一系列规则和设置，以确保安全性、合规性、性能优化和用户体验的一致性。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare namespace browser--><!--Device-unnamed-declare namespace browser-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getManagedBrowserPolicy](arkts-mdm-browser-getmanagedbrowserpolicy-f.md#getmanagedbrowserpolicy) | 通过应用包名获取指定浏览器的浏览器策略，适用于查询当前浏览器策略配置的场景，例如在企业设备管理应用中展示策略详情、验证策略是否生效等。 |
| [getPolicies](arkts-mdm-browser-getpolicies-f.md#getpolicies) | 获取指定浏览器的策略，使用callback异步回调。 |
| [getPolicies](arkts-mdm-browser-getpolicies-f.md#getpolicies-1) | 获取指定浏览器的策略，使用Promise异步回调。 |
| [getPoliciesSync](arkts-mdm-browser-getpoliciessync-f.md#getpoliciessync) | 通过appid获取指定浏览器设置的策略，适用于查询当前浏览器策略配置的场景，例如在企业设备管理应用中展示策略详情、验证策略是否生效等。 |
| [getPoliciesSync](arkts-mdm-browser-getpoliciessync-f.md#getpoliciessync-1) | 通过appid获取指定浏览器设置的策略，适用于查询当前浏览器策略配置的场景，例如在企业设备管理应用中展示策略详情、验证策略是否生效等。 |
| [getSelfManagedBrowserPolicy](arkts-mdm-browser-getselfmanagedbrowserpolicy-f.md#getselfmanagedbrowserpolicy) | 获取当前设备浏览器策略。 |
| [getSelfManagedBrowserPolicyVersion](arkts-mdm-browser-getselfmanagedbrowserpolicyversion-f.md#getselfmanagedbrowserpolicyversion) | 获取当前设备浏览器策略版本。 |
| [setManagedBrowserPolicy](arkts-mdm-browser-setmanagedbrowserpolicy-f.md#setmanagedbrowserpolicy) | 为指定的浏览器设置浏览器策略，适用于企业统一管理员工浏览器行为的场景，例如配置浏览器安全策略等。成功后会发布系统公共事件 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [setPolicies](arkts-mdm-browser-setpolicies-f.md#setpolicies) | 为指定的浏览器设置浏览策略，使用callback异步回调。 |
| [setPolicies](arkts-mdm-browser-setpolicies-f.md#setpolicies-1) | 为指定的浏览器设置浏览策略，使用Promise异步回调。 |
| [setPolicySync](arkts-mdm-browser-setpolicysync-f.md#setpolicysync) | 为指定的浏览器设置浏览器子策略，适用于企业统一管理员工浏览器行为的场景。 |

