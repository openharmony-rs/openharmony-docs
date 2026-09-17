# installForResult

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## installForResult

```TypeScript
function installForResult(admin: Want, hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

Installs the application bundle in the specified path and returns the installation result. This API uses a promise to return the result.

This API can be used to install only applications of the **enterprise_mdm** (MDM application) or **enterprise_normal** (common enterprise application) distribution type. You can call the [getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md) API to query the BundleInfo of an application, where **BundleInfo.appInfo.appDistributionType** indicates the distribution type.

> **NOTE:** 
> 
> This API is time-consuming. Subsequent calls to other synchronous APIs in the application main thread must wait
> for the asynchronous return of this API.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| hapFilePaths | Array&lt;string&gt; | Yes | Applications to install. The app bundle must be stored in the path that the app has the permission to access, such as the app sandbox path. For details about the mapping between the app sandbox path and the actual physical path, see [Mappings Between App Sandbox Paths and Physical Paths](../../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths). |
| installParam | [InstallParam](arkts-mdm-bundlemanager-installparam-i.md) | No | Application installation parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. If the operation fails, an error object will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9201002](../errorcode-enterpriseDeviceManager.md#9201002-failed-to-install-the-enterprise-application) | Failed to install the application. |
| [9201022](../errorcode-enterpriseDeviceManager.md#9201022-application-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the HAP because of insufficient system disk space. |
| [9201023](../errorcode-enterpriseDeviceManager.md#9201023-application-installation-failure-due-to-prohibition-by-enterprise-device-management) | Failed to install the HAP because enterprise device management disallows the installation. |
| [9201024](../errorcode-enterpriseDeviceManager.md#9201024-application-installation-failed-due-to-hap-parsing-failure) | Failed to install the HAP because the HAP fails to be parsed. |
| [9201025](../errorcode-enterpriseDeviceManager.md#9201025-application-installation-failed-due-to-hap-signature-verification-failure) | Failed to install the HAP because the HAP signature fails to be verified. |
| [9201026](../errorcode-enterpriseDeviceManager.md#9201026-application-installation-failed-due-to-an-invalid-hap-path-or-an-extra-large-hap) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [9201027](../errorcode-enterpriseDeviceManager.md#9201027-installation-failed-due-to-inconsistent-hap-configuration-information) | Failed to install the HAPs because they have different configuration information. |
| [9201028](../errorcode-enterpriseDeviceManager.md#9201028-application-installation-failed-due-to-unsupported-isolationmode-configuration) | Failed to install the HAP because the isolationMode configured is not supported. |
| [9201029](../errorcode-enterpriseDeviceManager.md#9201029-application-installation-failed-due-to-outdated-hap-version) | Failed to install the HAP since the version of the HAP to install is too early. |
| [9201030](../errorcode-enterpriseDeviceManager.md#9201030-application-installation-failed-because-versioncode-is-not-greater-than-the-current-version) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [9201031](../errorcode-enterpriseDeviceManager.md#9201031-application-installation-failed-because-the-dependent-module-does-not-exist) | Installation failed because the dependent module does not exist. |
| [9201032](../errorcode-enterpriseDeviceManager.md#9201032-specified-user-does-not-exist) | The specified user ID is not found. |
| [9201033](../errorcode-enterpriseDeviceManager.md#9201033-application-installation-failed-due-to-overlay-check-failure) | Failed to install the HAP because the overlay check failed. |
| [9201034](../errorcode-enterpriseDeviceManager.md#9201034-application-installation-failed-due-to-lack-of-required-permissions-in-the-hsp) | Failed to install the HSP due to missing required permissions. |
| [9201035](../errorcode-enterpriseDeviceManager.md#9201035-application-installation-failed-because-cross-application-shared-library-installation-is-not-allowed) | Installation failed because the installation of cross-app shared libraries is not allowed. |
| [9201036](../errorcode-enterpriseDeviceManager.md#9201036-app-installation-failed-due-to-incorrect-data-proxy-uri) | Failed to install the HAP due to incorrect URI in the data proxy. |
| [9201037](../errorcode-enterpriseDeviceManager.md#9201037-app-installation-failed-due-to-incorrect-data-proxy-permission-configuration) | Failed to install the HAP due to incorrect permission configuration in the data proxy. |
| [9201038](../errorcode-enterpriseDeviceManager.md#9201038-application-installation-failed-due-to-code-signature-verification-failure) | Failed to install the HAP due to code signature verification failure. |
| [9201039](../errorcode-enterpriseDeviceManager.md#9201039-application-installation-failed-due-to-enterprise-device-verification-failure) | Failed to install the HAP due to enterprise device verification failure. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
