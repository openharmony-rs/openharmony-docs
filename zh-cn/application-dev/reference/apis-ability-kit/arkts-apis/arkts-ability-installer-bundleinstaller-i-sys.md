# BundleInstaller（系统接口）

Bundle installer interface, include install uninstall recover.

**起始版本：** 9

<!--Device-installer-interface BundleInstaller--><!--Device-installer-interface BundleInstaller-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## addExtResource

```TypeScript
addExtResource(bundleName: string, filePaths: Array<string>): Promise<void>
```

根据给定的bundleName和hsp文件路径添加扩展资源。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-addExtResource(bundleName: string, filePaths: Array<string>): Promise<void>--><!--Device-BundleInstaller-addExtResource(bundleName: string, filePaths: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要添加扩展资源的应用名称。 |
| filePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 要添加扩展资源的资源路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700301](../errorcode-bundle.md#17700301-扩展资源添加失败) | AddExtResource failed due to parse file failed. |

**示例：**

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

## createAppClone

```TypeScript
createAppClone(bundleName: string, createAppCloneParam?: CreateAppCloneParam): Promise<number>
```

创建应用分身。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_CLONE_BUNDLE

<!--Device-BundleInstaller-createAppClone(bundleName: string, createAppCloneParam?: CreateAppCloneParam): Promise<int>--><!--Device-BundleInstaller-createAppClone(bundleName: string, createAppCloneParam?: CreateAppCloneParam): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待创建应用分身的包名。 |
| createAppCloneParam | [CreateAppCloneParam](arkts-ability-installer-createappcloneparam-i-sys.md) | 否 | 指定创建应用分身所需的其他参数，默认值：参照[createAppCloneParam](arkts-ability-installer-createappcloneparam-i-sys.md)的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回创建的分身应用索引值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The userId is invalid. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The appIndex is not in valid range or already exists. |
| [17700069](../errorcode-bundle.md#17700069-应用不支持创建分身) | The app does not support the creation of an appClone instance. |

**示例：**

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

## destroyAppClone

```TypeScript
destroyAppClone(bundleName: string, appIndex: number, userId?: number): Promise<void>
```

删除应用分身。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.UNINSTALL_CLONE_BUNDLE

<!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, userId?: number): Promise<void>--><!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, userId?: number): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待删除应用分身的包名。 |
| appIndex | number | 是 | 待删除应用分身的索引。 |
| userId | number | 否 | 待删除应用分身所属用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取。默认值：调用方所在用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.UNINSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The userId is invalid. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |

**示例：**

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

## destroyAppClone

```TypeScript
destroyAppClone(bundleName: string, appIndex: number, destroyAppCloneParam?: DestroyAppCloneParam): Promise<void>
```

删除应用分身。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.UNINSTALL_CLONE_BUNDLE

<!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, destroyAppCloneParam?: DestroyAppCloneParam): Promise<void>--><!--Device-BundleInstaller-destroyAppClone(bundleName: string, appIndex: number, destroyAppCloneParam?: DestroyAppCloneParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待删除应用分身的包名。 |
| appIndex | number | 是 | 待删除应用分身的索引。 |
| destroyAppCloneParam | [DestroyAppCloneParam](arkts-ability-installer-destroyappcloneparam-i-sys.md) | 否 | 指定删除应用分身所需的其他参数，默认值：参照[DestroyAppCloneParam](arkts-ability-installer-destroyappcloneparam-i-sys.md)的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.UNINSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The userId is invalid. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |
| [17700062](../errorcode-bundle.md#17700062-应用设置了卸载处置规则不允许直接卸载) | Failed to uninstall the app because the app is locked. |

**示例：**

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

## install

```TypeScript
install(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void
```

安装指定应用。使用callback异步回调。

> **说明：**  
>  
> 安装不同分发类型的应用需要申请相应的权限，分发类型可以参考[ApplicationInfo](arkts-ability-applicationinfo-i.md)中的  
> appDistributionType字段说明。

**起始版本：** 9

**需要权限：** 
- API版本23+：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)
- API版本13 - 22：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE
- API版本10 - 12：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE
- API版本9：ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 存储应用程序包的路径。路径应该是当前应用程序中存放HAP的数据目录。当传入的路径是一个目录时， 该目录下只能放同一个应用的HAP，且这些HAP的签名需要保持一致。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 是 | 指定安装所需的其他参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，安装应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE'). |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature; 4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-安装失败依赖的模块不存在) | Failed to install because the dependent module does not exist. |
| [17700031](../errorcode-bundle.md#17700031-overlay特征校验失败导致hap安装失败) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../errorcode-bundle.md#17700036-共享库缺少allowappsharelibrary特权导致安装失败) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../errorcode-bundle.md#17700039-不允许安装应用间共享库) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-企业设备管理不允许安装该应用) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-数据代理中的uri配置错误) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-数据代理中的权限配置错误) | Failed to install the HAP because of low APL in the non-system data proxy(required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-安装包设置的多进程配置项与系统配置项设置矛盾) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-要更新的应用版本没有大于当前版本) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the HAP because the code signature verification is failed.<br>**适用版本：** 10+ |
| [17700050](../errorcode-bundle.md#17700050-企业mdm应用普通企业应用不允许安装) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device.<br>**适用版本：** 10+ |
| [17700052](../errorcode-bundle.md#17700052-非开发者模式下不允许安装调试应用) | Failed to install the HAP because debug bundle cannot be installed under non  -developer mode.<br>**适用版本：** 11+ |
| [17700054](../errorcode-bundle.md#17700054-权限校验失败导致应用安装失败) | Failed to install the HAP because the HAP requests wrong permissions.<br>**适用版本：** 11+ |
| [17700058](../errorcode-bundle.md#17700058-指定的应用禁止在本设备或指定用户下安装) | Failed to install the HAP because the device has been controlled.<br>**适用版本：** 12+ |
| [17700066](../errorcode-bundle.md#17700066-安装失败native软件包安装失败) | Failed to install the HAP because installing the native package failed.<br>**适用版本：** 12+ |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the HAP because an application with the same<br>bundle name but different signature information exists on the device.<br>**适用版本：** 13+ |
| [17700077](../errorcode-bundle.md#17700077-安装应用失败但安装对应的预置应用成功) | Failed to install the HAP and restore to preinstalled bundle.<br>**适用版本：** 17+ |
| [17700076](../errorcode-bundle.md#17700076-签名证书profile文件中的类型被限制不允许安装到当前设备中导致安装失败) | Failed to install the HAP or HSP because the app distribution type is not allowed.<br>**适用版本：** 18+ |

**示例：**

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

## install

```TypeScript
install(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void
```

安装指定应用。使用callback异步回调。

> **说明：**  
>  
> 安装不同分发类型的应用需要申请相应的权限，分发类型可以参考[ApplicationInfo](arkts-ability-applicationinfo-i.md)中的  
> appDistributionType字段说明。

**起始版本：** 9

**需要权限：** 
- API版本23+：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)
- API版本13 - 22：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE
- API版本10 - 12：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE
- API版本9：ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-install(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-install(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 存储应用程序包的路径。路径应该是当前应用程序中存放HAP的数据目录。当传入的路径是一个目录时， 该目录下只能放同一个应用的HAP，且这些HAP的签名需要保持一致。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，安装应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE'). |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-安装失败依赖的模块不存在) | Failed to install because the dependent module does not exist. |
| [17700031](../errorcode-bundle.md#17700031-overlay特征校验失败导致hap安装失败) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../errorcode-bundle.md#17700036-共享库缺少allowappsharelibrary特权导致安装失败) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../errorcode-bundle.md#17700039-不允许安装应用间共享库) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-企业设备管理不允许安装该应用) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-数据代理中的uri配置错误) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-数据代理中的权限配置错误) | Failed to install the HAP because of low APL in the non-system data proxy(required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-安装包设置的多进程配置项与系统配置项设置矛盾) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-要更新的应用版本没有大于当前版本) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the HAP because the code signature verification is failed.<br>**适用版本：** 10+ |
| [17700050](../errorcode-bundle.md#17700050-企业mdm应用普通企业应用不允许安装) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device.<br>**适用版本：** 10+ |
| [17700052](../errorcode-bundle.md#17700052-非开发者模式下不允许安装调试应用) | Failed to install the HAP because debug bundle cannot be installed under non  -developer mode.<br>**适用版本：** 11+ |
| [17700054](../errorcode-bundle.md#17700054-权限校验失败导致应用安装失败) | Failed to install the HAP because the HAP requests wrong permissions.<br>**适用版本：** 11+ |
| [17700058](../errorcode-bundle.md#17700058-指定的应用禁止在本设备或指定用户下安装) | Failed to install the HAP because the device has been controlled.<br>**适用版本：** 12+ |
| [17700066](../errorcode-bundle.md#17700066-安装失败native软件包安装失败) | Failed to install the HAP because installing the native package failed.<br>**适用版本：** 12+ |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the HAP because an application with the same<br>bundle name but different signature information exists on the device.<br>**适用版本：** 13+ |
| [17700077](../errorcode-bundle.md#17700077-安装应用失败但安装对应的预置应用成功) | Failed to install the HAP and restore to preinstalled bundle.<br>**适用版本：** 17+ |
| [17700076](../errorcode-bundle.md#17700076-签名证书profile文件中的类型被限制不允许安装到当前设备中导致安装失败) | Failed to install the HAP or HSP because the app distribution type is not allowed.<br>**适用版本：** 18+ |

**示例：**

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

## install

```TypeScript
install(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

安装指定应用。使用Promise异步回调。

> **说明：**  
>  
> 安装不同分发类型的应用需要申请相应的权限，分发类型可以参考[ApplicationInfo](arkts-ability-applicationinfo-i.md)中的  
> appDistributionType字段说明。

**起始版本：** 9

**需要权限：** 
- API版本23+：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)
- API版本13 - 22：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE
- API版本10 - 12：ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE
- API版本9：ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-install(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 存储应用程序包的路径。路径应该是当前应用程序中存放HAP的数据目录。当传入的路径是一个目录时， 该目录下只能放同一个应用的HAP，且这些HAP的签名需要保持一致。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 否 | 指定安装所需的其他参数，默认值：参照[InstallParam](arkts-ability-installer-installparam-i-sys.md)的默认值。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE'). |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature; 4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-安装失败依赖的模块不存在) | Failed to install because the dependent module does not exist. |
| [17700031](../errorcode-bundle.md#17700031-overlay特征校验失败导致hap安装失败) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../errorcode-bundle.md#17700036-共享库缺少allowappsharelibrary特权导致安装失败) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../errorcode-bundle.md#17700039-不允许安装应用间共享库) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-企业设备管理不允许安装该应用) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-数据代理中的uri配置错误) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-数据代理中的权限配置错误) | Failed to install the HAP because of low APL in the non-system data proxy(required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-安装包设置的多进程配置项与系统配置项设置矛盾) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-要更新的应用版本没有大于当前版本) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the HAP because the code signature verification is failed.<br>**适用版本：** 10+ |
| [17700050](../errorcode-bundle.md#17700050-企业mdm应用普通企业应用不允许安装) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device.<br>**适用版本：** 10+ |
| [17700052](../errorcode-bundle.md#17700052-非开发者模式下不允许安装调试应用) | Failed to install the HAP because debug bundle cannot be installed under non  -developer mode.<br>**适用版本：** 11+ |
| [17700054](../errorcode-bundle.md#17700054-权限校验失败导致应用安装失败) | Failed to install the HAP because the HAP requests wrong permissions.<br>**适用版本：** 11+ |
| [17700058](../errorcode-bundle.md#17700058-指定的应用禁止在本设备或指定用户下安装) | Failed to install the HAP because the device has been controlled.<br>**适用版本：** 12+ |
| [17700066](../errorcode-bundle.md#17700066-安装失败native软件包安装失败) | Failed to install the HAP because installing the native package failed.<br>**适用版本：** 12+ |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the HAP because an application with the same<br>bundle name but different signature information exists on the device.<br>**适用版本：** 13+ |
| [17700077](../errorcode-bundle.md#17700077-安装应用失败但安装对应的预置应用成功) | Failed to install the HAP and restore to preinstalled bundle.<br>**适用版本：** 17+ |
| [17700076](../errorcode-bundle.md#17700076-签名证书profile文件中的类型被限制不允许安装到当前设备中导致安装失败) | Failed to install the HAP or HSP because the app distribution type is not allowed.<br>**适用版本：** 18+ |

**示例：**

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

## installPlugin

```TypeScript
installPlugin(hostBundleName: string, pluginFilePaths: Array<string>, pluginParam?: PluginParam): Promise<void>
```

应用安装插件。使用Promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.INSTALL_PLUGIN_BUNDLE

<!--Device-BundleInstaller-installPlugin(hostBundleName: string, pluginFilePaths: Array<string>, pluginParam?: PluginParam): Promise<void>--><!--Device-BundleInstaller-installPlugin(hostBundleName: string, pluginFilePaths: Array<string>, pluginParam?: PluginParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostBundleName | string | 是 | 待安装插件的应用包名。 |
| pluginFilePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 存储插件程序包的路径。当传入多个文件路径或者一个目录时，需确保这些文件是同一插件程序的HSP，且这些HSP的签名需要保持一致。 |
| pluginParam | [PluginParam](arkts-ability-installer-pluginparam-i-sys.md) | 否 | 指定安装插件所需的参数，默认值：参照 [PluginParam](arkts-ability-installer-pluginparam-i-sys.md) 的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_PLUGIN_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified hostBundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The userId is invalid. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the plugin because the plugin fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the plugin because the plugin signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the plugin because the HSP path is invalid or the HSP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the plugin because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the plugin because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the plugin since the version of the plugin to install is too early. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the plugin because the code signature verification is failed. |
| [17700052](../errorcode-bundle.md#17700052-非开发者模式下不允许安装调试应用) | Failed to install the plugin because debug bundle cannot be installed under non-developer mode. |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the plugin because a plugin with the same<br>bundle name but different signature information exists on the device. |
| [17700087](../errorcode-bundle.md#17700087-当前设备不支持安装插件) | Failed to install the plugin because the current device does not support plugin. |
| [17700088](../errorcode-bundle.md#17700088-应用缺少安装插件的权限) | Failed to install the plugin because the host application lacks ohos.permission.kernel.SUPPORT_PLUGIN. |
| [17700089](../errorcode-bundle.md#17700089-插件的-plugindistributionids-解析失败) | Failed to install the plugin because the plugin id fails to be parsed. |
| [17700090](../errorcode-bundle.md#17700090-插件与应用之间-plugindistributionids-校验失败) | Failed to install the plugin because the plugin id fails to be verified. |
| [17700091](../errorcode-bundle.md#17700091-插件与主体同包名) | Failed to install the plugin because the plugin name is same as host bundle name. |

**示例：**

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

## installPreexistingApp

```TypeScript
installPreexistingApp(bundleName: string, userId?: number): Promise<void>
```

在指定用户下安装指定bundleName的应用。使用Promise异步回调。

> **说明：**  
>  
> 该接口不支持安装[签名证书的分发类型](arkts-ability-applicationinfo-i.md)为enterprise，enterprise_mdm和  
> enterprise_normal的应用。

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-BundleInstaller-installPreexistingApp(bundleName: string, userId?: int): Promise<void>--><!--Device-BundleInstaller-installPreexistingApp(bundleName: string, userId?: int): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要安装应用的包名。 |
| userId | number | 否 | 需要安装应用的用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取，userId需要大于0。默认值：调用方所在用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName cannot be found or the bundle is not installed by the specified user. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The userId is invalid. |
| [17700071](../errorcode-bundle.md#17700071-不允许企业应用安装) | It is not allowed to install the enterprise bundle. |
| [17700058](../errorcode-bundle.md#17700058-指定的应用禁止在本设备或指定用户下安装) | Failed to install the HAP because this application is prohibited<br>from being installed on this device or by specified users.<br>**适用版本：** 14+ |

**示例：**

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

## recover

```TypeScript
recover(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void
```

回滚应用到初次安装时的状态。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

<!--Device-BundleInstaller-recover(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-recover(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待恢复应用的包名。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 是 | 指定安装所需的其他参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，回滚应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the HAP because an application with the same<br>bundle name but different signature information exists on the device.<br>**适用版本：** 13+ |
| [17700058](../errorcode-bundle.md#17700058-指定的应用禁止在本设备或指定用户下安装) | Failed to install the HAP because this application is prohibited<br>from being installed on this device or by specified users.<br>**适用版本：** 14+ |

**示例：**

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

## recover

```TypeScript
recover(bundleName: string, callback: AsyncCallback<void>): void
```

回滚应用到初次安装时的状态。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

<!--Device-BundleInstaller-recover(bundleName: string, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-recover(bundleName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待恢复应用的包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，回滚应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the HAP because an application with the same<br>bundle name but different signature information exists on the device.<br>**适用版本：** 13+ |
| [17700058](../errorcode-bundle.md#17700058-指定的应用禁止在本设备或指定用户下安装) | Failed to install the HAP because this application is prohibited<br>from being installed on this device or by specified users.<br>**适用版本：** 14+ |

**示例：**

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

## recover

```TypeScript
recover(bundleName: string, installParam?: InstallParam): Promise<void>
```

回滚应用到初次安装时的状态。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

<!--Device-BundleInstaller-recover(bundleName: string, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-recover(bundleName: string, installParam?: InstallParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待卸载应用的包名。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 否 | 指定安装所需的其他参数，默认值：参照[InstallParam](arkts-ability-installer-installparam-i-sys.md)的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or 'ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the HAP because an application with the same<br>bundle name but different signature information exists on the device.<br>**适用版本：** 13+ |
| [17700058](../errorcode-bundle.md#17700058-指定的应用禁止在本设备或指定用户下安装) | Failed to install the HAP because this application is prohibited<br>from being installed on this device or by specified users.<br>**适用版本：** 14+ |

**示例：**

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

## removeExtResource

```TypeScript
removeExtResource(bundleName: string, moduleNames: Array<string>): Promise<void>
```

根据给定的bundleName和moduleNames删除扩展资源。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-removeExtResource(bundleName: string, moduleNames: Array<string>): Promise<void>--><!--Device-BundleInstaller-removeExtResource(bundleName: string, moduleNames: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要删除扩展资源的应用名称。 |
| moduleNames | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 要删除扩展资源的moduleNames。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700302](../errorcode-bundle.md#17700302-扩展资源删除失败) | RemoveExtResource failed due to module does not exist. |

**示例：**

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

## uninstall

```TypeScript
uninstall(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void
```

卸载应用。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-uninstall(bundleName: string, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待卸载应用的包名。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 是 | 指定安装所需的其他参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，卸载应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700020](../errorcode-bundle.md#17700020-预置应用无法卸载) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../errorcode-bundle.md#17700040-不允许卸载应用间共享库) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../errorcode-bundle.md#17700045-企业设备管理不允许卸载该应用) | Failed to uninstall the HAP because uninstall is not allowed by the enterprise device management. |
| [17700067](../errorcode-bundle.md#17700067-卸载应用失败native软件包卸载失败) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**适用版本：** 12+ |
| [17700060](../errorcode-bundle.md#17700060-指定的应用不允许被卸载) | The specified application cannot be uninstalled.<br>**适用版本：** 13+ |
| [17700062](../errorcode-bundle.md#17700062-应用设置了卸载处置规则不允许直接卸载) | Failed to uninstall the app because the app is locked.<br>**适用版本：** 15+ |

**示例：**

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

## uninstall

```TypeScript
uninstall(bundleName: string, callback: AsyncCallback<void>): void
```

卸载应用。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(bundleName: string, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-uninstall(bundleName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待卸载应用的包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，卸载应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700020](../errorcode-bundle.md#17700020-预置应用无法卸载) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../errorcode-bundle.md#17700040-不允许卸载应用间共享库) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../errorcode-bundle.md#17700045-企业设备管理不允许卸载该应用) | Failed to uninstall the HAP because uninstall is not allowed by the enterprise device management. |
| [17700067](../errorcode-bundle.md#17700067-卸载应用失败native软件包卸载失败) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**适用版本：** 12+ |
| [17700060](../errorcode-bundle.md#17700060-指定的应用不允许被卸载) | The specified application cannot be uninstalled.<br>**适用版本：** 13+ |

**示例：**

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

## uninstall

```TypeScript
uninstall(bundleName: string, installParam?: InstallParam): Promise<void>
```

卸载应用。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(bundleName: string, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-uninstall(bundleName: string, installParam?: InstallParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待卸载应用的包名。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 否 | 指定安装所需的其他参数，默认值：参照[InstallParam](arkts-ability-installer-installparam-i-sys.md)的默认值。<br>**起始版本：** 15 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700020](../errorcode-bundle.md#17700020-预置应用无法卸载) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../errorcode-bundle.md#17700040-不允许卸载应用间共享库) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../errorcode-bundle.md#17700045-企业设备管理不允许卸载该应用) | Failed to uninstall the HAP because uninstall is not allowed by the enterprise device management. |
| [17700067](../errorcode-bundle.md#17700067-卸载应用失败native软件包卸载失败) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**适用版本：** 12+ |
| [17700060](../errorcode-bundle.md#17700060-指定的应用不允许被卸载) | The specified application cannot be uninstalled.<br>**适用版本：** 13+ |
| [17700062](../errorcode-bundle.md#17700062-应用设置了卸载处置规则不允许直接卸载) | Failed to uninstall the app because the app is locked.<br>**适用版本：** 15+ |

**示例：**

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

## uninstall

```TypeScript
uninstall(uninstallParam: UninstallParam, callback: AsyncCallback<void>): void
```

卸载一个共享包。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uninstallParam | [UninstallParam](arkts-ability-installer-uninstallparam-i-sys.md) | 是 | 共享包卸载需指定的参数信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，卸载应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700020](../errorcode-bundle.md#17700020-预置应用无法卸载) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700037](../errorcode-bundle.md#17700037-被卸载的shared-library版本被其他应用依赖) | The version of shared bundle is dependent on other applications. |
| [17700038](../errorcode-bundle.md#17700038-被卸载的shared-library不存在) | The specified shared bundle does not exist. |

**示例：**

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

## uninstall

```TypeScript
uninstall(uninstallParam: UninstallParam): Promise<void>
```

卸载一个共享包。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam): Promise<void>--><!--Device-BundleInstaller-uninstall(uninstallParam: UninstallParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uninstallParam | [UninstallParam](arkts-ability-installer-uninstallparam-i-sys.md) | 是 | 共享包卸载需指定的参数信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700020](../errorcode-bundle.md#17700020-预置应用无法卸载) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700037](../errorcode-bundle.md#17700037-被卸载的shared-library版本被其他应用依赖) | The version of shared bundle is dependent on other applications. |
| [17700038](../errorcode-bundle.md#17700038-被卸载的shared-library不存在) | The specified shared bundle does not exist. |

**示例：**

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

## uninstallNewPreinstalledApps

```TypeScript
uninstallNewPreinstalledApps(bundleNames: Array<string>): Promise<void>
```

批量卸载新增的预置应用。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.UNINSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInstaller-uninstallNewPreinstalledApps(bundleNames: Array<string>): Promise<void>--><!--Device-BundleInstaller-uninstallNewPreinstalledApps(bundleNames: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleNames | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 待卸载的应用的包名列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

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

## uninstallPlugin

```TypeScript
uninstallPlugin(hostBundleName: string, pluginBundleName: string, pluginParam?: PluginParam): Promise<void>
```

应用卸载插件。使用Promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.UNINSTALL_PLUGIN_BUNDLE

<!--Device-BundleInstaller-uninstallPlugin(hostBundleName: string, pluginBundleName: string, pluginParam?: PluginParam): Promise<void>--><!--Device-BundleInstaller-uninstallPlugin(hostBundleName: string, pluginBundleName: string, pluginParam?: PluginParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostBundleName | string | 是 | 待卸载插件的应用包名。 |
| pluginBundleName | string | 是 | 插件的包名。 |
| pluginParam | [PluginParam](arkts-ability-installer-pluginparam-i-sys.md) | 否 | 指定卸载插件所需的参数，默认值：参照 [PluginParam](arkts-ability-installer-pluginparam-i-sys.md) 的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.UNINSTALL_PLUGIN_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The user id is invalid. |
| [17700092](../errorcode-bundle.md#17700092-插件包名不存在) | Failed to uninstall the plugin because the specified plugin is not found. |

**示例：**

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

## uninstallUpdates

```TypeScript
uninstallUpdates(bundleName: string, installParam?: InstallParam): Promise<void>
```

对预置应用进行卸载更新，恢复到初次安装时的状态。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

<!--Device-BundleInstaller-uninstallUpdates(bundleName: string, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-uninstallUpdates(bundleName: string, installParam?: InstallParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待卸载更新应用的包名。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 否 | 指定卸载更新所需的其他参数，默认值：参照[InstallParam](arkts-ability-installer-installparam-i-sys.md)的默认值。其中userId无法指定，调用本接口将对所有已安装相应应用的用户进行卸载更新操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700045](../errorcode-bundle.md#17700045-企业设备管理不允许卸载该应用) | Failed to uninstall because enterprise device management disallow uninstall. |
| [17700057](../errorcode-bundle.md#17700057-指定的应用不是预置应用) | Failed to uninstall updates because the HAP is not pre-installed. |
| [17700060](../errorcode-bundle.md#17700060-指定的应用不允许被卸载) | The specified application cannot be uninstalled.<br>**适用版本：** 13+ |
| [17700067](../errorcode-bundle.md#17700067-卸载应用失败native软件包卸载失败) | Failed to uninstall the HAP because uninstalling the native package failed.<br>**适用版本：** 13+ |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the HAP because an application with the same<br>bundle name but different signature information exists on the device.<br>**适用版本：** 13+ |

**示例：**

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

## updateBundleForSelf

```TypeScript
updateBundleForSelf(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void
```

更新当前应用，仅限企业设备上的企业MDM应用调用，且传入的hapFilePaths中的hap必须都属于当前应用。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_SELF_BUNDLE

<!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam: InstallParam, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 存储应用程序包的路径。路径应该是当前应用程序中存放HAP的数据目录。当传入的路径是一个目录时， 该目录下只能放同一个应用的HAP，且这些HAP的签名需要保持一致。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 是 | 指定安装所需的其他参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，安装应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature;4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-安装失败依赖的模块不存在) | Failed to install because the dependent module does not exist. |
| [17700039](../errorcode-bundle.md#17700039-不允许安装应用间共享库) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-企业设备管理不允许安装该应用) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-数据代理中的uri配置错误) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-数据代理中的权限配置错误) | Failed to install the HAP because of low APL in the non-system data proxy(required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-安装包设置的多进程配置项与系统配置项设置矛盾) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-要更新的应用版本没有大于当前版本) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../errorcode-bundle.md#17700049-应用自升级时安装的应用与调用方包名不同) | Failed to install the HAP because the bundleName is different from the bundleName of the caller application. |
| [17700050](../errorcode-bundle.md#17700050-企业mdm应用普通企业应用不允许安装) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device. |
| [17700051](../errorcode-bundle.md#17700051-应用自升级时调用方的签名证书profile文件中的类型不是企业mdm) | Failed to install the HAP because the distribution type of caller application is not enterprise_mdm. |

**示例：**

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

## updateBundleForSelf

```TypeScript
updateBundleForSelf(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void
```

更新当前应用，仅限企业设备上的企业MDM应用调用，且传入的hapFilePaths中的hap必须都属于当前应用。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_SELF_BUNDLE

<!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void--><!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 存储应用程序包的路径。路径应该是当前应用程序中存放HAP的数据目录。当传入的路径是一个目录时， 该目录下只能放同一个应用的HAP，且这些HAP的签名需要保持一致。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，安装应用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-安装失败依赖的模块不存在) | Failed to install because the dependent module does not exist. |
| [17700039](../errorcode-bundle.md#17700039-不允许安装应用间共享库) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-企业设备管理不允许安装该应用) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-数据代理中的uri配置错误) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-数据代理中的权限配置错误) | Failed to install the HAP because of low APL in the non-system data proxy(required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-安装包设置的多进程配置项与系统配置项设置矛盾) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-要更新的应用版本没有大于当前版本) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../errorcode-bundle.md#17700049-应用自升级时安装的应用与调用方包名不同) | Failed to install the HAP because the bundleName is different from the bundleName of the caller application. |
| [17700050](../errorcode-bundle.md#17700050-企业mdm应用普通企业应用不允许安装) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device. |
| [17700051](../errorcode-bundle.md#17700051-应用自升级时调用方的签名证书profile文件中的类型不是企业mdm) | Failed to install the HAP because the distribution type of caller application is not enterprise_mdm. |

**示例：**

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

## updateBundleForSelf

```TypeScript
updateBundleForSelf(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

更新当前应用，仅限企业设备上的企业MDM应用调用，且传入的hapFilePaths中的hap必须都属于当前应用。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_SELF_BUNDLE

<!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>--><!--Device-BundleInstaller-updateBundleForSelf(hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 存储应用程序包的路径。路径应该是当前应用程序中存放HAP的数据目录。当传入的路径是一个目录时， 该目录下只能放同一个应用的HAP，且这些HAP的签名需要保持一致。 |
| installParam | [InstallParam](../../apis-mdm-kit/arkts-apis/arkts-mdm-bundlemanager-installparam-i.md) | 否 | 指定安装所需的其他参数，默认值：参照[InstallParam](arkts-ability-installer-installparam-i-sys.md)的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature;4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the HAPs because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [17700018](../errorcode-bundle.md#17700018-安装失败依赖的模块不存在) | Failed to install because the dependent module does not exist. |
| [17700039](../errorcode-bundle.md#17700039-不允许安装应用间共享库) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../errorcode-bundle.md#17700041-企业设备管理不允许安装该应用) | Failed to install because enterprise device management disallow install. |
| [17700042](../errorcode-bundle.md#17700042-数据代理中的uri配置错误) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../errorcode-bundle.md#17700043-数据代理中的权限配置错误) | Failed to install the HAP because of low APL in the non-system data proxy(required APL: system_basic or system_core). |
| [17700044](../errorcode-bundle.md#17700044-安装包设置的多进程配置项与系统配置项设置矛盾) | Failed to install the HAP because the isolationMode configured is not supported. |
| [17700047](../errorcode-bundle.md#17700047-要更新的应用版本没有大于当前版本) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../errorcode-bundle.md#17700049-应用自升级时安装的应用与调用方包名不同) | Failed to install the HAP because the bundleName is different from the bundleName of the caller application. |
| [17700050](../errorcode-bundle.md#17700050-企业mdm应用普通企业应用不允许安装) | Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device. |
| [17700051](../errorcode-bundle.md#17700051-应用自升级时调用方的签名证书profile文件中的类型不是企业mdm) | Failed to install the HAP because the distribution type of caller application is not enterprise_mdm. |

**示例：**

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

