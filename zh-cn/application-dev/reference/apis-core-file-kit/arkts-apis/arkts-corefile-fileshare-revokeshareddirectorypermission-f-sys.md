# revokeSharedDirectoryPermission（系统接口）

## revokeSharedDirectoryPermission

```TypeScript
function revokeSharedDirectoryPermission(): Promise<void>
```

撤销应用的捐献目录临时访问权限。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_SHARED_FILE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileShare-function revokeSharedDirectoryPermission(): Promise<void>--><!--Device-fileShare-function revokeSharedDirectoryPermission(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900001 | Operation not permitted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeSharedDirectoryPermission() {
  try {
    fileShare.revokeSharedDirectoryPermission().then(() => {
      console.info('revokeSharedDirectoryPermission success');
    }).catch((err: BusinessError) => {
      console.error(`revokeSharedDirectoryPermission err: ${JSON.stringify(err)}`);
    });
  } catch (error) {
    console.error(`revokeSharedDirectoryPermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeSharedDirectoryPermission() {
  try {
    await fileShare.revokeSharedDirectoryPermission();
    console.info("revokeSharedDirectoryPermission success.");
  }
  catch (error) {
    console.error('revokeSharedDirectoryPermission error, Code: ' + error.code + ', message: ' + error.message);
  }
}
```

