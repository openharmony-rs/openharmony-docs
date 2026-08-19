# getSharedDirectoryInfo（系统接口）

## 导入模块

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## getSharedDirectoryInfo

```TypeScript
function getSharedDirectoryInfo(): Promise<Array<SharedDirectoryInfo>>
```

获取所有应用捐献的沙箱目录。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_SHARED_FILE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileShare-function getSharedDirectoryInfo(): Promise<Array<SharedDirectoryInfo>>--><!--Device-fileShare-function getSharedDirectoryInfo(): Promise<Array<SharedDirectoryInfo>>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[SharedDirectoryInfo](arkts-corefile-fileshare-shareddirectoryinfo-i-sys.md)&gt;&gt; | Promise对象，返回所有应用捐献的沙箱目录数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900001 | Operation not permitted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900011 | Out of memory. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function getSharedDirectoryInfo() {
  try {
    fileShare.getSharedDirectoryInfo().then((infos: Array<fileShare.SharedDirectoryInfo>) => {
      infos.forEach((info: fileShare.SharedDirectoryInfo) => {
        console.info(`bundleName=${info.bundleName} path=${info.path} mode=${info.permissionMode}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`getSharedDirectoryInfo err: ${JSON.stringify(err)}`);
    });
  } catch (error) {
    console.error(`getSharedDirectoryInfo error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function getSharedDirectoryInfo() {
  try {
    let sharedInfos = await fileShare.getSharedDirectoryInfo();
    console.info("getSharedDirectoryInfo success.");
    for (let info of sharedInfos) {
      console.info("bundleName=" + info.bundleName + " path=" + info.path + " mode=" + info.permissionMode)
    }
  }
  catch (error) {
    console.error('getSharedDirectoryInfo error, Code: ' + error.code + ', message: ' + error.message);
  }
}
```

