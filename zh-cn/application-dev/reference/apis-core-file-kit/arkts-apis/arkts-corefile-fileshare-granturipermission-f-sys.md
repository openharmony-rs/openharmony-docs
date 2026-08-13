# grantUriPermission（系统接口）

## grantUriPermission

```TypeScript
function grantUriPermission(
    uri: string,
    bundleName: string,
    flag: wantConstant.Flags,
    callback: AsyncCallback<void>
  ): void
```

为应用授予公共目录文件URI的临时访问权限，使用Callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_MEDIA

<!--Device-fileShare-function grantUriPermission(    uri: string,    bundleName: string,    flag: wantConstant.Flags,    callback: AsyncCallback<void>  ): void--><!--Device-fileShare-function grantUriPermission(    uri: string,    bundleName: string,    flag: wantConstant.Flags,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 公共目录文件URI。 |
| bundleName | string | 是 | 分享目标的包名。 |
| flag | wantConstant.Flags | 是 | 授权的权限，可取wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION或 wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 异步授权之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application |
| 14300001 | IPC error |

## 示例

```TypeScript
import { wantConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

let uri: string =
  'file://docs/storage/Users/currentUser/Document/1.txt'; // 推荐使用系统接口生成URI。fileUri.getUriFromPath('沙箱路径');
let bundleName: string = 'com.demo.test';
try {
  fileShare.grantUriPermission(uri, bundleName, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION |
    wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION, (err: BusinessError) => {
    if (err) {
      console.error(`grantUriPermission failed with error: ${JSON.stringify(err)}`);
      return;
    }
    console.info('grantUriPermission success!');
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`grantUriPermission failed with error: ${JSON.stringify(error)}`);
}
```


## grantUriPermission

```TypeScript
function grantUriPermission(uri: string, bundleName: string, flag: wantConstant.Flags): Promise<void>
```

为应用授予公共目录文件URI的临时访问权限，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_MEDIA

<!--Device-fileShare-function grantUriPermission(uri: string, bundleName: string, flag: wantConstant.Flags): Promise<void>--><!--Device-fileShare-function grantUriPermission(uri: string, bundleName: string, flag: wantConstant.Flags): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 公共目录文件URI。 |
| bundleName | string | 是 | 分享目标的包名。 |
| flag | wantConstant.Flags | 是 | 授权的权限，可取wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION或 wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application |
| 14300001 | IPC error |

## 示例

```TypeScript
import { wantConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

let uri: string =
  'file://docs/storage/Users/currentUser/Document/1.txt'; // 推荐使用系统接口生成URI。fileUri.getUriFromPath('沙箱路径');
let bundleName: string = 'com.demo.test';
try {
  fileShare.grantUriPermission(uri, bundleName, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION |
    wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION).then(() => {
    console.info('grantUriPermission success!');
  }).catch((error: BusinessError) => {
    console.error(`grantUriPermission failed with error: ${JSON.stringify(error)}`);
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`grantUriPermission failed with error: ${JSON.stringify(error)}`);
}
```


## grantUriPermission

```TypeScript
function grantUriPermission(policies: Array<PolicyInfo>, targetBundleName: string, appCloneIndex: int): Promise<void>
```

给应用授予目标文件临时权限，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

<!--Device-fileShare-function grantUriPermission(policies: Array<PolicyInfo>, targetBundleName: string, appCloneIndex: int): Promise<void>--><!--Device-fileShare-function grantUriPermission(policies: Array<PolicyInfo>, targetBundleName: string, appCloneIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policies | Array&lt;[PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)&gt; | 是 | 需要授权URI的策略信息数组。 |
| targetBundleName | string | 是 | 被授权应用的应用包名。 |
| appCloneIndex | int | 是 | 被授权应用的分身索引，取值为0时表示主应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900001 | Operation not permitted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900011 | Out of memory. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function grantUriPermissionExample() {
  try {
    let uri = 'file://docs/storage/Users/currentUser/Documents/1.txt';
    let policyInfo: fileShare.PolicyInfo = {
      uri: uri,
      operationMode: fileShare.OperationMode.CREATE_MODE | fileShare.OperationMode.READ_MODE,
    };
    let policies: Array<fileShare.PolicyInfo> = [policyInfo];

    fileShare.grantUriPermission(policies, 'com.example.myapplicationtest', 0).then(() => {
    }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
      console.error(`grantUriPermission failed. Code: ${err.code}, message: ${err.message}`);
    });
  } catch (error) {
    console.info(`grantUriPermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

