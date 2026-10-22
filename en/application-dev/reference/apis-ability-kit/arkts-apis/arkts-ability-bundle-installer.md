# @ohos.bundle.installer(installer Module)

The module provides APIs for you to install, uninstall, and recover bundles on devices.

> **NOTE:** 
> 
> The APIs of this module are system APIs.

**Since:** 9

<!--Device-unnamed-declare namespace installer--><!--Device-unnamed-declare namespace installer-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getBundleInstaller](arkts-ability-installer-getbundleinstaller-f-sys.md#getbundleinstaller-1) | Obtains a BundleInstaller object. This API uses an asynchronous callback to return the result. |
| [getBundleInstaller](arkts-ability-installer-getbundleinstaller-f-sys.md#getbundleinstaller-2) | Obtains a BundleInstaller object. This API uses a promise to return the result. |
| [getBundleInstallerSync](arkts-ability-installer-getbundleinstallersync-f-sys.md#getbundleinstallersync-1) | Obtains and returns a BundleInstaller object. The API may return null when the call fails, so verify the return value before use. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BundleInstaller](arkts-ability-installer-bundleinstaller-i-sys.md) | Bundle installer interface, include install uninstall recover. |
| [CreateAppCloneParam](arkts-ability-installer-createappcloneparam-i-sys.md) | Describes the parameters used for creating an application clone. |
| [DestroyAppCloneParam](arkts-ability-installer-destroyappcloneparam-i-sys.md) | Describes the parameters used for destroying an application clone. |
| [HashParam](arkts-ability-installer-hashparam-i-sys.md) | Defines the hash parameters for bundle installation and uninstall. |
| [InstallParam](arkts-ability-installer-installparam-i-sys.md) | Defines the parameters that need to be specified for bundle installation, uninstall, or recovering. |
| [Parameters](arkts-ability-installer-parameters-i-sys.md) | Describes the extended parameter information. |
| [PGOParam](arkts-ability-installer-pgoparam-i-sys.md) | Defines the parameters of the PGO configuration file. |
| [PluginParam](arkts-ability-installer-pluginparam-i-sys.md) | Defines the parameters for installing or uninstalling a plugin. |
| [UninstallParam](arkts-ability-installer-uninstallparam-i-sys.md) | Defines the parameters required for the uninstall of a shared bundle. |
| [VerifyCodeParam](arkts-ability-installer-verifycodeparam-i-sys.md) | > Starting from API version 11, the code signature file of an application is integrated into the installation > package, rather than being specified by using this field. > Defines the information about the code signature file. |
<!--DelEnd-->
