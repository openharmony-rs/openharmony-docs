# BundleInstaller（系统接口）

本模块提供设备上安装、升级和卸载应用的能力。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BundleInstaller](arkts-ability-installer-bundleinstaller-i-sys.md)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## install

```TypeScript
install(bundleFilePaths: Array<string>, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

在应用中安装hap，支持多hap安装。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [install](arkts-ability-installer-bundleinstaller-i-sys.md#install)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFilePaths | Array & lt;string & gt; | 是 | 指示存储HAP的沙箱路径。 |
| param | [InstallParam](arkts-ability-bundleinstaller-installparam-depr-i-sys.md) | 是 | 指定安装所需的其他参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[InstallStatus](arkts-ability-bundleinstaller-installstatus-depr-i-sys.md)&gt; | 是 | [回调函数](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，程序 启动作为入参的回调函数，返回安装状态信息。 |

**示例**

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

## recover

```TypeScript
recover(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

恢复一个应用程序，使用callback异步回调。当预置应用被卸载后，可以通过此接口进行恢复。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [recover](arkts-ability-installer-bundleinstaller-i-sys.md#recover)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| param | [InstallParam](arkts-ability-bundleinstaller-installparam-depr-i-sys.md) | 是 | 指定应用恢复所需的其他参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[InstallStatus](arkts-ability-bundleinstaller-installstatus-depr-i-sys.md)&gt; | 是 | [回调函数](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，程序 启动作为入参的回调函数，返回安装状态信息。 |

**示例**

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

## uninstall

```TypeScript
uninstall(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

卸载应用程序，使用callback异步回调，返回安装状态信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [uninstall](arkts-ability-installer-bundleinstaller-i-sys.md#uninstall)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| param | [InstallParam](arkts-ability-bundleinstaller-installparam-depr-i-sys.md) | 是 | 指定卸载所需的其他参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[InstallStatus](arkts-ability-bundleinstaller-installstatus-depr-i-sys.md)&gt; | 是 | [回调函数](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，程序 启动作为入参的回调函数，返回安装状态信息。 |

**示例**

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
