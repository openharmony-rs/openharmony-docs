# revokeUriPermission（系统接口）

## 导入模块

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';
```

## revokeUriPermission

```TypeScript
function revokeUriPermission(uri: string, targetBundleName: string, callback: AsyncCallback<number>): void
```

撤销授权指定应用的URI。使用callback异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。

> **说明：**  
>  
> - 允许应用撤销自身获得的其他应用URI权限，或授权给其他应用的URI权限。  
>  
> - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证  
> 其功能。

**起始版本：** 10

**需要权限：** 
- API版本10 - 11：ohos.permission.PROXY_AUTHORIZATION_URI

<!--Device-uriPermissionManager-function revokeUriPermission(uri: string, targetBundleName: string, callback: AsyncCallback<number>): void--><!--Device-uriPermissionManager-function revokeUriPermission(uri: string, targetBundleName: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指向文件的URI，scheme固定为"file"，参考[FileUri](@ohos.file.fileuri:fileUri.FileUri#constructor)。 |
| targetBundleName | string | 是 | 被撤销授权uri的应用包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。返回0表示有权限，返回-1表示无权限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 10 - 11 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |

**示例：**

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';

let targetBundleName = 'com.example.test_case2';
let uri = "file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir";

// 撤销指定应用的URI权限
uriPermissionManager.revokeUriPermission(uri, targetBundleName, (error) => {
  if (error && error.code !== 0) {
    console.error(`revokeUriPermission failed. Code: ${error.code}, message: ${error.message}.`);
    return;
  }
  console.info('revokeUriPermission success');
});

```


## revokeUriPermission

```TypeScript
function revokeUriPermission(uri: string, targetBundleName: string): Promise<number>
```

撤销授权指定应用的URI。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。

> **说明：**  
>  
> - 允许应用撤销自身获得的其他应用URI权限，或授权给其他应用的URI权限。  
>  
> - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证  
> 其功能。

**起始版本：** 10

**需要权限：** 
- API版本10 - 11：ohos.permission.PROXY_AUTHORIZATION_URI

<!--Device-uriPermissionManager-function revokeUriPermission(uri: string, targetBundleName: string): Promise<number>--><!--Device-uriPermissionManager-function revokeUriPermission(uri: string, targetBundleName: string): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指向文件的URI，scheme固定为"file"，参考[FileUri](@ohos.file.fileuri:fileUri.FileUri#constructor)。 |
| targetBundleName | string | 是 | 被授权URI的应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回0表示有权限，返回-1表示无权限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 10 - 11 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |

**示例：**

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = 'com.example.test_case2';
let uri = 'file://com.example.test_case1/data/storage/el2/base/haps/entry_test/files/newDir';

// 撤销指定应用的URI权限
uriPermissionManager.revokeUriPermission(uri, targetBundleName)
  .then((data) => {
    console.info(`Verification success, data: ${JSON.stringify(data)}.`);
  }).catch((error: BusinessError) => {
  console.error(`Verification failed, err code: ${error.code}, err msg: ${error.message}.`);
});

```


## revokeUriPermission

```TypeScript
function revokeUriPermission(uri: string, targetBundleName: string, appCloneIndex: number): Promise<void>
```

撤销授权指定应用的URI。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。

> **说明：**  
>  
> - 允许应用撤销自身获得的其他应用URI权限，或授权给其他应用的URI权限。  
>  
> - 该接口支持撤销授权给分身应用的URI权限，需要指定目标应用的应用包名和分身索引。  
>  
> - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证  
> 其功能。

**起始版本：** 14

<!--Device-uriPermissionManager-function revokeUriPermission(uri: string, targetBundleName: string, appCloneIndex: int): Promise<void>--><!--Device-uriPermissionManager-function revokeUriPermission(uri: string, targetBundleName: string, appCloneIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指向文件的URI，scheme固定为"file"，参考[FileUri](@ohos.file.fileuri:fileUri.FileUri#constructor)。 |
| targetBundleName | string | 是 | 被授权应用的应用包名。 |
| appCloneIndex | number | 是 | 被授权应用的分身索引，有效范围为[0, 1000], 取值为0时表示主应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000059](../errorcode-ability.md#16000059-指定的uri类型无效) | Invalid URI type. |
| [16000081](../errorcode-ability.md#16000081-获取目标应用信息失败) | Failed to obtain the target application information. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |

**示例：**

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
    // 撤销主应用的URI权限
    try {
      let appCloneIndex: number = 0;
      uriPermissionManager.revokeUriPermission(uri, targetBundleName, appCloneIndex)
        .then(() => {
          console.info('revokeUriPermission succeeded.');
        }).catch((error: BusinessError) => {
        console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
    }

    // 撤销分身应用的URI权限
    try {
      let appCloneIndex: number = 1;
      uriPermissionManager.revokeUriPermission(uri, targetBundleName, appCloneIndex)
        .then(() => {
          console.info('revokeUriPermission succeeded.');
        }).catch((error: BusinessError) => {
        console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
      });
    } catch (error) {
      console.error(`revokeUriPermission failed. error: ${JSON.stringify(error)}.`);
    }
  }
}

```

