# @ohos.enterprise.bundleManager(Bundle Management)

This module provides package management capabilities, including installing and uninstalling application packages, and managing the installation trustlist, installation blocklist, uninstallation blocklist, and distribution types of installable applications. In enterprise device management scenarios, these capabilities enable fine-grained control over application installation and uninstallation, preventing unauthorized installations and uninstallations, thereby safeguarding enterprise device security and reducing security risks.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addAllowedInstallBundlesSync](arkts-mdm-bundlemanager-addallowedinstallbundlessync-f.md) | Adds the applications that can be installed by the current or specified user. The reinstallation of system apps after uninstallation is not restricted by the API. However, the reinstallation of regular apps after uninstallation is restricted by the API. |
| [addDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-adddisallowedinstallbundlessync-f.md) | Adds the applications that are not allowed to be installed by the current or specified user. The reinstallation of system apps after uninstallation is not restricted by the API. However, the reinstallation of regular apps after uninstallation is restricted by the API. |
| [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md) | Adds the applications that are not allowed to be uninstalled by the current or specified user. |
| [addInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-addinstallationallowedappdistributiontypes-f.md) | Adds the distribution type of the application that can be installed. Only applications of the distribution type that is added to [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md) can be installed on the current device. |
| [getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md) | Obtains the applications that can be installed by the current or specified user. |
| [getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md) | Obtains the applications that can be installed by the current or specified user. |
| [getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md) | Obtains the applications that cannot be installed by the current or specified user. |
| [getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md) | Obtains the applications that cannot be installed by the current or specified user. |
| [getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md) | Obtains the bundles that cannot be uninstalled by the current or specified user. |
| [getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md) | Obtains the bundles that are not allowed to be uninstalled by the current or specified user. |
| [getInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-getinstallationallowedappdistributiontypes-f.md) | Obtains the distribution type of the signing certificate used by applications that can be installed. |
| [getInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-getinstallationallowedappdistributiontypes-f.md) | Obtains the distribution type of the signing certificate used by applications that can be installed. |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md) | Obtains the applications installed by a specified user on a device. This API uses a promise to return the result. |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md) | Obtains the list of applications installed by a specified user based on the specified **bundleInfoGetFlag**. This API uses a promise to return the result. |
| [getInstalledBundleStorageStats](arkts-mdm-bundlemanager-getinstalledbundlestoragestats-f.md) | Obtains the storage usage of installed applications of a specified user on a device. This API uses a promise to return the result. |
| [install](arkts-mdm-bundlemanager-install-f.md) | Installs specified applications. This API uses a promise to return the result. |
| [installForResult](arkts-mdm-bundlemanager-installforresult-f.md) | Installs the application bundle in the specified path and returns the installation result. This API uses a promise to return the result. |
| [installMarketApps](arkts-mdm-bundlemanager-installmarketapps-f.md) | Downloads and installs an application from AppGallery. |
| [removeAllowedInstallBundlesSync](arkts-mdm-bundlemanager-removeallowedinstallbundlessync-f.md) | Removes the applications that can be installed by the current or specified user. |
| [removeDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-removedisallowedinstallbundlessync-f.md) | Removes the applications that cannot be installed by the current or specified user. |
| [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md) | Removes the applications that cannot be uninstalled by the current or specified user through the specified device administrator application. |
| [removeInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-removeinstallationallowedappdistributiontypes-f.md) | Removes the distribution type of an application. If only some distribution types in the array are removed, the current device can install applications of the remaining distribution types in the array, but cannot install applications of the distribution types not included in [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md). |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f.md) | Uninstalls a specified bundle of the current or specified user. The **isKeepData** parameter specifies whether to retain the bundle data. This API uses a promise to return the result. After the API is successfully called, the application is uninstalled, and the data is retained or deleted based on the **isKeepData** parameter. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md) | Adds the applications that can be installed by the current user. This API uses an asynchronous callback to return the result. |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md) | Adds the applications that can be installed by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md) | Adds the applications that can be installed by the current or specified user. This API uses a promise to return the result. |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md) | Adds the applications that cannot be installed by the current user. This API uses an asynchronous callback to return the result. |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md) | Adds the applications that cannot be installed by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md) | Adds the applications that are not allowed to be installed by the current or specified user. This API uses a promise to return the result. |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md) | Adds the applications that cannot be uninstalled by the current user. This API uses an asynchronous callback to return the result. |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md) | Adds the applications that cannot be uninstalled by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md) | Adds the applications that cannot be uninstalled by the current or specified user. This API uses a promise to return the result. |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md) | Obtains the applications that can be installed by the current user. This API uses an asynchronous callback to return the result. |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md) | Obtains the applications that can be installed by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md) | Obtains the list of applications that are allowed to be installed by the current or specified user. This API uses a promise to return the result. |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md) | Obtains the applications that cannot be installed by the current user. This API uses an asynchronous callback to return the result. |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md) | Obtains the applications that cannot be installed by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md) | Obtains the list of applications that are not allowed to be installed by the current or specified user. This API uses a promise to return the result. |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md) | Obtains the applications that cannot be uninstalled by the current user. This API uses an asynchronous callback to return the result. |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md) | Obtains the applications that cannot be uninstalled by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md) | Obtains the list of applications that are not allowed to be uninstalled by the current or specified user. This API uses a promise to return the result. |
| [install](arkts-mdm-bundlemanager-install-f-sys.md) | Installs specified applications. This API uses an asynchronous callback to return the result. |
| [install](arkts-mdm-bundlemanager-install-f-sys.md) | Installs applications with specified parameters. This API uses an asynchronous callback to return the result. |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md) | Removes the applications that can be installed by the current user. This API uses an asynchronous callback to return the result. |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md) | Removes the applications that can be installed by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md) | Removes the applications that can be installed by the current or specified user. This API uses a promise to return the result. |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md) | Removes the applications that cannot be installed by the current user. This API uses an asynchronous callback to return the result. |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md) | Removes the applications that cannot be installed by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md) | Removes the applications that cannot be installed by the current or specified user. This API uses a promise to return the result. |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md) | Removes the applications that cannot be uninstalled by the current user. This API uses an asynchronous callback to return the result. |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md) | Removes the applications that cannot be uninstalled by the user specified by **userId**. This API uses an asynchronous callback to return the result. |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md) | Removes the applications that cannot be uninstalled by the current or specified user. This API uses a promise to return the result. |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | Uninstalls an application of the current user without retaining the bundle data. This API uses an asynchronous callback to return the result. |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | Uninstalls an application of the specified user without retaining the bundle data This API uses an asynchronous callback to return the result. |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | Uninstalls an application of the current user. The **isKeepData** parameter specifies whether to retain the bundle data. This API uses an asynchronous callback to return the result. |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | Uninstalls an application of the specified user. The **isKeepData** parameter specifies whether to retain the bundle data. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ApplicationInfo](arkts-mdm-bundlemanager-applicationinfo-i.md) | Defines the application information. |
| [BundleInfo](arkts-mdm-bundlemanager-bundleinfo-i.md) | Describes the application bundle information. |
| [BundleStorageStats](arkts-mdm-bundlemanager-bundlestoragestats-i.md) | Storage usage information of the application. |
| [InstallParam](arkts-mdm-bundlemanager-installparam-i.md) | Defines the parameters for application installation. |
| [Resource](arkts-mdm-bundlemanager-resource-i.md) | Describes application resource information, including the bundle name, module name, and resource ID. |
| [SignatureInfo](arkts-mdm-bundlemanager-signatureinfo-i.md) | Describes the signature information of the bundle. |

### Enums

| Name | Description |
| --- | --- |
| [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md) | Defines the distribution type of the application signing certificate. For details, please refer to the **appDistributionType** attribute of [ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md). |
| [BundleInfoGetFlag](arkts-mdm-bundlemanager-bundleinfogetflag-e.md) | Enumerates the bundle flags, which indicate the type of bundle information to obtain. |
