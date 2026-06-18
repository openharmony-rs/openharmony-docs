# EnterpriseAdminExtensionAbility Development Guide
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a1815a6960f035b2f960cbb3747e78fb7c1af4a8 translatedAt=2026-06-15T08:10:56.167Z pushedAt=2026-06-16T14:10:17.394Z -->

## Overview

The enterprise device management extension ability component is a required component for device management apps. When developing a device management app for enterprises, developers need to inherit EnterpriseAdminExtensionAbility and implement MDM business logic in the EnterpriseAdminExtensionAbility instance. EnterpriseAdminExtensionAbility implements the system management status change notification function and defines callback interfaces for management app activation, deactivation, app installation, and uninstallation events.

## Available APIs
The following are the interfaces used in this development example. For more interfaces and usage, see [Enterprise Device Management Extension Ability Interface Documentation](../../application-dev/reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md).

| Interface Name                                  | Description                         |
| ----------------------------------------- | ---------------------------- |
| [onAdminEnabled(): void](../../application-dev/reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md#onadminenabled)                    | Callback method invoked when the device management app is activated.   |
| [onAdminDisabled(): void](../../application-dev/reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md#onadmindisabled)                   | Callback method invoked when the device management app is deactivated. |
| [onBundleAdded(bundleName: string): void](../../application-dev/reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md#onbundleadded)   | Callback method invoked when an app is installed.             |
| [onBundleRemoved(bundleName: string): void](../../application-dev/reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md#onbundleremoved) | Callback method invoked when an app is uninstalled.             |
| [onDeviceAdminEnabled(bundleName: string): void](../../application-dev/reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md#ondeviceadminenabled23) | Callback method invoked when a normal device management app is activated. |
| [onDeviceAdminDisabled(bundleName: string): void](../../application-dev/reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md#ondeviceadmindisabled23) | Callback method invoked when a normal device management app is deactivated. |

## How to Develop

After creating a project, the structure is as follows:

![guide_struct_init.png](./figures/guide_struct_init.png)

First, create an EnterpriseAdmin-type ExtensionAbility (that is, EnterpriseAdminExtensionAbility).

![guide_struct_done.png](./figures/guide_struct_done.png)

Next, open the newly created EnterpriseAdminAbility file, import the EnterpriseAdminExtensionAbility module, make it inherit EnterpriseAdminExtensionAbility, and add the required app notification callback methods, such as onAdminEnabled() and onAdminDisabled(). When the device management app is activated or deactivated, the system-sent notifications can be received in the corresponding callback methods.

<!-- @[enterprise_admin_extension_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/EnterpriseAdminExtensionAbility/EnterpriseAdminExtensionAbility/entry/src/main/ets/enterpriseadminability/EnterpriseAdminAbility.ets) -->

``` TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';
// ···

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
// ···

  // Callback method for device manager app activation. The app can perform initialization policy settings in this callback.
  onAdminEnabled() {
    console.info('onAdminEnabled');
    // ···
  }

  // Callback method for device manager application deactivation. The application can use this callback to notify the enterprise administrator that the device has been unmanaged.
  onAdminDisabled() {
    console.info('onAdminDisabled');
    // ···
  }

  // Callback method for application installation. The application can use this callback to report events and notify the enterprise administrator.
  onBundleAdded(bundleName: string) {
    console.info('EnterpriseAdminAbility onBundleAdded bundleName:' + bundleName);
  }

  // Callback method for application uninstallation. The application can use this callback to report events and notify the enterprise administrator.
  onBundleRemoved(bundleName: string) {
    console.info('EnterpriseAdminAbility onBundleRemoved bundleName' + bundleName);
  }

  // Callback method for standard device management application activation. The application can use this callback to perform initialization policy settings.
  onDeviceAdminEnabled(bundleName: string) {
    console.info("EnterpriseAdminAbility onDeviceAdminEnabled bundleName:" + bundleName);
  }

  // Callback method for standard device management application deactivation. The application can use this callback to notify the enterprise administrator that the device has been unmanaged.
  onDeviceAdminDisabled(bundleName: string) {
    console.info("EnterpriseAdminAbility onDeviceAdminDisabled bundleName" + bundleName);
  }
};
```


Finally, register EnterpriseAdminAbility as an ExtensionAbility in the [module.json5](../quick-start/module-configuration-file.md) configuration file of the project module. The type tag must be set to "enterpriseAdmin", and the srcEntry tag indicates the code path corresponding to the current ExtensionAbility component.

<!-- @[extension_abilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/EnterpriseAdminExtensionAbility/EnterpriseAdminExtensionAbility/entry/src/main/module.json5) -->

``` JSON5
"extensionAbilities": [
  {
    "name": "EnterpriseAdminAbility",
    "type": "enterpriseAdmin",
    "exported": true,
    "srcEntry": "./ets/enterpriseadminability/EnterpriseAdminAbility.ets"
  }
],
```


## Samples

For EnterpriseAdminExtensionAbility development, the following related samples are available for reference:

- [Enterprise Device Management Extension (ArkTS)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/EnterpriseAdminExtensionAbility/EnterpriseAdminExtensionAbility)