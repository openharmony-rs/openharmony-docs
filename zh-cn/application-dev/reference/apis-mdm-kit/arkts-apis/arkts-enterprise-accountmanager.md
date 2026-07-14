# @ohos.enterprise.accountManager

本模块提供设备账号管理能力，包括禁止创建本地账号等。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [activateOsAccount](arkts-mdm-activateosaccount-f.md#activateosaccount-1) | 激活系统账号 |
| [addOsAccountAsync](arkts-mdm-addosaccountasync-f.md#addosaccountasync-1) | 后台添加账号。使用Promise异步回调。 |
| [createNormalOsAccount](arkts-mdm-createnormalosaccount-f.md#createnormalosaccount-1) | 添加普通系统账号 |
| [disallowOsAccountAddition](arkts-mdm-disallowosaccountaddition-f.md#disallowosaccountaddition-1) | 禁止用户添加账号。 |
| [getDomainAccountPolicy](arkts-mdm-getdomainaccountpolicy-f.md#getdomainaccountpolicy-1) | 获取域账号策略。 |
| [isOsAccountAdditionDisallowed](arkts-mdm-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1) | 查询是否禁止用户添加账号。 |
| [removeOsAccount](arkts-mdm-removeosaccount-f.md#removeosaccount-1) | 移除系统账号 |
| [setDomainAccountPolicy](arkts-mdm-setdomainaccountpolicy-f.md#setdomainaccountpolicy-1) | 设置域账号策略。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addOsAccount](arkts-mdm-addosaccount-f-sys.md#addosaccount-1) | 后台添加账号。 |
| [disallowAddLocalAccount](arkts-mdm-disallowaddlocalaccount-f-sys.md#disallowaddlocalaccount-1) | 禁止设备创建本地账号。使用callback异步回调。 |
| [disallowAddLocalAccount](arkts-mdm-disallowaddlocalaccount-f-sys.md#disallowaddlocalaccount-2) | 禁止设备创建本地账号。使用Promise异步回调。 |
| [disallowAddOsAccountByUser](arkts-mdm-disallowaddosaccountbyuser-f-sys.md#disallowaddosaccountbyuser-1) | 禁止用户添加账号。 |
| [isAddOsAccountByUserDisallowed](arkts-mdm-isaddosaccountbyuserdisallowed-f-sys.md#isaddosaccountbyuserdisallowed-1) | 查询是否禁止某用户添加账号。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DomainAccountPolicy](arkts-mdm-domainaccountpolicy-i.md) | 域账号策略。 |

