# grantUriPermission（系统接口）

## grantUriPermission

```TypeScript
function grantUriPermission(
    uri: string,
    flag: wantConstant.Flags,
    targetBundleName: string,
    callback: AsyncCallback<number>
  ): void
```

授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考 [应用文件分享](../../../file-management/share-app-file.md)。使用callback异步回调。 该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 > **说明：** > > - 当应用拥有ohos.permission.PROXY_AUTHORIZATION_URI权限时, 可以授权不属于自身但具有访问权限的URI。如果不具备该权限，则仅支持授权属于自身的URI。 > > - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证 > 其功能。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PROXY_AUTHORIZATION_URI

<!--Device-uriPermissionManager-function grantUriPermission(    uri: string,    flag: wantConstant.Flags,    targetBundleName: string,    callback: AsyncCallback<number>  ): void--><!--Device-uriPermissionManager-function grantUriPermission(    uri: string,    flag: wantConstant.Flags,    targetBundleName: string,    callback: AsyncCallback<number>  ): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指向文件的URI，scheme固定为"file"，参考[FileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。 |
| flag | wantConstant.Flags | 是 | URI的读权限或写权限。 |
| targetBundleName | string | 是 | 被授权URI的应用包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 回调函数。返回0表示有权限，返回-1表示无权限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000060](../errorcode-ability.md#16000060-不支持沙箱应用授权uri) | A sandbox application cannot grant URI permission. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [16000058](../errorcode-ability.md#16000058-指定的uri-flag无效) | Invalid URI flag. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |

## 示例

```TypeScript
import { uriPermissionManager, wantConstant } from '@kit.AbilityKit';
import { fileIo, fileUri } from '@kit.CoreFileKit';

let targetBundleName = 'com.example.test_case1';
let path = 'file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir';
// 创建目录
fileIo.mkdir(path, (err) => {
  if (err) {
    console.error(`mkdir failed, err code: ${err.code}, err msg: ${err.message}.`);
    return;
  }
});
console.info(`mkdir success.`);
let uri = fileUri.getUriFromPath(path);
// 授权URI给指定应用
uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName,
  (error) => {
    if (error && error.code !== 0) {
      console.error(`grantUriPermission failed, err code: ${error.code}, err msg: ${error.message}.`);
      return;
    }
    console.info(`grantUriPermission success.`);
  });
});
```


## grantUriPermission

```TypeScript
function grantUriPermission(
    uri: string,
    flag: wantConstant.Flags,
    targetBundleName: string,
    callback: AsyncCallback<void>
  ): void
```

授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考 [应用文件分享](../../../file-management/share-app-file.md)。使用callback异步回调。 该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 > **说明：** > > - 当应用拥有ohos.permission.PROXY_AUTHORIZATION_URI权限时, 可以授权不属于自身但具有访问权限的URI。如果不具备该权限，则仅支持授权属于自身的URI。 > > - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证 > 其功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PROXY_AUTHORIZATION_URI

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uriPermissionManager-function grantUriPermission(    uri: string,    flag: wantConstant.Flags,    targetBundleName: string,    callback: AsyncCallback<void>  ): void--><!--Device-uriPermissionManager-function grantUriPermission(    uri: string,    flag: wantConstant.Flags,    targetBundleName: string,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指向文件的URI，scheme固定为"file"，参考[FileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。 |
| flag | wantConstant.Flags | 是 | URI的读权限或写权限。 |
| targetBundleName | string | 是 | 被授权URI的应用包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。返回0表示有权限，返回-1表示无权限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [16000060](../errorcode-ability.md#16000060-不支持沙箱应用授权uri) | A sandbox application cannot grant URI permission. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [16000058](../errorcode-ability.md#16000058-指定的uri-flag无效) | Invalid URI flag. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { uriPermissionManager, wantConstant } from '@kit.AbilityKit';
import { fileIo, fileUri } from '@kit.CoreFileKit';

let targetBundleName = 'com.example.test_case1'
let path = 'file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir';
fileIo.mkdir(path, (err) => {
  if (err) {
    console.error(`mkdir failed, err code: ${err.code}, err msg: ${err.message}.`);
  } else {
    console.info(`mkdir success.`);
  }
});
let uri = fileUri.getUriFromPath(path);
uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName,
  (error) => {
    if (error && error.code !== 0) {
      console.error(`grantUriPermission failed, err code: ${error.code}, err msg: ${error.message}.`);
      return;
    }
    console.info(`grantUriPermission success.`);
  });
```


## grantUriPermission

```TypeScript
function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string): Promise<number>
```

授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考 [应用文件分享](../../../file-management/share-app-file.md)。使用Promise异步回调。 该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 > **说明：** > > - 当应用拥有ohos.permission.PROXY_AUTHORIZATION_URI权限时, 可以授权不属于自身但具有访问权限的URI。如果不具备该权限，则仅支持授权属于自身的URI。 > > - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证 > 其功能。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PROXY_AUTHORIZATION_URI

<!--Device-uriPermissionManager-function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string): Promise<number>--><!--Device-uriPermissionManager-function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指向文件的URI，scheme固定为"file"，参考[FileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。 |
| flag | wantConstant.Flags | 是 | URI的读权限或写权限。 |
| targetBundleName | string | 是 | 被授权URI的应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回0表示有权限，返回-1表示无权限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000060](../errorcode-ability.md#16000060-不支持沙箱应用授权uri) | A sandbox application cannot grant URI permission. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [16000058](../errorcode-ability.md#16000058-指定的uri-flag无效) | Invalid URI flag. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |

## 示例

```TypeScript
import { uriPermissionManager, wantConstant } from '@kit.AbilityKit';
import { fileIo, fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = 'com.example.test_case1'
let path = 'file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir';

// 创建目录
fileIo.mkdir(path, (err) => {
  if (err) {
    console.error(`mkdir failed, err code: ${err.code}, err msg: ${err.message}.`);
    return;
  }
  console.info(`mkdir success.`);
  let uri = fileUri.getUriFromPath(path);
  // 授权URI给指定应用
  uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName)
    .then((data) => {
      console.info(`grantUriPermission succeeded, data: ${JSON.stringify(data)}.`);
    }).catch((err: BusinessError) => {
    console.error(`grantUriPermission failed, err code: ${err.code}, err msg: ${err.message}.`);
  });
});
```


## grantUriPermission

```TypeScript
function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string): Promise<void>
```

Grant URI to another application

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PROXY_AUTHORIZATION_URI

<!--Device-uriPermissionManager-function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string): Promise<void>--><!--Device-uriPermissionManager-function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | File URI. |
| flag | wantConstant.Flags | 是 | wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION or wantConstant.Flags.FLAG_AUTH_PERSISTABLE_URI_PERMISSION. |
| targetBundleName | string | 是 | Indicates the bundle name of authorization target. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [16000060](../errorcode-ability.md#16000060-不支持沙箱应用授权uri) | A sandbox application cannot grant URI permission. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [16000058](../errorcode-ability.md#16000058-指定的uri-flag无效) | Invalid URI flag. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { uriPermissionManager, wantConstant } from '@kit.AbilityKit';
import { fileIo, fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = 'com.example.test_case1'
let path = 'file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir';

fileIo.mkdir(path, (err) => {
  if (err) {
    console.error(`mkdir failed, err code: ${err.code}, err msg: ${err.message}.`);
  } else {
    console.info(`mkdir succeed.`);
  }
});
let uri = fileUri.getUriFromPath(path);
uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName)
  .then((data) => {
    console.info(`Verification succeeded, data: ${data}.`);
  }).catch((err: BusinessError<void>): void => {
  console.error(`Verification failed, err code: ${err.code}, err msg: ${err.message}.`);
});
```


## grantUriPermission

```TypeScript
function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string, appCloneIndex: int): Promise<void>
```

授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考 [应用文件分享](../../../file-management/share-app-file.md)。使用Promise异步回调。 该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 > **说明：** > > - 当应用拥有ohos.permission.PROXY_AUTHORIZATION_URI权限时, 可以授权不属于自身但具有访问权限的URI。如果不具备该权限，则仅支持授权属于自身的URI。 > > - 该接口支持给分身应用授权，需要指定目标应用的应用包名和分身索引。 > > - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证 > 其功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PROXY_AUTHORIZATION_URI

<!--Device-uriPermissionManager-function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string, appCloneIndex: int): Promise<void>--><!--Device-uriPermissionManager-function grantUriPermission(uri: string, flag: wantConstant.Flags, targetBundleName: string, appCloneIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指向文件的URI，scheme固定为"file"，参考[FileUri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。 |
| flag | wantConstant.Flags | 是 | URI的读权限或写权限。 |
| targetBundleName | string | 是 | 被授权应用的应用包名。 |
| appCloneIndex | int | 是 | 被授权应用的分身索引，有效范围为[0, 1000], 取值为0时表示主应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |
| [16000081](../errorcode-ability.md#16000081-获取目标应用信息失败) | Failed to obtain the target application information. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000060](../errorcode-ability.md#16000060-不支持沙箱应用授权uri) | A sandbox application cannot grant URI permission. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [16000058](../errorcode-ability.md#16000058-指定的uri-flag无效) | Invalid URI flag. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { AbilityConstant, UIAbility, Want, wantConstant, uriPermissionManager } from '@kit.AbilityKit';
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    let targetBundleName: string = 'com.example.demo1';
    let filePath: string = this.context.filesDir + "/test.txt";
    let uri: string = fileUri.getUriFromPath(filePath);
    // 授权URI权限至主应用程序
    try {
      let appCloneIndex: number = 0;
      uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName,
        appCloneIndex)
        .then(() => {
          console.info('grantUriPermission succeeded.');
        }).catch((error: BusinessError) => {
        console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
    }

    // 授权URI权限至分身应用程序
    try {
      let appCloneIndex: number = 1;
      uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName,
        appCloneIndex)
        .then(() => {
          console.info('grantUriPermission succeeded.');
        }).catch((error: BusinessError) => {
        console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { AbilityConstant, UIAbility, Want, wantConstant, uriPermissionManager } from '@kit.AbilityKit';
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    let targetBundleName: string = 'com.example.demo1';
    let filePath: string = this.context.filesDir + "/test.txt";
    let uri: string = fileUri.getUriFromPath(filePath);
    // 授权URI权限至主应用程序
    try {
      let appCloneIndex: int = 0;
      uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName,
        appCloneIndex)
        .then(() => {
          console.info('grantUriPermission succeeded.');
        }).catch((error: BusinessError<void>): void => {
        console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
    }

    // 授权URI权限至分身应用程序
    try {
      let appCloneIndex: int = 1;
      uriPermissionManager.grantUriPermission(uri, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetBundleName,
        appCloneIndex)
        .then(() => {
          console.info('grantUriPermission succeeded.');
        }).catch((error: BusinessError<void>): void => {
        console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`grantUriPermission failed. error: ${JSON.stringify(error)}.`);
    }
  }
}
```

