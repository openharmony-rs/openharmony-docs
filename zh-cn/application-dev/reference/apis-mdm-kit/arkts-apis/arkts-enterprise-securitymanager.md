# @ohos.enterprise.securityManager

本模块提供设备安全管理的能力，包括查询安全补丁状态、查询文件加密状态等。
> **说明：**  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 11

<!--Device-unnamed-declare namespace securityManager--><!--Device-unnamed-declare namespace securityManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedPermissionBundle](arkts-mdm-securitymanager-addallowedpermissionbundle-f.md#addallowedpermissionbundle) | 添加允许使用已禁用指定权限的应用到权限使用例外名单，权限使用例外名单中的应用可以不受[setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md#setdisallowedpermission)的策略限制。 |
| [addUserExtCredential](arkts-mdm-securitymanager-adduserextcredential-f.md#adduserextcredential) | 添加扩展用户认证凭据 |
| [cancelScreenWatermarkImage](arkts-mdm-securitymanager-cancelscreenwatermarkimage-f.md#cancelscreenwatermarkimage) | 取消屏幕水印 |
| [cancelWatermarkImage](arkts-mdm-securitymanager-cancelwatermarkimage-f.md#cancelwatermarkimage) | 取消指定用户的水印策略。 |
| [closeSession](arkts-mdm-securitymanager-closesession-f.md#closesession) | 关闭指定用户的凭据变更会话 |
| [getAllowedPermissionBundles](arkts-mdm-securitymanager-getallowedpermissionbundles-f.md#getallowedpermissionbundles) | 获取权限使用例外名单的应用列表。 |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getappclipboardpolicy) | 获取设备剪贴板策略。 |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getappclipboardpolicy-1) | 获取指定用户下指定应用的设备剪贴板策略。 |
| [getDeviceSecurityLevelPolicy](arkts-mdm-securitymanager-getdevicesecuritylevelpolicy-f.md#getdevicesecuritylevelpolicy) | 查询DSL切换策略 |
| [getDisallowedPermissions](arkts-mdm-securitymanager-getdisallowedpermissions-f.md#getdisallowedpermissions) | 获取指定用户下禁用的权限列表。 |
| [getExternalSourceExtensionsPolicy](arkts-mdm-securitymanager-getexternalsourceextensionspolicy-f.md#getexternalsourceextensionspolicy) | 获取外部来源扩展程序的管控策略。 |
| [getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f.md#getpasswordpolicy) | 获取设备锁屏口令策略。 |
| [getPermissionManagedState](arkts-mdm-securitymanager-getpermissionmanagedstate-f.md#getpermissionmanagedstate) | 获取指定应用的指定[user_grant权限](permissions:Permissions)的管理策略。 |
| [getSecurityStatus](arkts-mdm-securitymanager-getsecuritystatus-f.md#getsecuritystatus) | 获取当前设备安全策略信息。 |
| [getUnlockPolicy](arkts-mdm-securitymanager-getunlockpolicy-f.md#getunlockpolicy) | 查询解锁策略 |
| [getUserCertificates](arkts-mdm-securitymanager-getusercertificates-f.md#getusercertificates) | 获取指定系统账户下的用户证书信息。 |
| [getUserExtCredential](arkts-mdm-securitymanager-getuserextcredential-f.md#getuserextcredential) | 查询指定用户安装的扩展用户凭据 |
| [getWatermarkImageApps](arkts-mdm-securitymanager-getwatermarkimageapps-f.md#getwatermarkimageapps) | 查询设置了水印的应用列表 |
| [installEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md#installenterpriseresignaturecertificate) | 安装企业应用重签名证书。  同一用户下最多可下发10本不同证书。证书别名作为证书的唯一标识，不支持重复下发相同别名的证书。如需更新同一别名的证书，需先调用[uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md#uninstallenterpriseresignaturecertificate)进行卸载。  在MDM应用卸载或admin取消激活场景下，已安装的证书会保留在设备上，不会被移除。  在企业应用分发场景下，<!--RP2--><!--RP2End-->开发者可以使用重签名证书对企业应用进行二次签名，签名完成后将应用包提供给企业管理员。企业管理员可以将重签名后的应用安装在已部署重签名证书的企业设备上。  企业应用重签名证书使用流程：<!--RP3--><!--RP3End-->  1.通过MDM应用安装企业应用重签名证书；  2.开发者利用签名工具（如ohos-signer或DevEco Studio签名插件），对原始HAP包进行二次签名；  3.安装重签名应用（可以通过企业私有应用市场安装）；  4.运行应用。  规格约束：  1.安装新的签名证书之后，使用旧签名证书的应用可以继续运行；  2.已经安装的企业应用，安装了新的企业签名证书后，已安装的应用如需更新，可以直接覆盖安装，无需先卸载原应用；  3.企业场景下，特别是在涉及信息安全的场景中，企业需要确保员工使用的移动设备中仅安装并运行特定的内部软件和工具。企业应用重签名证书通过统一的应用身份标识，与系统的应用管理与权限控制机制配合使用，可支持企业应用的静默安装、受控的系统能力调用及运行范围限制，从而实现企业软件在受控终端上的准入控制与安全管理。 |
| [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installusercertificate) | 安装用户证书，使用Promise异步回调。 |
| [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installusercertificate-1) | 支持按系统账户安装用户证书。 |
| [isScreenLockDisabledForAccount](arkts-mdm-securitymanager-isscreenlockdisabledforaccount-f.md#isscreenlockdisabledforaccount) | 查询当前用户的滑动解锁能力是否被禁用。 |
| [openSession](arkts-mdm-securitymanager-opensession-f.md#opensession) | 开启指定用户的凭据变更会话 |
| [removeAllowedPermissionBundle](arkts-mdm-securitymanager-removeallowedpermissionbundle-f.md#removeallowedpermissionbundle) | 从权限使用例外名单中移除指定应用，移除后该应用则不能继续使用对应的权限。 |
| [removeUserExtCredential](arkts-mdm-securitymanager-removeuserextcredential-f.md#removeuserextcredential) | 移除扩展用户认证凭据 |
| [setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setappclipboardpolicy) | 设置设备剪贴板策略。 |
| [setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setappclipboardpolicy-1) | 设置指定用户下指定应用的设备剪贴板策略。 |
| [setDeviceSecurityLevelPolicy](arkts-mdm-securitymanager-setdevicesecuritylevelpolicy-f.md#setdevicesecuritylevelpolicy) | 设备DSL切换策略 |
| [setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md#setdisallowedpermission) | 禁用指定用户下的指定权限，禁用后指定用户下的所有应用申请和使用指定权限时默认拒绝。 |
| [setExternalSourceExtensionsPolicy](arkts-mdm-securitymanager-setexternalsourceextensionspolicy-f.md#setexternalsourceextensionspolicy) | 设置外部来源扩展程序的管控策略。  - DEFAULT：  默认，表示无管控策略，用户可以通过“设置-隐私与安全-高级”中的“运行外部来源的扩展程序”开关来设置是否允许扩展程序运行。  - DISALLOW：  禁用。设置此策略后，禁止运行外部来源的扩展程序，运行中的扩展程序可继续运行，扩展程序关闭后无法启动运行。用户无法开启“设置-隐私和安全-高级”中的“运行外部来源的扩展程序”开关。  - FORCE_OPEN：  强制开启。设置此策略后，允许运行外部来源的扩展程序，用户无法关闭“设置-隐私和安全-高级”中的“运行外部来源的扩展程序”开关。 |
| [setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md#setpasswordpolicy) | 设置设备锁屏口令策略。当用户设置锁屏口令时，如果设置的锁屏口令不符合要求，会有安全提示重新设置锁屏口令。 |
| [setPermissionManagedState](arkts-mdm-securitymanager-setpermissionmanagedstate-f.md#setpermissionmanagedstate) | 设置指定应用的[user_grant权限](permissions:Permissions)的管理策略。 |
| [setScreenLockDisabledForAccount](arkts-mdm-securitymanager-setscreenlockdisabledforaccount-f.md#setscreenlockdisabledforaccount) | 禁用/启用当前用户的滑动解锁能力。启用时：设备灭屏后再亮屏，用户需要在屏幕上滑动后才能进入桌面。禁用时：设备灭屏后再亮屏会直接进入桌面。 |
| [setScreenWatermarkImage](arkts-mdm-securitymanager-setscreenwatermarkimage-f.md#setscreenwatermarkimage) | 设置屏幕水印 |
| [setUnlockPolicy](arkts-mdm-securitymanager-setunlockpolicy-f.md#setunlockpolicy) | 设置解锁策略 |
| [setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setwatermarkimage) | 为指定用户的指定应用设置水印策略。当前只支持最多保存100个策略。 |
| [setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setwatermarkimage-1) | 为指定用户的指定应用设置水印策略。 |
| [uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md#uninstallenterpriseresignaturecertificate) | 卸载企业应用重签名证书。 |
| [uninstallUserCertificate](arkts-mdm-securitymanager-uninstallusercertificate-f.md#uninstallusercertificate) | 卸载用户证书，使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDeviceEncryptionStatus](arkts-mdm-securitymanager-getdeviceencryptionstatus-f-sys.md#getdeviceencryptionstatus) | 查询设备文件系统加密状态。 |
| [getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f-sys.md#getpasswordpolicy-1) | 获取设备锁屏口令策略。 |
| [getSecurityPatchTag](arkts-mdm-securitymanager-getsecuritypatchtag-f-sys.md#getsecuritypatchtag) | 查询设备安全补丁Tag。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AddCredentialInfo](arkts-mdm-securitymanager-addcredentialinfo-i.md) | 添加凭证信息 |
| [ApplicationInstance](arkts-mdm-securitymanager-applicationinstance-i.md) | 应用实例。 |
| [CertBlob](arkts-mdm-securitymanager-certblob-i.md) | 证书信息。 |
| [PasswordPolicy](arkts-mdm-securitymanager-passwordpolicy-i.md) | 设备锁屏口令策略。 |
| [WatermarkProperties](arkts-mdm-securitymanager-watermarkproperties-i.md) | 水印参数 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceEncryptionStatus](arkts-mdm-securitymanager-deviceencryptionstatus-i-sys.md) |  |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ClipboardPolicy](arkts-mdm-securitymanager-clipboardpolicy-e.md) | 设备剪贴板策略。 |
| [PermissionManagedState](arkts-mdm-securitymanager-permissionmanagedstate-e.md) | 应用权限的管理状态。 |

