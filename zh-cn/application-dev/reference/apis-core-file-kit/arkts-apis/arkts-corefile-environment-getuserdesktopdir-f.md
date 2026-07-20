# getUserDesktopDir

## 导入模块

```TypeScript
import { Environment } from '@kit.CoreFileKit';
```

<a id="getuserdesktopdir"></a>
## getUserDesktopDir

```TypeScript
function getUserDesktopDir(): string
```

获取当前用户预授权桌面目录的沙箱路径。

**起始版本：** 11

**需要权限：** 
- API版本11：ohos.permission.READ_WRITE_DESKTOP_DIRECTORY

<!--Device-Environment-function getUserDesktopDir(): string--><!--Device-Environment-function getUserDesktopDir(): string-End-->

**系统能力：** SystemCapability.FileManagement.File.Environment.FolderObtain

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回当前用户预授权桌面目录的沙箱路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken.<br>**适用版本：** 11+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getUserDesktopDirExample() {
  try {
    let path = Environment.getUserDesktopDir();
    console.info(`Succeeded in getUserDesktopDir, path is ${path}`);
  } catch (err) {
    console.error(`Failed to getUserDesktopDir. Code: ${err.code}, message: ${err.message}`);
  }
}

```

