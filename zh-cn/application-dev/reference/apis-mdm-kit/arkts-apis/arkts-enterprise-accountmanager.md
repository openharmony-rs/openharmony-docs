# @ohos.enterprise.accountManager

本模块提供设备账号管理能力，包括禁止创建本地账号等。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare namespace accountManager--><!--Device-unnamed-declare namespace accountManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [activateOsAccount](arkts-mdm-accountmanager-activateosaccount-f.md#activateosaccount) | 切换系统账号。当前仅支持手机、平板设备使用，只能在[createNormalOsAccount]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_创建的普通系统账号和默认系统账号 (ID为10 0) 之间切换。 |
| [addOsAccount](arkts-mdm-accountmanager-addosaccount-f.md#addosaccount) | 后台添加账号。 |
| [addOsAccountAsync](arkts-mdm-accountmanager-addosaccountasync-f.md#addosaccountasync) | 后台添加账号。使用Promise异步回调。适用于企业批量创建账号或远程管理场景，无需用户交互即可完成账号创建，提升管理效率。 |
| [createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md#createnormalosaccount) | 创建普通系统账号。最多可以创建2个normal类型的系统账号 ([osAccount.OsAccountType]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_) 。 |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f.md#disallowaddlocalaccount) | 禁止设备创建本地账号。使用callback异步回调。 |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f.md#disallowaddlocalaccount-1) | 禁止设备创建本地账号。使用Promise异步回调。 |
| [disallowAddOsAccountByUser](arkts-mdm-accountmanager-disallowaddosaccountbyuser-f.md#disallowaddosaccountbyuser) | 禁止用户添加账号。 |
| [disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md#disallowosaccountaddition) | 禁止用户添加账号。调用成功后，系统将禁止指定用户或所有用户添加新账号。适用于企业设备管理场景，如防止员工随意创建本地账号、加强设备安全管理等。 |
| [getDomainAccountPolicy](arkts-mdm-accountmanager-getdomainaccountpolicy-f.md#getdomainaccountpolicy) | 获取域账号策略。适用于企业管理场景，如查询当前域账号策略配置、策略合规性审计等。 |
| [isAddOsAccountByUserDisallowed](arkts-mdm-accountmanager-isaddosaccountbyuserdisallowed-f.md#isaddosaccountbyuserdisallowed) | 查询是否禁止某用户添加账号。 |
| [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed) | 查询是否禁止用户添加账号。适用于企业审计和合规检查场景，帮助管理员确认账号策略执行情况。 |
| [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1) | 查询是否禁止用户添加账号。适用于企业审计和合规检查场景，帮助管理员确认账号策略执行情况。 |
| [removeOsAccount](arkts-mdm-accountmanager-removeosaccount-f.md#removeosaccount) | 移除系统账号。当前仅支持手机、平板设备使用，可以移除使用[createNormalOsAccount]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_创建的普通系统账号（normal类型）和 [addOsAccountAsync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_创建的系统账号（admin、normal、guest类型），不可移除默认系统账号（ID为100）。 |
| [setDomainAccountPolicy](arkts-mdm-accountmanager-setdomainaccountpolicy-f.md#setdomainaccountpolicy) | 设置域账号策略。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DomainAccountPolicy](arkts-mdm-accountmanager-domainaccountpolicy-i.md) | 域账号策略。 |

