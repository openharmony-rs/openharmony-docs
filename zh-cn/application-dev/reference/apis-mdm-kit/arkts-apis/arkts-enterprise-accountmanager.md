# @ohos.enterprise.accountManager

本模块提供设备账号管理能力，包括禁止创建本地账号等。
> **说明：**  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace accountManager--><!--Device-unnamed-declare namespace accountManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [activateOsAccount](arkts-mdm-accountmanager-activateosaccount-f.md#activateosaccount) | 激活系统账号 |
| [addOsAccountAsync](arkts-mdm-accountmanager-addosaccountasync-f.md#addosaccountasync) | 后台添加账号。使用Promise异步回调。 |
| [createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md#createnormalosaccount) | 添加普通系统账号 |
| [disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md#disallowosaccountaddition) | 禁止用户添加账号。 |
| [getDomainAccountPolicy](arkts-mdm-accountmanager-getdomainaccountpolicy-f.md#getdomainaccountpolicy) | 获取域账号策略。 |
| [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed) | 查询是否禁止用户添加账号。 |
| [removeOsAccount](arkts-mdm-accountmanager-removeosaccount-f.md#removeosaccount) | 移除系统账号 |
| [setDomainAccountPolicy](arkts-mdm-accountmanager-setdomainaccountpolicy-f.md#setdomainaccountpolicy) | 设置域账号策略。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addOsAccount](arkts-mdm-accountmanager-addosaccount-f-sys.md#addosaccount) | 后台添加账号。 |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f-sys.md#disallowaddlocalaccount) | 禁止设备创建本地账号。使用callback异步回调。 |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f-sys.md#disallowaddlocalaccount-1) | 禁止设备创建本地账号。使用Promise异步回调。 |
| [disallowAddOsAccountByUser](arkts-mdm-accountmanager-disallowaddosaccountbyuser-f-sys.md#disallowaddosaccountbyuser) | 禁止用户添加账号。 |
| [isAddOsAccountByUserDisallowed](arkts-mdm-accountmanager-isaddosaccountbyuserdisallowed-f-sys.md#isaddosaccountbyuserdisallowed) | 查询是否禁止某用户添加账号。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DomainAccountPolicy](arkts-mdm-accountmanager-domainaccountpolicy-i.md) | 域账号策略。 |

