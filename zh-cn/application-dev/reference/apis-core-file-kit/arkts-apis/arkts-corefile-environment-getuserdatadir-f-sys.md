# getUserDataDir（系统接口）

## 导入模块

```TypeScript
import { Environment } from '@kit.CoreFileKit';
```

<a id="getuserdatadir"></a>
## getUserDataDir

```TypeScript
function getUserDataDir(): Promise<string>
```

异步方法获取公共文件根目录，使用promise异步回调。

**起始版本：** 8

<!--Device-Environment-function getUserDataDir(): Promise<string>--><!--Device-Environment-function getUserDataDir(): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.Environment

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 返回公共文件根目录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |


<a id="getuserdatadir-1"></a>
## getUserDataDir

```TypeScript
function getUserDataDir(callback: AsyncCallback<string>): void
```

异步方法获取公共文件根目录，使用callback异步回调。

**起始版本：** 8

<!--Device-Environment-function getUserDataDir(callback: AsyncCallback<string>): void--><!--Device-Environment-function getUserDataDir(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.Environment

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 异步获取公共文件根目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

