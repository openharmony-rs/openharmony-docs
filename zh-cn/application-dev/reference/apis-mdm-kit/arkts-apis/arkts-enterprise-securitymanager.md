# @ohos.enterprise.securityManager(安全管理)

本模块提供企业设备安全管理能力，支持证书管理、设备安全策略管理、口令策略管理、剪贴板策略管理、水印策略管理、权限管理等功能。企业可使用本模块实现设备安全状态的实时监控、企业证书的生命周期管理、设备口令策略的统一配置、应用剪贴板使用行为 的管控、屏幕和应用水印的设置以防止信息泄露、以及应用权限的精细化管理等场景，帮助企业提升设备安全防护能力，降低数据泄露风险。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace securityManager--><!--Device-unnamed-declare namespace securityManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedPermissionBundle(安全管理)](arkts-mdm-securitymanager-addallowedpermissionbundle-f.md) | 将应用添加至权限使用例外名单，例外名单中的应用不受[setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md)设置的权限禁用策略限制。适用于企业应 用场景，如相机权限被禁用时，允许考勤应用、协作办公应用继续使用相机功能，保障企业关键业务正常运行。 |
| [cancelScreenWatermarkImage(安全管理)](arkts-mdm-securitymanager-cancelscreenwatermarkimage-f.md) | 取消屏幕水印策略，对所有用户生效。取消成功后，设备屏幕上的水印消失。当设备不再需要屏幕水印保护时，企业可调用此接口取消水印策略。只有设置屏幕水印的用户才能取消该水印，例如用户100设置的屏幕水印，用户101无法取消。 |
| [cancelWatermarkImage(安全管理)](arkts-mdm-securitymanager-cancelwatermarkimage-f.md) | 取消指定用户的水印策略。当应用不再需要水印保护或需要更换水印时，企业可调用此接口取消水印策略。 |
| [getAllowedPermissionBundles(安全管理)](arkts-mdm-securitymanager-getallowedpermissionbundles-f.md) | 获取权限使用例外名单的应用列表。 |
| [getAppClipboardPolicy(安全管理)](arkts-mdm-securitymanager-getappclipboardpolicy-f.md) | 获取设备剪贴板策略。企业可通过此接口查询当前配置的剪贴板策略，用于策略审计和合规性检查，确保剪贴板管控策略符合企业安全要求。 |
| [getAppClipboardPolicy(安全管理)](arkts-mdm-securitymanager-getappclipboardpolicy-f.md) | 获取设备剪贴板策略。企业可通过此接口查询当前配置的剪贴板策略，用于策略审计和合规性检查，确保剪贴板管控策略符合企业安全要求。 |
| [getAppClipboardPolicy(安全管理)](arkts-mdm-securitymanager-getappclipboardpolicy-f.md) | 获取指定用户下指定应用的设备剪贴板策略。企业可通过此接口查询特定应用的剪贴板使用权限配置，用于策略审计和合规性检查。 |
| [getAppClipboardPolicy(安全管理)](arkts-mdm-securitymanager-getappclipboardpolicy-f.md) | 获取指定用户下指定应用的设备剪贴板策略。企业可通过此接口查询特定应用的剪贴板使用权限配置，用于策略审计和合规性检查。 |
| [getDisallowedPermissions(安全管理)](arkts-mdm-securitymanager-getdisallowedpermissions-f.md) | 获取指定用户下禁用的权限列表。 |
| [getExternalSourceExtensionsPolicy(安全管理)](arkts-mdm-securitymanager-getexternalsourceextensionspolicy-f.md) | 获取外部来源扩展程序的管控策略。 |
| [getExternalSourceExtensionsPolicy(安全管理)](arkts-mdm-securitymanager-getexternalsourceextensionspolicy-f.md) | 获取外部来源扩展程序的管控策略。 |
| [getPasswordPolicy(安全管理)](arkts-mdm-securitymanager-getpasswordpolicy-f.md) | 获取设备锁屏口令策略。企业可通过此接口查询当前配置的口令策略，用于策略审计、合规性检查等场景，确保设备口令策略符合企业安全规范。 |
| [getPasswordPolicy(安全管理)](arkts-mdm-securitymanager-getpasswordpolicy-f.md) | 获取设备锁屏口令策略。企业可通过此接口查询当前配置的口令策略，用于策略审计、合规性检查等场景，确保设备口令策略符合企业安全规范。 |
| [getPermissionManagedState(安全管理)](arkts-mdm-securitymanager-getpermissionmanagedstate-f.md) | 获取指定应用的指定user_grant权限的管理策略。 |
| [getSecurityStatus(安全管理)](arkts-mdm-securitymanager-getsecuritystatus-f.md) | 获取当前设备安全策略信息。适用于设备合规性检查、安全状态审计、策略执行效果验证等场景，帮助企业管理员确认设备是否符合安全要求。企业可通过此接口实时监控设备的安全补丁状态和文件加密状态，及时发现设备安全风险并采取相应措施，保障企业设 备和数据安全。 |
| [getUserCertificates(安全管理)](arkts-mdm-securitymanager-getusercertificates-f.md) | 获取指定系统账户下的用户证书信息。企业可通过此接口查询设备上已安装的用户证书列表，用于证书审计、证书有效期管理等场景，确保证书管理的可追溯性。 |
| [getWatermarkImageApps(安全管理)](arkts-mdm-securitymanager-getwatermarkimageapps-f.md) | 获取指定用户下已设置水印的应用程序包名列表。 |
| [installEnterpriseReSignatureCertificate(安全管理)](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md) | 安装企业应用重签名证书。安装成功后，企业可使用该证书对应用进行重签名。 同一用户下最多可下发10本不同证书。证书别名作为证书的唯一标识，不支持重复下发相同别名的证书。如需更新同一别名的证书，需先调用 [uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md)进行卸载。 在MDM应用卸载或admin取消激活场景下，已安装的证书会保留在设备上，不会被移除。 在企业应用分发场景下，开发者可以使用重签名证书对企业应用进行二次签名，签名完成后将应用包提供给企业管理员。企业管理员可以将重签名后的应用安装在已部署重签名证书的企业设备上。 企业应用重签名证书使用流程： 1.通过MDM应用安装企业应用重签名证书； 2.开发者利用签名工具（如ohos-signer或DevEco Studio签名插件），对原始HAP包进行二次签名； 3.安装重签名应用（可以通过企业私有应用市场安装）； 4.运行应用。 规格约束： 1.安装新的签名证书之后，使用旧签名证书的应用可以继续运行； 2.已经安装的企业应用，安装了新的企业签名证书后，已安装的应用如需更新，可以直接覆盖安装，无需先卸载原应用； 3.企业场景下，特别是在涉及信息安全的场景中，企业需要确保员工使用的移动设备中仅安装并运行特定的内部软件和工具。企业应用重签名证书通过统一的应用身份标识，与系统的应用管理与权限控制机制配合使用，可支持企业应用的静默安装、受控的系统 能力调用及运行范围限制，从而实现企业软件在受控终端上的准入控制与安全管理。 |
| [installUserCertificate(安全管理)](arkts-mdm-securitymanager-installusercertificate-f.md) | 安装用户证书，使用Promise异步回调。企业可通过此接口将证书安装到设备上，用于企业VPN连接、安全认证、数字签名等场景，实现企业级的安全通信和数据保护。 |
| [installUserCertificate(安全管理)](arkts-mdm-securitymanager-installusercertificate-f.md) | 支持按系统账户安装用户证书。企业可为不同用户账户安装独立的证书，实现多用户环境下的安全隔离和个性化证书管理，满足多用户设备的安全管控需求。 |
| [isScreenLockDisabledForAccount(安全管理)](arkts-mdm-securitymanager-isscreenlockdisabledforaccount-f.md) | 查询当前用户的滑动解锁能力是否被禁用。 |
| [removeAllowedPermissionBundle(安全管理)](arkts-mdm-securitymanager-removeallowedpermissionbundle-f.md) | 从权限使用例外名单中移除指定应用，移除后该应用不能继续使用对应的权限。 |
| [setAppClipboardPolicy(安全管理)](arkts-mdm-securitymanager-setappclipboardpolicy-f.md) | 设置设备剪贴板策略。策略设置后，应用将按照设置的策略限制剪贴板的使用范围。适用于企业数据防泄露场景，如限制敏感应用（如企业邮箱、财务系统）的剪贴板使用范围，防止敏感数据被复制到非授权应用，降低数据泄露风险。企业可通过此接口控制应用 的剪贴板使用权限，防止敏感数据通过剪贴板泄露到未授权应用，增强企业数据安全防护能力。 |
| [setAppClipboardPolicy(安全管理)](arkts-mdm-securitymanager-setappclipboardpolicy-f.md) | 设置指定用户下指定应用的设备剪贴板策略。策略设置后，指定应用的剪贴板将按照策略限制使用范围。企业可为不同用户的不同应用配置差异化的剪贴板使用权限，实现精细化的数据访问控制，满足多用户多应用场景下的安全管控需求。 |
| [setDisallowedPermission(安全管理)](arkts-mdm-securitymanager-setdisallowedpermission-f.md) | 禁用指定用户下的指定权限，禁用后指定用户下的所有应用申请和使用指定权限时默认拒绝。适用于企业安全合规场景，如禁用相机、麦克风等高风险权限防止隐私泄露，或禁用特定功能（如蓝牙分享）防止企业数据外传。 |
| [setExternalSourceExtensionsPolicy(安全管理)](arkts-mdm-securitymanager-setexternalsourceextensionspolicy-f.md) | 设置外部来源扩展程序的管控策略。策略设置后，系统将按照设置的策略控制外部来源扩展程序的运行行为。适用于企业安全管控场景，如防止员工安装非授权浏览器扩展程序，或强制开启企业批准的扩展程序功能，保障企业终端安全。 - DEFAULT： 默认，表示无管控策略，用户可以通过“设置-隐私与安全-高级”中的“运行外部来源的扩展程序”开关来设置是否允许扩展程序运行。 - DISALLOW： 禁用。设置此策略后，禁止运行外部来源的扩展程序，运行中的扩展程序可继续运行，扩展程序关闭后无法启动运行。用户无法开启“设置-隐私和安全-高级”中的“运行外部来源的扩展程序”开关。 - FORCE_OPEN： 强制开启。设置此策略后，允许运行外部来源的扩展程序，用户无法关闭“设置-隐私和安全-高级”中的“运行外部来源的扩展程序”开关。 |
| [setPasswordPolicy(安全管理)](arkts-mdm-securitymanager-setpasswordpolicy-f.md) | 设置设备锁屏口令策略。策略设置后，当用户设置锁屏口令时，如果设置的锁屏口令不符合要求，会有安全提示重新设置锁屏口令。适用于企业安全合规场景，如强制要求员工使用强密码、定期更换密码等，降低企业数据泄露风险。 |
| [setPermissionManagedState(安全管理)](arkts-mdm-securitymanager-setpermissionmanagedstate-f.md) | 设置指定应用的user_grant权限的管理策略。适用于企业应用批量部署场景，如静默授权减少权限弹窗干扰、统一企业应用权限管理策略，提升员工使用体验和管理效率。 |
| [setScreenLockDisabledForAccount(安全管理)](arkts-mdm-securitymanager-setscreenlockdisabledforaccount-f.md) | 禁用/启用当前用户的滑动解锁能力。启用时：设备灭屏后再亮屏，用户需要在屏幕上滑动后才能进入桌面。禁用时：设备灭屏后再亮屏会直接进入桌面。适用于企业设备管理场景，如在特定安全环境下禁用滑动解锁简化操作，或在通用场景下启用滑动解锁作为 基础安全措施。 |
| [setScreenWatermarkImage(安全管理)](arkts-mdm-securitymanager-setscreenwatermarkimage-f.md) | 设置屏幕水印策略，对所有用户生效。 |
| [setWatermarkImage(安全管理)](arkts-mdm-securitymanager-setwatermarkimage-f.md) | 为指定用户的指定应用设置水印策略。当前只支持最多保存100个策略。 |
| [setWatermarkImage(安全管理)](arkts-mdm-securitymanager-setwatermarkimage-f.md) | 为指定用户的指定应用设置水印策略。当前只支持最多保存100个策略。 |
| [uninstallEnterpriseReSignatureCertificate(安全管理)](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md) | 卸载企业应用重签名证书。卸载企业重签名证书后，使用该证书签名的应用在设备重启前正常运行，设备重启后无法运行。 使用场景： 1.安装新证书：调用[installEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md)接 口安装新证书后，经新证书重签名的应用可正常运行。如果旧签名证书对应的应用为超级设备管理应用，需先取消激活后才能卸载证书，否则卸载证书后该应用无法卸载且无法运行。 2.恢复误删证书：调用[installEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md) 接口重新安装误删除的证书后，已重签名的应用可正常运行，不受影响。 > **注意：** > > 删除证书常见证书过期和证书泄露场景，建议开发者在实现该功能时，强提示管理员谨慎删除证书，并确保删除证书前加载新的重签名证书，并完成所有应用更新切换到新的重签名证书，否则重启后历史安装的应用将无法运行。 |
| [uninstallUserCertificate(安全管理)](arkts-mdm-securitymanager-uninstallusercertificate-f.md) | 卸载用户证书，使用Promise异步回调。适用于企业证书管理场景，如证书过期更换、撤销员工对企业资源的访问权限等。企业可在证书过期、更换或不再需要时调用此接口卸载证书，确保设备证书管理的灵活性和安全性。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDeviceEncryptionStatus(安全管理)](arkts-mdm-securitymanager-getdeviceencryptionstatus-f-sys.md) | 查询设备文件系统加密状态。 |
| [getPasswordPolicy(安全管理)](arkts-mdm-securitymanager-getpasswordpolicy-f-sys.md) | 获取设备锁屏口令策略。 |
| [getSecurityPatchTag(安全管理)](arkts-mdm-securitymanager-getsecuritypatchtag-f-sys.md) | 查询设备安全补丁Tag。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApplicationInstance(安全管理)](arkts-mdm-securitymanager-applicationinstance-i.md) | 应用实例。 |
| [CertBlob(安全管理)](arkts-mdm-securitymanager-certblob-i.md) | 证书信息。 |
| [PasswordPolicy(安全管理)](arkts-mdm-securitymanager-passwordpolicy-i.md) | 设备锁屏口令策略。 |
| [WatermarkProperties(安全管理)](arkts-mdm-securitymanager-watermarkproperties-i.md) | 水印属性。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceEncryptionStatus(安全管理)](arkts-mdm-securitymanager-deviceencryptionstatus-i-sys.md) | 设备管理应用的文件系统加密状态。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ClipboardPolicy(安全管理)](arkts-mdm-securitymanager-clipboardpolicy-e.md) | 设备剪贴板策略。 |
| [PasswordAlgs(安全管理)](arkts-mdm-securitymanager-passwordalgs-e.md) | 处理口令数据使用的加密算法。 |
| [PermissionManagedState(安全管理)](arkts-mdm-securitymanager-permissionmanagedstate-e.md) | 应用权限的管理状态。 |

