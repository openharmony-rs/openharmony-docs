# BundleInstaller (System API)

```TypeScript
export interface BundleInstaller
```

The module provides APIs for you to install, uninstall, and recover bundles on devices.

> **NOTE:** 
> 
> This module is no longer maintained since API version 9. You are advised to use
> [@ohos.bundle.installer.install](arkts-ability-bundle-installer.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [BundleInstaller](arkts-ability-installer-bundleinstaller-i-sys.md)

<!--Device-unnamed-export interface BundleInstaller--><!--Device-unnamed-export interface BundleInstaller-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## install

```TypeScript
install(bundleFilePaths: Array<string>, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

Installs a bundle. Multiple HAP files can be installed. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [install](arkts-ability-installer-bundleinstaller-i-sys.md#install)

**Required permissions:** ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-install(bundleFilePaths: Array<string>, param: InstallParam, callback: AsyncCallback<InstallStatus>): void--><!--Device-BundleInstaller-install(bundleFilePaths: Array<string>, param: InstallParam, callback: AsyncCallback<InstallStatus>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFilePaths | Array&lt;string&gt; | Yes | Sandbox path where the HAP files of the bundle are stored. For details about how to obtain the sandbox path, see [Obtaining the Sandbox Path](../../../reference/apis-ability-kit/js-apis-bundle-BundleInstaller-sys.md#obtaining-the-sandbox-path). |
| param | [InstallParam](arkts-ability-bundleinstaller-installparam-depr-i-sys.md) | Yes | Parameters required for bundle installation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[InstallStatus](arkts-ability-bundleinstaller-installstatus-depr-i-sys.md)&gt; | Yes | Callback used to return the installation status. |

<!--Del-->
**Examples**

```TypeScript
import bundleInstall from '@ohos.bundle.installer';
import { BusinessError } from '@ohos.base';

let hapFilePaths: Array<string> = ['/data/storage/el2/base/haps/entry/files/'];
let installParam: bundleInstall.InstallParam = {
  userId: 100,
  isKeepData: false,
  installFlag: 1,
};

bundleInstall.getBundleInstaller().then(installer => {
  installer.install(hapFilePaths, installParam, err => {
    if (err) {
      console.error('install failed:' + JSON.stringify(err));
    } else {
      console.info('install successfully.');
    }
  });
}).catch((error: BusinessError)=> {
  let message = (error as BusinessError).message;
  console.error('getBundleInstaller failed. Cause: ' + message);
});
```

<!--DelEnd-->

## recover

```TypeScript
recover(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

Recovers a bundle. This API uses an asynchronous callback to return the result. After a pre-installed bundle is uninstalled, you can call this API to recover it.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [recover](arkts-ability-installer-bundleinstaller-i-sys.md#recover)

**Required permissions:** ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-recover(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void--><!--Device-BundleInstaller-recover(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| param | [InstallParam](arkts-ability-bundleinstaller-installparam-depr-i-sys.md) | Yes | Parameters required for bundle recovery. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[InstallStatus](arkts-ability-bundleinstaller-installstatus-depr-i-sys.md)&gt; | Yes | Callback used to return the recovery status. |

<!--Del-->
**Examples**

```TypeScript
import bundleInstall from '@ohos.bundle.installer';
import { BusinessError } from '@ohos.base';

let bundleName: string = 'com.example.myapplication';
let installParam: bundleInstall.InstallParam = {
  userId: 100,
  isKeepData: false,
  installFlag: 1,
};

bundleInstall.getBundleInstaller().then(installer => {
  installer.recover(bundleName, installParam, err => {
    if (err) {
      console.error('recover failed:' + JSON.stringify(err));
    } else {
      console.info('recover successfully.');
    }
  });
}).catch((error: BusinessError) => {
  let message = (error as BusinessError).message;
  console.error('getBundleInstaller failed. Cause: ' + message);
});
```

<!--DelEnd-->

## uninstall

```TypeScript
uninstall(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

Uninstalls a bundle. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [uninstall](arkts-ability-installer-bundleinstaller-i-sys.md#uninstall)

**Required permissions:** ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void--><!--Device-BundleInstaller-uninstall(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| param | [InstallParam](arkts-ability-bundleinstaller-installparam-depr-i-sys.md) | Yes | Parameters required for bundle uninstall. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[InstallStatus](arkts-ability-bundleinstaller-installstatus-depr-i-sys.md)&gt; | Yes | Callback used to return the installation status. |

<!--Del-->
**Examples**

```TypeScript
import bundleInstall from '@ohos.bundle.installer';
import { BusinessError } from '@ohos.base';

let bundleName: string = 'com.example.myapplication';
let installParam: bundleInstall.InstallParam = {
  userId: 100,
  isKeepData: false,
  installFlag: 1,
};

bundleInstall.getBundleInstaller().then(installer => {
  installer.uninstall(bundleName, installParam, err => {
    if (err) {
      console.error('uninstall failed:' + JSON.stringify(err));
    } else {
      console.info('uninstall successfully.');
    }
  });
}).catch((error: BusinessError) => {
  let message = (error as BusinessError).message;
  console.error('getBundleInstaller failed. Cause: ' + message);
});
```

<!--DelEnd-->
