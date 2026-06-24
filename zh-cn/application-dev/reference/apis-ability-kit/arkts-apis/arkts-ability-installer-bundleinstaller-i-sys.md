# BundleInstaller（系统接口）

Bundle installer interface, include install uninstall recover.

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## addExtResource

```TypeScript
addExtResource(bundleName: string, filePaths: Array<string>): Promise<void>
```

���ݸ�����bundleName��hsp�ļ�·��������չ��Դ��ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ������չ��Դ��Ӧ�����ơ� |
| filePaths | Array&lt;string&gt; | 是 | Ҫ������չ��Դ����Դ·���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700301](../../errorcode-universal.md#17700301-AddExtResource) | AddExtResource failed due to parse file failed. |

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

����Ӧ�÷�����ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_CLONE_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ������Ӧ�÷����İ����� |
| createAppCloneParam | CreateAppCloneParam | 否 | ָ������Ӧ�÷������������������Ĭ��ֵ������<br/>[createAppCloneParam](arkts-ability-installer-createappcloneparam-i-sys.md#CreateAppCloneParam)��Ĭ��ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󡣷��ش����ķ���Ӧ������ֵ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName cannot be found or the bundle is not installed by<br/>the specified user. |
| [17700004](../../errorcode-universal.md#17700004-The) | The userId is invalid. |
| [17700061](../../errorcode-universal.md#17700061-The) | The appIndex is not in valid range or already exists. |
| [17700069](../../errorcode-universal.md#17700069-The) | The app does not support the creation of an appClone instance. |

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

ɾ��Ӧ�÷�����ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.UNINSTALL_CLONE_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ɾ��Ӧ�÷����İ����� |
| appIndex | number | 是 | ��ɾ��Ӧ�÷����������� |
| userId | number | 否 | ��ɾ��Ӧ�÷��������û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.UNINSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName cannot be found or the bundle is not installed by<br/>the specified user. |
| [17700004](../../errorcode-universal.md#17700004-The) | The userId is invalid. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |

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

ɾ��Ӧ�÷�����ʹ��Promise�첽�ص���

**起始版本：** 15

**需要权限：** ohos.permission.UNINSTALL_CLONE_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ɾ��Ӧ�÷����İ����� |
| appIndex | number | 是 | ��ɾ��Ӧ�÷����������� |
| destroyAppCloneParam | DestroyAppCloneParam | 否 | ָ��ɾ��Ӧ�÷������������������Ĭ��ֵ������<br/>[DestroyAppCloneParam](arkts-ability-installer-destroyappcloneparam-i-sys.md#DestroyAppCloneParam)��Ĭ��ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.UNINSTALL_CLONE_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName cannot be found or the bundle is not installed by<br/>the specified user. |
| [17700004](../../errorcode-universal.md#17700004-The) | The userId is invalid. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |
| [17700062](../../errorcode-universal.md#17700062-Failed) | Failed to uninstall the app because the app is locked. |

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

��װָ��Ӧ�á�ʹ��callback�첽�ص���

> **˵����**
>
> ��װ��ͬ�ַ����͵�Ӧ����Ҫ������Ӧ��Ȩ�ޣ��ַ����Ϳ��Բο�[ApplicationInfo](arkts-ability-applicationinfo-i.md#ApplicationInfo)�е�
> appDistributionType�ֶ�˵����

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | 是 | �洢Ӧ�ó������·����·��Ӧ���ǵ�ǰӦ�ó����д��HAP������Ŀ¼���������·����һ��Ŀ¼ʱ�� ��Ŀ¼��ֻ�ܷ�ͬһ��Ӧ�õ�HAP������ЩHAP��ǩ<br/>����Ҫ����һ�¡� |
| installParam | InstallParam | 是 | ָ����װ��������������� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)����װӦ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or '<br/>ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or<br/>'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'<br/>or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'<br/>or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE'). |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature; 4. The size of<br/>specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700010](../../errorcode-universal.md#17700010-Failed) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../../errorcode-universal.md#17700011-Failed) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../../errorcode-universal.md#17700012-Failed) | Failed to install the HAP because the HAP path is invalid or the HAP is too<br/>large. |
| [17700015](../../errorcode-universal.md#17700015-Failed) | Failed to install the HAPs because they have different configuration<br/>information. |
| [17700016](../../errorcode-universal.md#17700016-Failed) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../../errorcode-universal.md#17700017-Failed) | Failed to install the HAP since the version of the HAP to install is too<br/>early. |
| [17700018](../../errorcode-universal.md#17700018-Failed) | Failed to install because the dependent module does not exist. |
| [17700031](../../errorcode-universal.md#17700031-Failed) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../../errorcode-universal.md#17700036-Failed) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../../errorcode-universal.md#17700039-Failed) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../../errorcode-universal.md#17700041-Failed) | Failed to install because enterprise device management disallow install. |
| [17700042](../../errorcode-universal.md#17700042-Failed) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../../errorcode-universal.md#17700043-Failed) | Failed to install the HAP because of low APL in the non-system data proxy<br/>(required APL: system_basic or system_core). |
| [17700044](../../errorcode-universal.md#17700044-Failed) | Failed to install the HAP because the isolationMode configured is not<br/>supported. |
| [17700047](../../errorcode-universal.md#17700047-Failed) | Failed to install the HAP because the VersionCode to be updated is not<br/>greater than the current VersionCode. |
| [17700048](../../errorcode-universal.md#17700048-Failed) | Failed to install the HAP because the code signature verification is<br/>failed.&lt;br&gt;**适用版本：** 10+ |
| [17700050](../../errorcode-universal.md#17700050-Failed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be<br/>installed on non-enterprise device.&lt;br&gt;**适用版本：** 10+ |
| [17700052](../../errorcode-universal.md#17700052-Failed) | Failed to install the HAP because debug bundle cannot be installed under non<br/>-developer mode.&lt;br&gt;**适用版本：** 11+ |
| [17700054](../../errorcode-universal.md#17700054-Failed) | Failed to install the HAP because the HAP requests wrong<br/>permissions.&lt;br&gt;**适用版本：** 11+ |
| [17700058](../../errorcode-universal.md#17700058-Failed) | Failed to install the HAP because the device has been controlled.&lt;br&gt;**适用版本：** 12+ |
| [17700066](../../errorcode-universal.md#17700066-Failed) | Failed to install the HAP because installing the native package<br/>failed.&lt;br&gt;**适用版本：** 12+ |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the HAP because an application with the same<br/><br/>bundle name but different signature information exists on the device.&lt;br&gt;**适用版本：** 13+ |
| [17700077](../../errorcode-universal.md#17700077-Failed) | Failed to install the HAP and restore to preinstalled bundle.&lt;br&gt;**适用版本：** 17+ |
| [17700076](../../errorcode-universal.md#17700076-Failed) | Failed to install the HAP or HSP because the app distribution type is not<br/>allowed.&lt;br&gt;**适用版本：** 18+ |

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

��װָ��Ӧ�á�ʹ��callback�첽�ص���

> **˵����**
>
> ��װ��ͬ�ַ����͵�Ӧ����Ҫ������Ӧ��Ȩ�ޣ��ַ����Ϳ��Բο�[ApplicationInfo](arkts-ability-applicationinfo-i.md#ApplicationInfo)�е�
> appDistributionType�ֶ�˵����

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | 是 | �洢Ӧ�ó������·����·��Ӧ���ǵ�ǰӦ�ó����д��HAP������Ŀ¼���������·����һ��Ŀ¼ʱ�� ��Ŀ¼��ֻ�ܷ�ͬһ��Ӧ�õ�HAP������ЩHAP��ǩ<br/>����Ҫ����һ�¡� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)����װӦ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or '<br/>ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or<br/>'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'<br/>or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'<br/>or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE'). |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700010](../../errorcode-universal.md#17700010-Failed) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../../errorcode-universal.md#17700011-Failed) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../../errorcode-universal.md#17700012-Failed) | Failed to install the HAP because the HAP path is invalid or the HAP is too<br/>large. |
| [17700015](../../errorcode-universal.md#17700015-Failed) | Failed to install the HAPs because they have different configuration<br/>information. |
| [17700016](../../errorcode-universal.md#17700016-Failed) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../../errorcode-universal.md#17700017-Failed) | Failed to install the HAP since the version of the HAP to install is too<br/>early. |
| [17700018](../../errorcode-universal.md#17700018-Failed) | Failed to install because the dependent module does not exist. |
| [17700031](../../errorcode-universal.md#17700031-Failed) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../../errorcode-universal.md#17700036-Failed) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../../errorcode-universal.md#17700039-Failed) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../../errorcode-universal.md#17700041-Failed) | Failed to install because enterprise device management disallow install. |
| [17700042](../../errorcode-universal.md#17700042-Failed) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../../errorcode-universal.md#17700043-Failed) | Failed to install the HAP because of low APL in the non-system data proxy<br/>(required APL: system_basic or system_core). |
| [17700044](../../errorcode-universal.md#17700044-Failed) | Failed to install the HAP because the isolationMode configured is not<br/>supported. |
| [17700047](../../errorcode-universal.md#17700047-Failed) | Failed to install the HAP because the VersionCode to be updated is not<br/>greater than the current VersionCode. |
| [17700048](../../errorcode-universal.md#17700048-Failed) | Failed to install the HAP because the code signature verification is<br/>failed.&lt;br&gt;**适用版本：** 10+ |
| [17700050](../../errorcode-universal.md#17700050-Failed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be<br/>installed on non-enterprise device.&lt;br&gt;**适用版本：** 10+ |
| [17700052](../../errorcode-universal.md#17700052-Failed) | Failed to install the HAP because debug bundle cannot be installed under non<br/>-developer mode.&lt;br&gt;**适用版本：** 11+ |
| [17700054](../../errorcode-universal.md#17700054-Failed) | Failed to install the HAP because the HAP requests wrong<br/>permissions.&lt;br&gt;**适用版本：** 11+ |
| [17700058](../../errorcode-universal.md#17700058-Failed) | Failed to install the HAP because the device has been controlled.&lt;br&gt;**适用版本：** 12+ |
| [17700066](../../errorcode-universal.md#17700066-Failed) | Failed to install the HAP because installing the native package<br/>failed.&lt;br&gt;**适用版本：** 12+ |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the HAP because an application with the same<br/><br/>bundle name but different signature information exists on the device.&lt;br&gt;**适用版本：** 13+ |
| [17700077](../../errorcode-universal.md#17700077-Failed) | Failed to install the HAP and restore to preinstalled bundle.&lt;br&gt;**适用版本：** 17+ |
| [17700076](../../errorcode-universal.md#17700076-Failed) | Failed to install the HAP or HSP because the app distribution type is not<br/>allowed.&lt;br&gt;**适用版本：** 18+ |

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

��װָ��Ӧ�á�ʹ��Promise�첽�ص���

> **˵����**
>
> ��װ��ͬ�ַ����͵�Ӧ����Ҫ������Ӧ��Ȩ�ޣ��ַ����Ϳ��Բο�[ApplicationInfo](arkts-ability-applicationinfo-i.md#ApplicationInfo)�е�
> appDistributionType�ֶ�˵����

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE, ohos.permission.INSTALL_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE or ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE or ohos.permission.INSTALL_INTERNALTESTING_BUNDLE or (ohos.permission.INSTALL_BUNDLE and ohos.permission.INSTALL_ALLOW_DOWNGRADE)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | 是 | �洢Ӧ�ó������·����·��Ӧ���ǵ�ǰӦ�ó����д��HAP������Ŀ¼���������·����һ��Ŀ¼ʱ�� ��Ŀ¼��ֻ�ܷ�ͬһ��Ӧ�õ�HAP������ЩHAP��ǩ<br/>����Ҫ����һ�¡� |
| installParam | InstallParam | 否 | ָ����װ���������������Ĭ��ֵ������[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)��Ĭ��ֵ<br/>�� [since 12] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or '<br/>ohos.permission.INSTALL_ENTERPRISE_BUNDLE' or<br/>'ohos.permission.INSTALL_ENTERPRISE_MDM_BUNDLE' or 'ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE'<br/>or 'ohos.permission.INSTALL_INTERNALTESTING_BUNDLE'<br/>or ('ohos.permission.INSTALL_BUNDLE' and 'ohos.permission.INSTALL_ALLOW_DOWNGRADE'). |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature; 4. The size of<br/>specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3000. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700010](../../errorcode-universal.md#17700010-Failed) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../../errorcode-universal.md#17700011-Failed) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../../errorcode-universal.md#17700012-Failed) | Failed to install the HAP because the HAP path is invalid or the HAP is too<br/>large. |
| [17700015](../../errorcode-universal.md#17700015-Failed) | Failed to install the HAPs because they have different configuration<br/>information. |
| [17700016](../../errorcode-universal.md#17700016-Failed) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../../errorcode-universal.md#17700017-Failed) | Failed to install the HAP since the version of the HAP to install is too<br/>early. |
| [17700018](../../errorcode-universal.md#17700018-Failed) | Failed to install because the dependent module does not exist. |
| [17700031](../../errorcode-universal.md#17700031-Failed) | Failed to install the HAP because the overlay check of the HAP is failed. |
| [17700036](../../errorcode-universal.md#17700036-Failed) | Failed to install the HSP because lacks appropriate permissions. |
| [17700039](../../errorcode-universal.md#17700039-Failed) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../../errorcode-universal.md#17700041-Failed) | Failed to install because enterprise device management disallow install. |
| [17700042](../../errorcode-universal.md#17700042-Failed) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../../errorcode-universal.md#17700043-Failed) | Failed to install the HAP because of low APL in the non-system data proxy<br/>(required APL: system_basic or system_core). |
| [17700044](../../errorcode-universal.md#17700044-Failed) | Failed to install the HAP because the isolationMode configured is not<br/>supported. |
| [17700047](../../errorcode-universal.md#17700047-Failed) | Failed to install the HAP because the VersionCode to be updated is not<br/>greater than the current VersionCode. |
| [17700048](../../errorcode-universal.md#17700048-Failed) | Failed to install the HAP because the code signature verification is<br/>failed.&lt;br&gt;**适用版本：** 10+ |
| [17700050](../../errorcode-universal.md#17700050-Failed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be<br/>installed on non-enterprise device.&lt;br&gt;**适用版本：** 10+ |
| [17700052](../../errorcode-universal.md#17700052-Failed) | Failed to install the HAP because debug bundle cannot be installed under non<br/>-developer mode.&lt;br&gt;**适用版本：** 11+ |
| [17700054](../../errorcode-universal.md#17700054-Failed) | Failed to install the HAP because the HAP requests wrong<br/>permissions.&lt;br&gt;**适用版本：** 11+ |
| [17700058](../../errorcode-universal.md#17700058-Failed) | Failed to install the HAP because the device has been controlled.&lt;br&gt;**适用版本：** 12+ |
| [17700066](../../errorcode-universal.md#17700066-Failed) | Failed to install the HAP because installing the native package<br/>failed.&lt;br&gt;**适用版本：** 12+ |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the HAP because an application with the same<br/><br/>bundle name but different signature information exists on the device.&lt;br&gt;**适用版本：** 13+ |
| [17700077](../../errorcode-universal.md#17700077-Failed) | Failed to install the HAP and restore to preinstalled bundle.&lt;br&gt;**适用版本：** 17+ |
| [17700076](../../errorcode-universal.md#17700076-Failed) | Failed to install the HAP or HSP because the app distribution type is not<br/>allowed.&lt;br&gt;**适用版本：** 18+ |

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

Ӧ�ð�װ�����ʹ��Promise�첽�ص���

**起始版本：** 19

**需要权限：** ohos.permission.INSTALL_PLUGIN_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostBundleName | string | 是 | ����װ�����Ӧ�ð����� |
| pluginFilePaths | Array&lt;string&gt; | 是 | �洢����������·�������������ļ�·������һ��Ŀ¼ʱ����ȷ����Щ�ļ���ͬһ��������HSP������ЩHSP��ǩ����Ҫ����һ�¡� |
| pluginParam | PluginParam | 否 | ָ����װ�������Ĳ�����Ĭ��ֵ������ [PluginParam](arkts-ability-installer-pluginparam-i-sys.md#PluginParam) ��Ĭ��ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_PLUGIN_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified hostBundleName cannot be found or the bundle is not installed<br/>by the specified user. |
| [17700004](../../errorcode-universal.md#17700004-The) | The userId is invalid. |
| [17700010](../../errorcode-universal.md#17700010-Failed) | Failed to install the plugin because the plugin fails to be parsed. |
| [17700011](../../errorcode-universal.md#17700011-Failed) | Failed to install the plugin because the plugin signature fails to be<br/>verified. |
| [17700012](../../errorcode-universal.md#17700012-Failed) | Failed to install the plugin because the HSP path is invalid or the HSP is<br/>too large. |
| [17700015](../../errorcode-universal.md#17700015-Failed) | Failed to install the plugin because they have different configuration<br/>information. |
| [17700016](../../errorcode-universal.md#17700016-Failed) | Failed to install the plugin because of insufficient system disk space. |
| [17700017](../../errorcode-universal.md#17700017-Failed) | Failed to install the plugin since the version of the plugin to install is<br/>too early. |
| [17700048](../../errorcode-universal.md#17700048-Failed) | Failed to install the plugin because the code signature verification is<br/>failed. |
| [17700052](../../errorcode-universal.md#17700052-Failed) | Failed to install the plugin because debug bundle cannot be installed under<br/>non-developer mode. |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the plugin because a plugin with the same<br/><br/>bundle name but different signature information exists on the device. |
| [17700087](../../errorcode-universal.md#17700087-Failed) | Failed to install the plugin because the current device does not support<br/>plugin. |
| [17700088](../../errorcode-universal.md#17700088-Failed) | Failed to install the plugin because the host application lacks<br/>ohos.permission.kernel.SUPPORT_PLUGIN. |
| [17700089](../../errorcode-universal.md#17700089-Failed) | Failed to install the plugin because the plugin id fails to be parsed. |
| [17700090](../../errorcode-universal.md#17700090-Failed) | Failed to install the plugin because the plugin id fails to be verified. |
| [17700091](../../errorcode-universal.md#17700091-Failed) | Failed to install the plugin because the plugin name is same as host bundle<br/>name. |

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

��ָ���û��°�װָ��bundleName��Ӧ�á�ʹ��Promise�첽�ص���

> **˵����**
>
> �ýӿڲ�֧�ְ�װ[ǩ��֤��ķַ�����](arkts-ability-applicationinfo-i.md#ApplicationInfo)Ϊenterprise��enterprise_mdm��
> enterprise_normal��Ӧ�á�

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��Ҫ��װӦ�õİ����� |
| userId | number | 否 | ��Ҫ��װӦ�õ��û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��userId��Ҫ����0��Ĭ��ֵ�����÷������û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName cannot be found or the bundle is not installed by<br/>the specified user. |
| [17700004](../../errorcode-universal.md#17700004-The) | The userId is invalid. |
| [17700071](../../errorcode-universal.md#17700071-It) | It is not allowed to install the enterprise bundle. |
| [17700058](../../errorcode-universal.md#17700058-Failed) | Failed to install the HAP because this application is prohibited<br/><br/>from being installed on this device or by specified users.&lt;br&gt;**适用版本：** 14+ |

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

�ع�Ӧ�õ����ΰ�װʱ��״̬��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ���ָ�Ӧ�õİ����� |
| installParam | InstallParam | 是 | ָ����װ��������������� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)���ع�Ӧ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or '<br/>ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the HAP because an application with the same<br/><br/>bundle name but different signature information exists on the device.&lt;br&gt;**适用版本：** 13+ |
| [17700058](../../errorcode-universal.md#17700058-Failed) | Failed to install the HAP because this application is prohibited<br/><br/>from being installed on this device or by specified users.&lt;br&gt;**适用版本：** 14+ |

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

�ع�Ӧ�õ����ΰ�װʱ��״̬��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ���ָ�Ӧ�õİ����� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)���ع�Ӧ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or '<br/>ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the HAP because an application with the same<br/><br/>bundle name but different signature information exists on the device.&lt;br&gt;**适用版本：** 13+ |
| [17700058](../../errorcode-universal.md#17700058-Failed) | Failed to install the HAP because this application is prohibited<br/><br/>from being installed on this device or by specified users.&lt;br&gt;**适用版本：** 14+ |

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

�ع�Ӧ�õ����ΰ�װʱ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.RECOVER_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ж��Ӧ�õİ����� |
| installParam | InstallParam | 否 | ָ����װ���������������Ĭ��ֵ������[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)��Ĭ��ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_BUNDLE' or '<br/>ohos.permission.RECOVER_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the HAP because an application with the same<br/><br/>bundle name but different signature information exists on the device.&lt;br&gt;**适用版本：** 13+ |
| [17700058](../../errorcode-universal.md#17700058-Failed) | Failed to install the HAP because this application is prohibited<br/><br/>from being installed on this device or by specified users.&lt;br&gt;**适用版本：** 14+ |

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

���ݸ�����bundleName��moduleNamesɾ����չ��Դ��ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫɾ����չ��Դ��Ӧ�����ơ� |
| moduleNames | Array&lt;string&gt; | 是 | Ҫɾ����չ��Դ��moduleNames�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700302](../../errorcode-universal.md#17700302-RemoveExtResource) | RemoveExtResource failed due to module does not exist. |

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

ж��Ӧ�á�ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ж��Ӧ�õİ����� |
| installParam | InstallParam | 是 | ָ����װ��������������� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��ж��Ӧ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700020](../../errorcode-universal.md#17700020-The) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../../errorcode-universal.md#17700040-The) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../../errorcode-universal.md#17700045-Failed) | Failed to uninstall the HAP because uninstall is not allowed by the<br/>enterprise device management. |
| [17700067](../../errorcode-universal.md#17700067-Failed) | Failed to uninstall the HAP because uninstalling the native package<br/>failed.&lt;br&gt;**适用版本：** 12+ |
| [17700060](../../errorcode-universal.md#17700060-The) | The specified application cannot be uninstalled.&lt;br&gt;**适用版本：** 13+ |
| [17700062](../../errorcode-universal.md#17700062-Failed) | Failed to uninstall the app because the app is locked.&lt;br&gt;**适用版本：** 15+ |

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

ж��Ӧ�á�ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ж��Ӧ�õİ����� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��ж��Ӧ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700020](../../errorcode-universal.md#17700020-The) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../../errorcode-universal.md#17700040-The) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../../errorcode-universal.md#17700045-Failed) | Failed to uninstall the HAP because uninstall is not allowed by the<br/>enterprise device management. |
| [17700067](../../errorcode-universal.md#17700067-Failed) | Failed to uninstall the HAP because uninstalling the native package<br/>failed.&lt;br&gt;**适用版本：** 12+ |
| [17700060](../../errorcode-universal.md#17700060-The) | The specified application cannot be uninstalled.&lt;br&gt;**适用版本：** 13+ |

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

ж��Ӧ�á�ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ж��Ӧ�õİ����� |
| installParam | InstallParam | 否 | ָ����װ���������������Ĭ��ֵ������[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)��Ĭ��ֵ<br/>�� [since 15] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700020](../../errorcode-universal.md#17700020-The) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700040](../../errorcode-universal.md#17700040-The) | The specified bundle is a shared bundle and cannot be uninstalled. |
| [17700045](../../errorcode-universal.md#17700045-Failed) | Failed to uninstall the HAP because uninstall is not allowed by the<br/>enterprise device management. |
| [17700067](../../errorcode-universal.md#17700067-Failed) | Failed to uninstall the HAP because uninstalling the native package<br/>failed.&lt;br&gt;**适用版本：** 12+ |
| [17700060](../../errorcode-universal.md#17700060-The) | The specified application cannot be uninstalled.&lt;br&gt;**适用版本：** 13+ |
| [17700062](../../errorcode-universal.md#17700062-Failed) | Failed to uninstall the app because the app is locked.&lt;br&gt;**适用版本：** 15+ |

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

ж��һ����������ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uninstallParam | UninstallParam | 是 | ������ж����ָ���Ĳ�����Ϣ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��ж��Ӧ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700020](../../errorcode-universal.md#17700020-The) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700037](../../errorcode-universal.md#17700037-The) | The version of shared bundle is dependent on other applications. |
| [17700038](../../errorcode-universal.md#17700038-The) | The specified shared bundle does not exist. |

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

ж��һ����������ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uninstallParam | UninstallParam | 是 | ������ж����ָ���Ĳ�����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700020](../../errorcode-universal.md#17700020-The) | The specified bundle is a pre-installed bundle and cannot be uninstalled. |
| [17700037](../../errorcode-universal.md#17700037-The) | The version of shared bundle is dependent on other applications. |
| [17700038](../../errorcode-universal.md#17700038-The) | The specified shared bundle does not exist. |

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

����ж��������Ԥ��Ӧ�á�ʹ��Promise�첽�ص���

**起始版本：** 24

**需要权限：** ohos.permission.UNINSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleNames | Array&lt;string&gt; | 是 | ��ж�ص�Ӧ�õİ����б��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |

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

Ӧ��ж�ز����ʹ��Promise�첽�ص���

**起始版本：** 19

**需要权限：** ohos.permission.UNINSTALL_PLUGIN_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostBundleName | string | 是 | ��ж�ز����Ӧ�ð����� |
| pluginBundleName | string | 是 | ����İ����� |
| pluginParam | PluginParam | 否 | ָ��ж�ز������Ĳ�����Ĭ��ֵ������ [PluginParam](arkts-ability-installer-pluginparam-i-sys.md#PluginParam) ��Ĭ��ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.UNINSTALL_PLUGIN_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The user id is invalid. |
| [17700092](../../errorcode-universal.md#17700092-Failed) | Failed to uninstall the plugin because the specified plugin is not found. |

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

��Ԥ��Ӧ�ý���ж�ظ��£��ָ������ΰ�װʱ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.INSTALL_BUNDLE or ohos.permission.UNINSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ж�ظ���Ӧ�õİ����� |
| installParam | InstallParam | 否 | ָ��ж�ظ������������������Ĭ��ֵ������[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)��Ĭ��ֵ������<br/>userId�޷�ָ�������ñ��ӿڽ��������Ѱ�װ��ӦӦ�õ��û�����ж�ظ��²����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700045](../../errorcode-universal.md#17700045-Failed) | Failed to uninstall because enterprise device management disallow uninstall. |
| [17700057](../../errorcode-universal.md#17700057-Failed) | Failed to uninstall updates because the HAP is not pre-installed. |
| [17700060](../../errorcode-universal.md#17700060-The) | The specified application cannot be uninstalled.&lt;br&gt;**适用版本：** 13+ |
| [17700067](../../errorcode-universal.md#17700067-Failed) | Failed to uninstall the HAP because uninstalling the native package<br/>failed.&lt;br&gt;**适用版本：** 13+ |
| [17700073](../../errorcode-universal.md#17700073-Failed) | Failed to install the HAP because an application with the same<br/><br/>bundle name but different signature information exists on the device.&lt;br&gt;**适用版本：** 13+ |

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

���µ�ǰӦ�ã�������ҵ�豸�ϵ���ҵMDMӦ�õ��ã��Ҵ����hapFilePaths�е�hap���붼���ڵ�ǰӦ�á�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_SELF_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | 是 | �洢Ӧ�ó������·����·��Ӧ���ǵ�ǰӦ�ó����д��HAP������Ŀ¼���������·����һ��Ŀ¼ʱ�� ��Ŀ¼��ֻ�ܷ�ͬһ��Ӧ�õ�HAP������ЩHAP��ǩ<br/>����Ҫ����һ�¡� |
| installParam | InstallParam | 是 | ָ����װ��������������� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)����װӦ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature;<br/>4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3<br/>000. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700010](../../errorcode-universal.md#17700010-Failed) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../../errorcode-universal.md#17700011-Failed) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../../errorcode-universal.md#17700012-Failed) | Failed to install the HAP because the HAP path is invalid or the HAP is too<br/>large. |
| [17700015](../../errorcode-universal.md#17700015-Failed) | Failed to install the HAPs because they have different configuration<br/>information. |
| [17700016](../../errorcode-universal.md#17700016-Failed) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../../errorcode-universal.md#17700017-Failed) | Failed to install the HAP since the version of the HAP to install is too<br/>early. |
| [17700018](../../errorcode-universal.md#17700018-Failed) | Failed to install because the dependent module does not exist. |
| [17700039](../../errorcode-universal.md#17700039-Failed) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../../errorcode-universal.md#17700041-Failed) | Failed to install because enterprise device management disallow install. |
| [17700042](../../errorcode-universal.md#17700042-Failed) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../../errorcode-universal.md#17700043-Failed) | Failed to install the HAP because of low APL in the non-system data proxy<br/>(required APL: system_basic or system_core). |
| [17700044](../../errorcode-universal.md#17700044-Failed) | Failed to install the HAP because the isolationMode configured is not<br/>supported. |
| [17700047](../../errorcode-universal.md#17700047-Failed) | Failed to install the HAP because the VersionCode to be updated is not<br/>greater than the current VersionCode. |
| [17700048](../../errorcode-universal.md#17700048-Failed) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../../errorcode-universal.md#17700049-Failed) | Failed to install the HAP because the bundleName is different from the<br/>bundleName of the caller application. |
| [17700050](../../errorcode-universal.md#17700050-Failed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be<br/>installed on non-enterprise device. |
| [17700051](../../errorcode-universal.md#17700051-Failed) | Failed to install the HAP because the distribution type of caller<br/>application is not enterprise_mdm. |

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

���µ�ǰӦ�ã�������ҵ�豸�ϵ���ҵMDMӦ�õ��ã��Ҵ����hapFilePaths�е�hap���붼���ڵ�ǰӦ�á�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_SELF_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | 是 | �洢Ӧ�ó������·����·��Ӧ���ǵ�ǰӦ�ó����д��HAP������Ŀ¼���������·����һ��Ŀ¼ʱ�� ��Ŀ¼��ֻ�ܷ�ͬһ��Ӧ�õ�HAP������ЩHAP��ǩ<br/>����Ҫ����һ�¡� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)����װӦ�óɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2<br/>. Incorrect parameter types. |
| [17700010](../../errorcode-universal.md#17700010-Failed) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../../errorcode-universal.md#17700011-Failed) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../../errorcode-universal.md#17700012-Failed) | Failed to install the HAP because the HAP path is invalid or the HAP is too<br/>large. |
| [17700015](../../errorcode-universal.md#17700015-Failed) | Failed to install the HAPs because they have different configuration<br/>information. |
| [17700016](../../errorcode-universal.md#17700016-Failed) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../../errorcode-universal.md#17700017-Failed) | Failed to install the HAP since the version of the HAP to install is too<br/>early. |
| [17700018](../../errorcode-universal.md#17700018-Failed) | Failed to install because the dependent module does not exist. |
| [17700039](../../errorcode-universal.md#17700039-Failed) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../../errorcode-universal.md#17700041-Failed) | Failed to install because enterprise device management disallow install. |
| [17700042](../../errorcode-universal.md#17700042-Failed) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../../errorcode-universal.md#17700043-Failed) | Failed to install the HAP because of low APL in the non-system data proxy<br/>(required APL: system_basic or system_core). |
| [17700044](../../errorcode-universal.md#17700044-Failed) | Failed to install the HAP because the isolationMode configured is not<br/>supported. |
| [17700047](../../errorcode-universal.md#17700047-Failed) | Failed to install the HAP because the VersionCode to be updated is not<br/>greater than the current VersionCode. |
| [17700048](../../errorcode-universal.md#17700048-Failed) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../../errorcode-universal.md#17700049-Failed) | Failed to install the HAP because the bundleName is different from the<br/>bundleName of the caller application. |
| [17700050](../../errorcode-universal.md#17700050-Failed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be<br/>installed on non-enterprise device. |
| [17700051](../../errorcode-universal.md#17700051-Failed) | Failed to install the HAP because the distribution type of caller<br/>application is not enterprise_mdm. |

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

���µ�ǰӦ�ã�������ҵ�豸�ϵ���ҵMDMӦ�õ��ã��Ҵ����hapFilePaths�е�hap���붼���ڵ�ǰӦ�á�ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.INSTALL_SELF_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePaths | Array&lt;string&gt; | 是 | �洢Ӧ�ó������·����·��Ӧ���ǵ�ǰӦ�ó����д��HAP������Ŀ¼���������·����һ��Ŀ¼ʱ�� ��Ŀ¼��ֻ�ܷ�ͬһ��Ӧ�õ�HAP������ЩHAP��ǩ<br/>����Ҫ����һ�¡� |
| installParam | InstallParam | 否 | ָ����װ���������������Ĭ��ֵ������[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)��Ĭ��ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Calling) | Calling interface without permission 'ohos.permission.INSTALL_SELF_BUNDLE'. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter hapFiles is needed for code signature;<br/>4. The size of specifiedDistributionType is greater than 128; 5. The size of additionalInfo is greater than 3<br/>000. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700010](../../errorcode-universal.md#17700010-Failed) | Failed to install the HAP because the HAP fails to be parsed. |
| [17700011](../../errorcode-universal.md#17700011-Failed) | Failed to install the HAP because the HAP signature fails to be verified. |
| [17700012](../../errorcode-universal.md#17700012-Failed) | Failed to install the HAP because the HAP path is invalid or the HAP is too<br/>large. |
| [17700015](../../errorcode-universal.md#17700015-Failed) | Failed to install the HAPs because they have different configuration<br/>information. |
| [17700016](../../errorcode-universal.md#17700016-Failed) | Failed to install the HAP because of insufficient system disk space. |
| [17700017](../../errorcode-universal.md#17700017-Failed) | Failed to install the HAP since the version of the HAP to install is too<br/>early. |
| [17700018](../../errorcode-universal.md#17700018-Failed) | Failed to install because the dependent module does not exist. |
| [17700039](../../errorcode-universal.md#17700039-Failed) | Failed to install because disallow install a shared bundle by hapFilePaths. |
| [17700041](../../errorcode-universal.md#17700041-Failed) | Failed to install because enterprise device management disallow install. |
| [17700042](../../errorcode-universal.md#17700042-Failed) | Failed to install the HAP because of incorrect URI in the data proxy. |
| [17700043](../../errorcode-universal.md#17700043-Failed) | Failed to install the HAP because of low APL in the non-system data proxy<br/>(required APL: system_basic or system_core). |
| [17700044](../../errorcode-universal.md#17700044-Failed) | Failed to install the HAP because the isolationMode configured is not<br/>supported. |
| [17700047](../../errorcode-universal.md#17700047-Failed) | Failed to install the HAP because the VersionCode to be updated is not<br/>greater than the current VersionCode. |
| [17700048](../../errorcode-universal.md#17700048-Failed) | Failed to install the HAP because the code signature verification is failed. |
| [17700049](../../errorcode-universal.md#17700049-Failed) | Failed to install the HAP because the bundleName is different from the<br/>bundleName of the caller application. |
| [17700050](../../errorcode-universal.md#17700050-Failed) | Failed to install the HAP because enterprise normal/MDM bundle cannot be<br/>installed on non-enterprise device. |
| [17700051](../../errorcode-universal.md#17700051-Failed) | Failed to install the HAP because the distribution type of caller<br/>application is not enterprise_mdm. |

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

