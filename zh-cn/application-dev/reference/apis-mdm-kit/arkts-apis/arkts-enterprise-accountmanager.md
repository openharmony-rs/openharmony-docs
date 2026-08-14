# @ohos.enterprise.accountManager

本模块提供设备账号管理能力，包括禁止创建本地账号等。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare namespace accountManager--><!--Device-unnamed-declare namespace accountManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [activateOsAccount](arkts-mdm-accountmanager-activateosaccount-f.md#activateOsAccount) | 切换系统账号。当前仅支持手机、平板设备使用，只能在[createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md#createNormalOsAccount)创建的普通系统账号和默认系统账号 (ID为10 0) 之间切换。 |
| [addOsAccountAsync](arkts-mdm-accountmanager-addosaccountasync-f.md#addOsAccountAsync) | 后台添加账号。使用Promise异步回调。适用于企业批量创建账号或远程管理场景，无需用户交互即可完成账号创建，提升管理效率。 |
| [createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md#createNormalOsAccount) | 创建普通系统账号。最多可以创建2个normal类型的系统账号 ([osAccount.OsAccountType](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-osaccounttype-e.md#OsAccountType)) 。 |
| [disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md#disallowOsAccountAddition) | 禁止用户添加账号。调用成功后，系统将禁止指定用户或所有用户添加新账号。适用于企业设备管理场景，如防止员工随意创建本地账号、加强设备安全管理等。 |
| [getDomainAccountPolicy](arkts-mdm-accountmanager-getdomainaccountpolicy-f.md#getDomainAccountPolicy) | 获取域账号策略。适用于企业管理场景，如查询当前域账号策略配置、策略合规性审计等。 |
| [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isOsAccountAdditionDisallowed) | 查询是否禁止用户添加账号。适用于企业审计和合规检查场景，帮助管理员确认账号策略执行情况。 |
| [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isOsAccountAdditionDisallowed) | 查询是否禁止用户添加账号。适用于企业审计和合规检查场景，帮助管理员确认账号策略执行情况。 |
| [removeOsAccount](arkts-mdm-accountmanager-removeosaccount-f.md#removeOsAccount) | 移除系统账号。当前仅支持手机、平板设备使用，可以移除使用[createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md#createNormalOsAccount)创建的普通系统账号（normal类型）和 [addOsAccountAsync](arkts-mdm-accountmanager-addosaccountasync-f.md#addOsAccountAsync)创建的系统账号（admin、normal、guest类型），不可移除默认系统账号（ID为100）。 |
| [setDomainAccountPolicy](arkts-mdm-accountmanager-setdomainaccountpolicy-f.md#setDomainAccountPolicy) | 设置域账号策略。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addOsAccount](arkts-mdm-accountmanager-addosaccount-f-sys.md#addOsAccount) | 后台添加账号。 |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f-sys.md#disallowAddLocalAccount) | 禁止设备创建本地账号。使用callback异步回调。 |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f-sys.md#disallowAddLocalAccount（系统接口）) | 禁止设备创建本地账号。使用Promise异步回调。 |
| [disallowAddOsAccountByUser](arkts-mdm-accountmanager-disallowaddosaccountbyuser-f-sys.md#disallowAddOsAccountByUser) | 禁止用户添加账号。 |
| [isAddOsAccountByUserDisallowed](arkts-mdm-accountmanager-isaddosaccountbyuserdisallowed-f-sys.md#isAddOsAccountByUserDisallowed) | 查询是否禁止某用户添加账号。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DomainAccountPolicy](arkts-mdm-accountmanager-domainaccountpolicy-i.md) | 域账号策略。 |

