# BundleInstaller (System API)

```TypeScript
interface BundleInstaller
```

Bundle installer interface, include install uninstall recover.

**Since:** 9

<!--Device-installer-interface BundleInstaller--><!--Device-installer-interface BundleInstaller-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## addExtResource

```TypeScript
addExtResource(bundleName: string, filePaths: Array<string>): Promise<void>
```

Adds extended resources based on the specified bundle name and HSP file path. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-addExtResource(bundleName: string, filePaths: Array<string>): Promise<void>--><!--Device-BundleInstaller-addExtResource(bundleName: string, filePaths: Array<string>): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application to which extension resources are added. |
| filePaths | Array&lt;string&gt; | Yes | Path of the extended resources to be added. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700301](../errorcode-bundle.md#17700301-failed-to-add-extended-resources) | AddExtResource failed due to parse file failed. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName : string = 'com.ohos.demo';
let filePaths : Array<string> = ['/data/storage/el2/base/a.hsp'];
try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.addExtResource(bundleName, filePaths).then((data) => {
            console.info('addExtResource successfully');
        }).catch((err: BusinessError) => {
            console.error('addExtResource failed. Cause: ' + err.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## createAppClone

```TypeScript
createAppClone(bundleName: string, createAppCloneParam?: CreateAppCloneParam): Promise<number>
```

Creates an application clone. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INSTALL_CLONE_BUNDLE

<!--Device-BundleInstaller-createAppClone(bundleName: string, createAppCloneParam?: CreateAppCloneParam): Promise<int>--><!--Device-BundleInstaller-createAppClone(bundleName: string, createAppCloneParam?: CreateAppCloneParam): Promise<int>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application for which a clone is to be created. |
| createAppCloneParam | [CreateAppCloneParam](arkts-ability-installer-createappcloneparam-i-sys.md) | No | Specifies other parameters required for creating an app clone. Default value: refer to the default value of [CreateAppCloneParam](arkts-ability-installer-createappcloneparam-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the index of the application clone. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The userId is invalid. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | The appIndex is not in valid range or already exists. |
| [17700069](../errorcode-bundle.md#17700069-application-clone-is-not-supported) | The app does not support the creation of an appClone instance. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.camera';
let createAppCloneParam: installer.CreateAppCloneParam = {
    userId: 100,
    appIndex: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.createAppClone(bundleName, createAppCloneParam)
            .then(() => {
                console.info('createAppClone successfully.');
        }).catch((error: BusinessError) => {
            console.error('createAppClone failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## destroyAppClone

```TypeScript
destroyAppClone(bundleName: string, appIndex: number, userId?: number): Promise<void>
```

Destroys an app clone or a CLI sandbox app. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.UNINSTALL_CLONE_BUNDLE

<!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, userId?: number): Promise<void>--><!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, userId?: number): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the app clone or CLI sandbox app to be deleted. |
| appIndex | number | Yes | Index of the app clone or CLI sandbox app to be deleted. Value range: [1, 5] and [2000, 3000]. 1 to 5 indicates an app clone, and 2000 to 3000 indicates a CLI sandbox app. Since API version 26.0.0, the value range [2000, 3000] is supported. |
| userId | number | No | User ID to which the app clone or CLI sandbox app to be deleted belongs. It can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). Default value: the caller's user. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.UNINSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The userId is invalid. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.camera';
let index = 1;
let userId = 100;

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.destroyAppClone(bundleName, index, userId)
            .then(() => {
                console.info('destroyAppClone successfully.');
        }).catch((error: BusinessError) => {
            console.error('destroyAppClone failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## destroyAppClone

```TypeScript
destroyAppClone(bundleName: string, appIndex: number, destroyAppCloneParam?: DestroyAppCloneParam): Promise<void>
```

Destroys an app clone or a CLI sandbox app. This API uses a promise to return the result.

**Since:** 15

**Required permissions:** ohos.permission.UNINSTALL_CLONE_BUNDLE

<!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, destroyAppCloneParam?: DestroyAppCloneParam): Promise<void>--><!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, destroyAppCloneParam?: DestroyAppCloneParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the app clone or CLI sandbox app to be deleted. |
| appIndex | number | Yes | Index of the app clone or CLI sandbox app to be deleted. Value range: [1, 5] and [2000, 3000]. 1 to 5 indicates an app clone, and 2000 to 3000 indicates a CLI sandbox app. Since API version 26.0.0, the value range [2000, 3000] is supported. |
| destroyAppCloneParam | [DestroyAppCloneParam](arkts-ability-installer-destroyappcloneparam-i-sys.md) | No | Other parameters required for deleting the app clone or CLI sandbox app. Default value: refer to the default value of [DestroyAppCloneParam](arkts-ability-installer-destroyappcloneparam-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.UNINSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The userId is invalid. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range. |
| [17700062](../errorcode-bundle.md#17700062-failed-to-uninstall-an-application-configured-with-an-uninstallation-disposed-rule) | Failed to uninstall the app because the app is locked. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.camera';
let index = 1;
let userId = 100;
let key = 'ohos.bms.param.verifyUninstallRule';
let value = 'false';
let item: installer.Parameters = {key, value};
let destroyAppCloneOpt: installer.DestroyAppCloneParam = {
    userId: userId,
    parameters: [item]
};


try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.destroyAppClone(bundleName, index, destroyAppCloneOpt)
            .then(() => {
                console.info('destroyAppClone successfully.');
        }).catch((error: BusinessError) => {
            console.error('destroyAppClone failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## install

```TypeScript
install(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void
```

Installs a specified app. This API uses an asynchronous callback to return the result. Since API version 26.0.0, installing an APP package is supported.

> **NOTE:** 
> 
> To install apps of different distribution types, you need to apply for the corresponding permissions. For
> details about the distribution types, see the description of the appDistributionType field in
> [ApplicationInfo](arkts-ability-applicationinfo-i.md).

**Since:** 9

**Required permissions:** 
- API version 26 and later: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE) or ohos.permission.INSTALL_DEVELOPER_ID_BUNDLE
- API version 23 and later: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)
- API versions 13 to 22: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE
- API versions 10 to 12: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE
- API version 9: ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | Yes | Path for storing the application package. The path should be the data directory where the HAP or APP of the current app is stored. When the path is a directory, the directory can contain only the HAPs of the same app or one APP. The signatures of the HAPs of the same app must be consistent. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | Yes | Parameters required for the installation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the app is installed successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE') or 'ohos.permission.INSTALL_DEVELOPER_ID_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature; 4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-bundle-installation-failure-because-the-dependent-module-does-not-exist) | Failed to install because the dependent module does not exist. |
| [17700031](../errorcode-bundle.md#17700031-hap-installation-fails-due-to-overlay-feature-verification-failure) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../errorcode-bundle.md#17700036-failure-in-installing-the-shared-library-because-of-no-allowappsharelibrary-privilege) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../errorcode-bundle.md#17700039-failure-in-installing-an-inter-application-shared-library) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-application-installation-is-not-allowed-by-enterprise-device-management) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-incorrect-uri-in-the-data-proxy) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-incorrect-permission-configuration-in-the-data-proxy) | Failed to install the HAP because of low APL in the non-system data proxy (required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-field-isolationmode-in-the-hap-conflicts-with-the-device-isolation-mode) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-application-version-to-be-updated-is-not-later-than-the-current-version) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the HAP because the code signature verification is failed.<br>**Applicable version:** 10 and later |
| [17700050](../errorcode-bundle.md#17700050-installation-of-enterprise-mdm-applications-and-standard-enterprise-applications-not-allowed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device.<br>**Applicable version:** 10 and later |
| [17700052](../errorcode-bundle.md#17700052-installing-a-debug-self-distributed-plugin-or-debug-application-is-not-allowed-in-non-developer-mode) | Failed to install the HAP because debug bundle cannot be installed under non -developer mode.<br>**Applicable version:** 11 and later |
| [17700054](../errorcode-bundle.md#17700054-bundle-installation-failure-due-to-permission-verification-failure) | Failed to install the HAP because the HAP requests wrong permissions.<br>**Applicable version:** 11 and later |
| [17700058](../errorcode-bundle.md#17700058-specified-application-cannot-be-installed-on-this-device-or-by-this-user) | Failed to install the HAP because the device has been controlled.<br>**Applicable version:** 12 and later |
| [17700066](../errorcode-bundle.md#17700066-failed-to-install-the-native-software-package) | Failed to install the HAP because installing the native package failed.<br>**Applicable version:** 12 and later |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the HAP because an application with the same <br>bundle name but different signature information exists on the device.<br>**Applicable version:** 13 and later |
| [17700077](../errorcode-bundle.md#17700077-application-installation-fails-but-preinstallation-is-successful) | Failed to install the HAP and restore to preinstalled bundle.<br>**Applicable version:** 17 and later |
| [17700076](../errorcode-bundle.md#17700076-application-installation-failure-due-to-unsupported-distribution-type-in-the-signing-certificate-profile) | Failed to install the HAP or HSP because the app distribution type is not allowed.<br>**Applicable version:** 18 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapFilePaths = ['/data/storage/el2/base/haps/entry/files/'];
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.install(hapFilePaths, installParam, (err: BusinessError) => {
            if (err) {
                console.error('install failed:' + err.message);
            } else {
                console.info('install successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## install

```TypeScript
install(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void
```

Installs a specified app. This API uses an asynchronous callback to return the result. Since API version 26.0.0, installing an APP package is supported.

> **NOTE:** 
> 
> To install apps of different distribution types, you need to apply for the corresponding permissions. For
> details about the distribution types, see the description of the appDistributionType field in
> [ApplicationInfo](arkts-ability-applicationinfo-i.md).

**Since:** 9

**Required permissions:** 
- API version 26 and later: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE) or ohos.permission.INSTALL_DEVELOPER_ID_BUNDLE
- API version 23 and later: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)
- API versions 13 to 22: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE
- API versions 10 to 12: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE
- API version 9: ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-install(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-install(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | Yes | Paths for storing the application packages. The path should be the data directory where the HAP or APP is stored in the current app. When the path passed in is a directory, the directory can contain only the HAPs of the same app or one APP. The signatures of the HAPs of the same app must be consistent. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the app is installed successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE') or 'ohos.permission.INSTALL_DEVELOPER_ID_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-bundle-installation-failure-because-the-dependent-module-does-not-exist) | Failed to install because the dependent module does not exist. |
| [17700031](../errorcode-bundle.md#17700031-hap-installation-fails-due-to-overlay-feature-verification-failure) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../errorcode-bundle.md#17700036-failure-in-installing-the-shared-library-because-of-no-allowappsharelibrary-privilege) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../errorcode-bundle.md#17700039-failure-in-installing-an-inter-application-shared-library) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-application-installation-is-not-allowed-by-enterprise-device-management) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-incorrect-uri-in-the-data-proxy) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-incorrect-permission-configuration-in-the-data-proxy) | Failed to install the HAP because of low APL in the non-system data proxy (required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-field-isolationmode-in-the-hap-conflicts-with-the-device-isolation-mode) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-application-version-to-be-updated-is-not-later-than-the-current-version) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the HAP because the code signature verification is failed.<br>**Applicable version:** 10 and later |
| [17700050](../errorcode-bundle.md#17700050-installation-of-enterprise-mdm-applications-and-standard-enterprise-applications-not-allowed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device.<br>**Applicable version:** 10 and later |
| [17700052](../errorcode-bundle.md#17700052-installing-a-debug-self-distributed-plugin-or-debug-application-is-not-allowed-in-non-developer-mode) | Failed to install the HAP because debug bundle cannot be installed under non -developer mode.<br>**Applicable version:** 11 and later |
| [17700054](../errorcode-bundle.md#17700054-bundle-installation-failure-due-to-permission-verification-failure) | Failed to install the HAP because the HAP requests wrong permissions.<br>**Applicable version:** 11 and later |
| [17700058](../errorcode-bundle.md#17700058-specified-application-cannot-be-installed-on-this-device-or-by-this-user) | Failed to install the HAP because the device has been controlled.<br>**Applicable version:** 12 and later |
| [17700066](../errorcode-bundle.md#17700066-failed-to-install-the-native-software-package) | Failed to install the HAP because installing the native package failed.<br>**Applicable version:** 12 and later |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the HAP because an application with the same <br>bundle name but different signature information exists on the device.<br>**Applicable version:** 13 and later |
| [17700077](../errorcode-bundle.md#17700077-application-installation-fails-but-preinstallation-is-successful) | Failed to install the HAP and restore to preinstalled bundle.<br>**Applicable version:** 17 and later |
| [17700076](../errorcode-bundle.md#17700076-application-installation-failure-due-to-unsupported-distribution-type-in-the-signing-certificate-profile) | Failed to install the HAP or HSP because the app distribution type is not allowed.<br>**Applicable version:** 18 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapFilePaths = ['/data/storage/el2/base/haps/entry/files/'];

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.install(hapFilePaths, (err: BusinessError) => {
            if (err) {
                console.error('install failed:' + err.message);
            } else {
                console.info('install successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## install

```TypeScript
install(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

Installs a specified app. This API uses a promise to return the result. Since API version 26.0.0, installing an APP package is supported.

> **NOTE:** 
> 
> To install apps of different distribution types, you need to apply for the corresponding permissions. For
> details about the distribution types, see the description of the appDistributionType field in
> [ApplicationInfo](arkts-ability-applicationinfo-i.md).

**Since:** 9

**Required permissions:** 
- API version 26 and later: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE) or ohos.permission.INSTALL_DEVELOPER_ID_BUNDLE
- API version 23 and later: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)
- API versions 13 to 22: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE
- API versions 10 to 12: ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE
- API version 9: ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | Yes | Path for storing the application package. The path should be the data directory where the HAP or APP is stored in the current app. When the path passed in is a directory, the directory can contain only the HAPs of the same app or one APP. The signatures of the HAPs of the same app must be consistent. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | No | Parameters required for the installation. For details about their default values, see [InstallParam](arkts-ability-installer-installparam-i-sys.md).<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE') or 'ohos.permission.INSTALL_DEVELOPER_ID_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature; 4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-bundle-installation-failure-because-the-dependent-module-does-not-exist) | Failed to install because the dependent module does not exist. |
| [17700031](../errorcode-bundle.md#17700031-hap-installation-fails-due-to-overlay-feature-verification-failure) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../errorcode-bundle.md#17700036-failure-in-installing-the-shared-library-because-of-no-allowappsharelibrary-privilege) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../errorcode-bundle.md#17700039-failure-in-installing-an-inter-application-shared-library) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-application-installation-is-not-allowed-by-enterprise-device-management) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-incorrect-uri-in-the-data-proxy) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-incorrect-permission-configuration-in-the-data-proxy) | Failed to install the HAP because of low APL in the non-system data proxy (required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-field-isolationmode-in-the-hap-conflicts-with-the-device-isolation-mode) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-application-version-to-be-updated-is-not-later-than-the-current-version) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the HAP because the code signature verification is failed.<br>**Applicable version:** 10 and later |
| [17700050](../errorcode-bundle.md#17700050-installation-of-enterprise-mdm-applications-and-standard-enterprise-applications-not-allowed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device.<br>**Applicable version:** 10 and later |
| [17700052](../errorcode-bundle.md#17700052-installing-a-debug-self-distributed-plugin-or-debug-application-is-not-allowed-in-non-developer-mode) | Failed to install the HAP because debug bundle cannot be installed under non -developer mode.<br>**Applicable version:** 11 and later |
| [17700054](../errorcode-bundle.md#17700054-bundle-installation-failure-due-to-permission-verification-failure) | Failed to install the HAP because the HAP requests wrong permissions.<br>**Applicable version:** 11 and later |
| [17700058](../errorcode-bundle.md#17700058-specified-application-cannot-be-installed-on-this-device-or-by-this-user) | Failed to install the HAP because the device has been controlled.<br>**Applicable version:** 12 and later |
| [17700066](../errorcode-bundle.md#17700066-failed-to-install-the-native-software-package) | Failed to install the HAP because installing the native package failed.<br>**Applicable version:** 12 and later |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the HAP because an application with the same <br>bundle name but different signature information exists on the device.<br>**Applicable version:** 13 and later |
| [17700077](../errorcode-bundle.md#17700077-application-installation-fails-but-preinstallation-is-successful) | Failed to install the HAP and restore to preinstalled bundle.<br>**Applicable version:** 17 and later |
| [17700076](../errorcode-bundle.md#17700076-application-installation-failure-due-to-unsupported-distribution-type-in-the-signing-certificate-profile) | Failed to install the HAP or HSP because the app distribution type is not allowed.<br>**Applicable version:** 18 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapFilePaths = ['/data/storage/el2/base/haps/entry/files/'];
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.install(hapFilePaths, installParam)
            .then((data: void) => {
                console.info('install successfully: ' + JSON.stringify(data));
        }).catch((error: BusinessError) => {
            console.error('install failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## installPlugin

```TypeScript
installPlugin(hostBundleName: string, pluginFilePaths: Array<string>, pluginParam?: PluginParam): Promise<void>
```

Installs a plugin for an application. This API uses a promise to return the result.

**Since:** 19

**Required permissions:** ohos.permission.INSTALL_PLUGIN_BUNDLE

<!--Device-BundleInstaller-installPlugin(hostBundleName: string, pluginFilePaths: Array<string>, pluginParam?: PluginParam): Promise<void>--><!--Device-BundleInstaller-installPlugin(hostBundleName: string, pluginFilePaths: Array<string>, pluginParam?: PluginParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hostBundleName | string | Yes | Bundle name of the application for which the plugin is to be installed. |
| pluginFilePaths | Array&lt;string&gt; | Yes | Paths where the plugin package files are stored. If multiple file paths or a directory is provided, ensure that these files are HSPs of the same plugin program and their signatures are consistent. |
| pluginParam | [PluginParam](arkts-ability-installer-pluginparam-i-sys.md) | No | Parameters required for installing the plugin. For details about the default value, see [PluginParam](arkts-ability-installer-pluginparam-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_PLUGIN_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified hostBundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The userId is invalid. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the plugin because the plugin fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the plugin because the plugin signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the plugin because the HSP path is invalid or the HSP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the plugin because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the plugin because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the plugin since the version of the plugin to install is too early. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the plugin because the code signature verification is failed. |
| [17700052](../errorcode-bundle.md#17700052-installing-a-debug-self-distributed-plugin-or-debug-application-is-not-allowed-in-non-developer-mode) | Failed to install the plugin because debug bundle cannot be installed under non-developer mode. |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the plugin because a plugin with the same <br>bundle name but different signature information exists on the device. |
| [17700087](../errorcode-bundle.md#17700087-unsupported-plugin-installation) | Failed to install the plugin because the current device does not support plugin. |
| [17700088](../errorcode-bundle.md#17700088-plugin-installation-failure-due-to-no-permission) | Failed to install the plugin because the host application lacks ohos.permission.kernel.SUPPORT_PLUGIN. |
| [17700089](../errorcode-bundle.md#17700089-plugin-installation-failure-because-of-plugin-id-parsing-failure) | Failed to install the plugin because the plugin id fails to be parsed. |
| [17700090](../errorcode-bundle.md#17700090-plugin-installation-failure-because-of-plugin-id-verification-failure) | Failed to install the plugin because the plugin id fails to be verified. |
| [17700091](../errorcode-bundle.md#17700091-plugin-installation-failure-because-of-the-same-plugin-name-and-host-bundle-name) | Failed to install the plugin because the plugin name is same as host bundle name. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hostBundleName = 'com.example.application';
let pluginFilePaths = ['/data/bms_app_install/test.hsp'];
let pluginParam : installer.PluginParam = {
    userId : 100,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.installPlugin(hostBundleName, pluginFilePaths, pluginParam)
            .then(() => {
                console.info('installPlugin successfully.');
        }).catch((error: BusinessError) => {
            console.error('installPlugin failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('installPlugin failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## installPreexistingApp

```TypeScript
installPreexistingApp(bundleName: string, userId?: number): Promise<void>
```

Installs the app with the specified bundleName for the specified user. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API does not support installing apps whose
> [appDistributionType](arkts-ability-applicationinfo-i.md) is enterprise, enterprise_mdm, or
> enterprise_normal.

**Since:** 12

**Required permissions:** ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-installPreexistingApp(bundleName: string, userId?: int): Promise<void>--><!--Device-BundleInstaller-installPreexistingApp(bundleName: string, userId?: int): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application to install. |
| userId | number | No | User ID of the app to be installed. It can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The value must be greater than 0. Default value: the user of the caller. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The userId is invalid. |
| [17700071](../errorcode-bundle.md#17700071-enterprise-applications-cannot-be-installed) | It is not allowed to install the enterprise bundle. |
| [17700058](../errorcode-bundle.md#17700058-specified-application-cannot-be-installed-on-this-device-or-by-this-user) | Failed to install the HAP because this application is prohibited <br>from being installed on this device or by specified users.<br>**Applicable version:** 14 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.camera';
let userId = 100;

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.installPreexistingApp(bundleName, userId)
            .then(() => {
                console.info('installPreexistingApp successfully.');
        }).catch((error: BusinessError) => {
            console.error('installPreexistingApp failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## recover

```TypeScript
recover(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void
```

Rolls back an application to the initial installation state. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

<!--Device-BundleInstaller-recover(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-recover(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the target bundle. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | Yes | Other parameters required for recovery. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) invoked to return the result. If the app rollback is successful, err is undefined; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the HAP because an application with the same <br>bundle name but different signature information exists on the device.<br>**Applicable version:** 13 and later |
| [17700058](../errorcode-bundle.md#17700058-specified-application-cannot-be-installed-on-this-device-or-by-this-user) | Failed to install the HAP because this application is prohibited <br>from being installed on this device or by specified users.<br>**Applicable version:** 14 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.demo';
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.recover(bundleName, installParam, (err: BusinessError) => {
            if (err) {
                console.error('recover failed:' + err.message);
            } else {
                console.info('recover successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## recover

```TypeScript
recover(bundleName: string, callback: AsyncCallback<void>): void
```

Rolls back an application to the initial installation state. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

<!--Device-BundleInstaller-recover(bundleName: string, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-recover(bundleName: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the target bundle. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the app is rolled back successfully, err is undefined; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the HAP because an application with the same <br>bundle name but different signature information exists on the device.<br>**Applicable version:** 13 and later |
| [17700058](../errorcode-bundle.md#17700058-specified-application-cannot-be-installed-on-this-device-or-by-this-user) | Failed to install the HAP because this application is prohibited <br>from being installed on this device or by specified users.<br>**Applicable version:** 14 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.demo';

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.recover(bundleName, (err: BusinessError) => {
            if (err) {
                console.error('recover failed:' + err.message);
            } else {
                console.info('recover successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## recover

```TypeScript
recover(bundleName: string, installParam?: InstallParam): Promise<void>
```

Rolls back an application to the initial installation state. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

<!--Device-BundleInstaller-recover(bundleName: string, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-recover(bundleName: string, installParam?: InstallParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application to be recovered. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | No | Specifies other parameters required for recovery. Default value: refer to the default value of [InstallParam](arkts-ability-installer-installparam-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the HAP because an application with the same <br>bundle name but different signature information exists on the device.<br>**Applicable version:** 13 and later |
| [17700058](../errorcode-bundle.md#17700058-specified-application-cannot-be-installed-on-this-device-or-by-this-user) | Failed to install the HAP because this application is prohibited <br>from being installed on this device or by specified users.<br>**Applicable version:** 14 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.demo';
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.recover(bundleName, installParam)
            .then((data: void) => {
                console.info('recover successfully: ' + JSON.stringify(data));
        }).catch((error: BusinessError) => {
            console.error('recover failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## removeExtResource

```TypeScript
removeExtResource(bundleName: string, moduleNames: Array<string>): Promise<void>
```

Removes extended resources based on the specified bundle name and module names. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-removeExtResource(bundleName: string, moduleNames: Array<string>): Promise<void>--><!--Device-BundleInstaller-removeExtResource(bundleName: string, moduleNames: Array<string>): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application whose extended resources are to be deleted. |
| moduleNames | Array&lt;string&gt; | Yes | Names of the modules whose extended resources are to be removed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700302](../errorcode-bundle.md#17700302-failed-to-delete-extended-resources) | RemoveExtResource failed due to module does not exist. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName : string = 'com.ohos.demo';
let moduleNames : Array<string> = ['moduleTest'];
try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.removeExtResource(bundleName, moduleNames).then((data) => {
            console.info('removeExtResource successfully');
        }).catch((err: BusinessError) => {
            console.error('removeExtResource failed. Cause: ' + err.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstall

```TypeScript
uninstall(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void
```

Uninstalls an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-uninstall(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the target bundle. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | Yes | Specifies other parameters required for uninstallation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the app is uninstalled successfully, **err** is undefined; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700020](../errorcode-bundle.md#17700020-failure-to-uninstall-preinstalled-applications) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../errorcode-bundle.md#17700040-failure-in-uninstalling-an-inter-application-shared-library) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../errorcode-bundle.md#17700045-application-uninstall-is-not-allowed-by-enterprise-device-management) | Failed to uninstall the HAP because uninstall is not allowed by the enterprise device management. |
| [17700067](../errorcode-bundle.md#17700067-failed-to-uninstall-the-native-software-package) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**Applicable version:** 12 and later |
| [17700060](../errorcode-bundle.md#17700060-specified-application-cannot-be-uninstalled) | The specified application cannot be uninstalled.<br>**Applicable version:** 13 and later |
| [17700062](../errorcode-bundle.md#17700062-failed-to-uninstall-an-application-configured-with-an-uninstallation-disposed-rule) | Failed to uninstall the app because the app is locked.<br>**Applicable version:** 15 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.demo';
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstall(bundleName, installParam, (err: BusinessError) => {
            if (err) {
                console.error('uninstall failed:' + err.message);
            } else {
                console.info('uninstall successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstall

```TypeScript
uninstall(bundleName: string, callback: AsyncCallback<void>): void
```

Uninstalls an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(bundleName: string, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-uninstall(bundleName: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the target bundle. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the app is uninstalled successfully, **err** is undefined; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700020](../errorcode-bundle.md#17700020-failure-to-uninstall-preinstalled-applications) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../errorcode-bundle.md#17700040-failure-in-uninstalling-an-inter-application-shared-library) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../errorcode-bundle.md#17700045-application-uninstall-is-not-allowed-by-enterprise-device-management) | Failed to uninstall the HAP because uninstall is not allowed by the enterprise device management. |
| [17700067](../errorcode-bundle.md#17700067-failed-to-uninstall-the-native-software-package) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**Applicable version:** 12 and later |
| [17700060](../errorcode-bundle.md#17700060-specified-application-cannot-be-uninstalled) | The specified application cannot be uninstalled.<br>**Applicable version:** 13 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.demo';

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstall(bundleName, (err: BusinessError) => {
            if (err) {
                console.error('uninstall failed:' + err.message);
            } else {
                console.info('uninstall successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstall

```TypeScript
uninstall(bundleName: string, installParam?: InstallParam): Promise<void>
```

Uninstalls an application. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(bundleName: string, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-uninstall(bundleName: string, installParam?: InstallParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the target bundle. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | No | Specifies other parameters required for uninstallation. Default value: refer to the default values of [InstallParam](arkts-ability-installer-installparam-i-sys.md).<br>**Since:** 15 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700020](../errorcode-bundle.md#17700020-failure-to-uninstall-preinstalled-applications) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../errorcode-bundle.md#17700040-failure-in-uninstalling-an-inter-application-shared-library) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../errorcode-bundle.md#17700045-application-uninstall-is-not-allowed-by-enterprise-device-management) | Failed to uninstall the HAP because uninstall is not allowed by the enterprise device management. |
| [17700067](../errorcode-bundle.md#17700067-failed-to-uninstall-the-native-software-package) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**Applicable version:** 12 and later |
| [17700060](../errorcode-bundle.md#17700060-specified-application-cannot-be-uninstalled) | The specified application cannot be uninstalled.<br>**Applicable version:** 13 and later |
| [17700062](../errorcode-bundle.md#17700062-failed-to-uninstall-an-application-configured-with-an-uninstallation-disposed-rule) | Failed to uninstall the app because the app is locked.<br>**Applicable version:** 15 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.demo';
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstall(bundleName, installParam)
            .then((data: void) => {
                console.info('uninstall successfully: ' + JSON.stringify(data));
        }).catch((error: BusinessError) => {
            console.error('uninstall failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstall

```TypeScript
uninstall(uninstallParam: UninstallParam, callback: AsyncCallback<void>): void
```

Uninstalls a shared package. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uninstallParam | [UninstallParam](arkts-ability-installer-uninstallparam-i-sys.md) | Yes | Parameters required for the uninstall. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md), which is used to return the result. If the app is uninstalled successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700020](../errorcode-bundle.md#17700020-failure-to-uninstall-preinstalled-applications) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700037](../errorcode-bundle.md#17700037-failure-in-uninstalling-the-shared-library-due-to-dependency) | The version of shared bundle is dependent on other applications. |
| [17700038](../errorcode-bundle.md#17700038-shared-library-to-uninstall-does-not-exist) | The specified shared bundle does not exist. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uninstallParam: installer.UninstallParam = {
    bundleName: "com.ohos.demo",
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstall(uninstallParam, (err: BusinessError) => {
            if (err) {
                console.error('uninstall failed:' + err.message);
            } else {
                console.info('uninstall successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstall

```TypeScript
uninstall(uninstallParam: UninstallParam): Promise<void>
```

Uninstalls a shared package. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam): Promise<void>--><!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uninstallParam | [UninstallParam](arkts-ability-installer-uninstallparam-i-sys.md) | Yes | Parameters required for the uninstall. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700020](../errorcode-bundle.md#17700020-failure-to-uninstall-preinstalled-applications) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700037](../errorcode-bundle.md#17700037-failure-in-uninstalling-the-shared-library-due-to-dependency) | The version of shared bundle is dependent on other applications. |
| [17700038](../errorcode-bundle.md#17700038-shared-library-to-uninstall-does-not-exist) | The specified shared bundle does not exist. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uninstallParam: installer.UninstallParam = {
    bundleName: "com.ohos.demo",
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstall(uninstallParam, (err: BusinessError) => {
            if (err) {
                console.error('uninstall failed:' + err.message);
            } else {
                console.info('uninstall successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstallNewPreinstalledApps

```TypeScript
uninstallNewPreinstalledApps(bundleNames: Array<string>): Promise<void>
```

Uninstalls newly added preinstalled apps in batches. This API uses a promise to return the result.

**Since:** 24

**Required permissions:** ohos.permission.UNINSTALL_BUNDLE

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInstaller-uninstallNewPreinstalledApps(bundleNames: Array<string>): Promise<void>--><!--Device-BundleInstaller-uninstallNewPreinstalledApps(bundleNames: Array<string>): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleNames | Array&lt;string&gt; | Yes | List of bundle names of the apps to be uninstalled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleNames = ['com.example.application', 'com.example.demo'];

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstallNewPreinstalledApps(bundleNames)
            .then(() => {
                console.info('uninstallNewPreinstalledApps successfully.');
        }).catch((error: BusinessError) => {
            console.error('uninstallNewPreinstalledApps failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('uninstallNewPreinstalledApps failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstallPlugin

```TypeScript
uninstallPlugin(hostBundleName: string, pluginBundleName: string, pluginParam?: PluginParam): Promise<void>
```

Uninstalls a plugin for an application. This API uses a promise to return the result.

**Since:** 19

**Required permissions:** ohos.permission.UNINSTALL_PLUGIN_BUNDLE

<!--Device-BundleInstaller-uninstallPlugin(hostBundleName: string, pluginBundleName: string, pluginParam?: PluginParam): Promise<void>--><!--Device-BundleInstaller-uninstallPlugin(hostBundleName: string, pluginBundleName: string, pluginParam?: PluginParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hostBundleName | string | Yes | Bundle name of the application for which the plugin is to be uninstalled. |
| pluginBundleName | string | Yes | Bundle name of the plugin. |
| pluginParam | [PluginParam](arkts-ability-installer-pluginparam-i-sys.md) | No | Parameters required for uninstalling the plugin. For details about the default value, see [PluginParam](arkts-ability-installer-pluginparam-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.UNINSTALL_PLUGIN_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The user id is invalid. |
| [17700092](../errorcode-bundle.md#17700092-plugin-uninstall-failure-because-of-nonexistent-plugin-bundle-name) | Failed to uninstall the plugin because the specified plugin is not found. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hostBundleName = 'com.example.application';
let pluginBundleName = 'com.ohos.pluginDemo';
let pluginParam : installer.PluginParam = {
    userId : 100,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstallPlugin(hostBundleName, pluginBundleName, pluginParam)
            .then(() => {
                console.info('uninstallPlugin successfully.');
        }).catch((error: BusinessError) => {
            console.error('uninstallPlugin failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('uninstallPlugin failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## uninstallUpdates

```TypeScript
uninstallUpdates(bundleName: string, installParam?: InstallParam): Promise<void>
```

Uninstalls and updates a preinstalled application and restores it to the initial installation status. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstallUpdates(bundleName: string, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-uninstallUpdates(bundleName: string, installParam?: InstallParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the target bundle. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | No | Parameters required for the uninstall and update. For details about their default values, see [InstallParam](arkts-ability-installer-installparam-i-sys.md). The **userId** parameter cannot be specified. Calling this API will uninstall and update the application for all users. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700045](../errorcode-bundle.md#17700045-application-uninstall-is-not-allowed-by-enterprise-device-management) | Failed to uninstall because enterprise device management disallow uninstall. |
| [17700057](../errorcode-bundle.md#17700057-specified-application-is-not-a-preset-application) | Failed to uninstall updates because the HAP is not pre-installed. |
| [17700060](../errorcode-bundle.md#17700060-specified-application-cannot-be-uninstalled) | The specified application cannot be uninstalled.<br>**Applicable version:** 13 and later |
| [17700067](../errorcode-bundle.md#17700067-failed-to-uninstall-the-native-software-package) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**Applicable version:** 13 and later |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the HAP because an application with the same <br>bundle name but different signature information exists on the device.<br>**Applicable version:** 13 and later |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.ohos.camera';
let installParam: installer.InstallParam = {
    isKeepData: true,
    installFlag: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.uninstallUpdates(bundleName, installParam)
            .then(() => {
                console.info('uninstallUpdates successfully.');
        }).catch((error: BusinessError) => {
            console.error('uninstallUpdates failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## updateBundleForSelf

```TypeScript
updateBundleForSelf(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void
```

Updates the current bundle. This API can be called only by enterprise MDM applications on enterprise devices, and the HAPs in **hapFilePaths** must belong to the current application. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INSTALL_SELF_BUNDLE

<!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | Yes | Paths where the HAP files of the bundle are stored, which are the data directories. If only one directory is passed, the HAP files in the directory must belong to the same bundle and have the same signature. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | Yes | Other parameters required for the update. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md), invoked when the application is updated successfully, in which case err is undefined; otherwise, an error object is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature;         4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3 000. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-bundle-installation-failure-because-the-dependent-module-does-not-exist) | Failed to install because the dependent module does not exist. |
| [17700039](../errorcode-bundle.md#17700039-failure-in-installing-an-inter-application-shared-library) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-application-installation-is-not-allowed-by-enterprise-device-management) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-incorrect-uri-in-the-data-proxy) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-incorrect-permission-configuration-in-the-data-proxy) | Failed to install the HAP because of low APL in the non-system data proxy (required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-field-isolationmode-in-the-hap-conflicts-with-the-device-isolation-mode) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-application-version-to-be-updated-is-not-later-than-the-current-version) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../errorcode-bundle.md#17700049-update-failure-because-of-incorrect-bundle-name) | Failed to install the HAP because the bundleName is different from the bundleName of the caller application. |
| [17700050](../errorcode-bundle.md#17700050-installation-of-enterprise-mdm-applications-and-standard-enterprise-applications-not-allowed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device. |
| [17700051](../errorcode-bundle.md#17700051-hap-installation-failure-due-to-incorrect-distribution-type-in-the-signing-certificate-profile-of-the-caller) | Failed to install the HAP because the distribution type of caller application is not enterprise_mdm. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapFilePaths = ['/data/storage/el2/base/haps/entry/files/'];
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.updateBundleForSelf(hapFilePaths, installParam, (err: BusinessError) => {
            if (err) {
                console.error('updateBundleForSelf failed:' + err.message);
            } else {
                console.info('updateBundleForSelf successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## updateBundleForSelf

```TypeScript
updateBundleForSelf(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void
```

Updates the current bundle. This API can be called only by enterprise MDM applications on enterprise devices, and the HAPs in **hapFilePaths** must belong to the current application. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INSTALL_SELF_BUNDLE

<!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | Yes | Paths where the HAP files of the bundle are stored, which are the data directories. If only one directory is passed, the HAP files in the directory must belong to the same bundle and have the same signature. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md), invoked to return the result. If the application is updated successfully, err is undefined; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-bundle-installation-failure-because-the-dependent-module-does-not-exist) | Failed to install because the dependent module does not exist. |
| [17700039](../errorcode-bundle.md#17700039-failure-in-installing-an-inter-application-shared-library) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-application-installation-is-not-allowed-by-enterprise-device-management) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-incorrect-uri-in-the-data-proxy) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-incorrect-permission-configuration-in-the-data-proxy) | Failed to install the HAP because of low APL in the non-system data proxy (required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-field-isolationmode-in-the-hap-conflicts-with-the-device-isolation-mode) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-application-version-to-be-updated-is-not-later-than-the-current-version) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../errorcode-bundle.md#17700049-update-failure-because-of-incorrect-bundle-name) | Failed to install the HAP because the bundleName is different from the bundleName of the caller application. |
| [17700050](../errorcode-bundle.md#17700050-installation-of-enterprise-mdm-applications-and-standard-enterprise-applications-not-allowed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device. |
| [17700051](../errorcode-bundle.md#17700051-hap-installation-failure-due-to-incorrect-distribution-type-in-the-signing-certificate-profile-of-the-caller) | Failed to install the HAP because the distribution type of caller application is not enterprise_mdm. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapFilePaths = ['/data/storage/el2/base/haps/entry/files/'];

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.updateBundleForSelf(hapFilePaths, (err: BusinessError) => {
            if (err) {
                console.error('updateBundleForSelf failed:' + err.message);
            } else {
                console.info('updateBundleForSelf successfully.');
            }
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->

## updateBundleForSelf

```TypeScript
updateBundleForSelf(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

Updates the current bundle. This API can be called only by enterprise MDM applications on enterprise devices, and the HAPs in **hapFilePaths** must belong to the current application. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INSTALL_SELF_BUNDLE

<!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | Yes | Paths where the HAP files of the bundle are stored, which are the data directories. If only one directory is passed, the HAP files in the directory must belong to the same bundle and have the same signature. |
| installParam | [InstallParam](arkts-ability-installer-installparam-i-sys.md) | No | Other parameters required for the update. Default value: refer to the default values of [InstallParam](arkts-ability-installer-installparam-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature;         4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3 000. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-bundle-installation-failure-because-the-dependent-module-does-not-exist) | Failed to install because the dependent module does not exist. |
| [17700039](../errorcode-bundle.md#17700039-failure-in-installing-an-inter-application-shared-library) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-application-installation-is-not-allowed-by-enterprise-device-management) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-incorrect-uri-in-the-data-proxy) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-incorrect-permission-configuration-in-the-data-proxy) | Failed to install the HAP because of low APL in the non-system data proxy (required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-field-isolationmode-in-the-hap-conflicts-with-the-device-isolation-mode) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-application-version-to-be-updated-is-not-later-than-the-current-version) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../errorcode-bundle.md#17700049-update-failure-because-of-incorrect-bundle-name) | Failed to install the HAP because the bundleName is different from the bundleName of the caller application. |
| [17700050](../errorcode-bundle.md#17700050-installation-of-enterprise-mdm-applications-and-standard-enterprise-applications-not-allowed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device. |
| [17700051](../errorcode-bundle.md#17700051-hap-installation-failure-due-to-incorrect-distribution-type-in-the-signing-certificate-profile-of-the-caller) | Failed to install the HAP because the distribution type of caller application is not enterprise_mdm. |

<!--Del-->
**Examples**

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapFilePaths = ['/data/storage/el2/base/haps/entry/files/'];
let installParam: installer.InstallParam = {
    userId: 100,
    isKeepData: false,
    installFlag: 1,
};

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        data.updateBundleForSelf(hapFilePaths, installParam)
            .then((data: void) => {
                console.info('updateBundleForSelf successfully: ' + JSON.stringify(data));
        }).catch((error: BusinessError) => {
            console.error('updateBundleForSelf failed:' + error.message);
        });
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

<!--DelEnd-->
