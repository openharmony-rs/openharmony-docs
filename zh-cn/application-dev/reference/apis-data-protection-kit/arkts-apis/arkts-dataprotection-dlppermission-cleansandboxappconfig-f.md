# cleanSandboxAppConfig

## cleanSandboxAppConfig

```TypeScript
function cleanSandboxAppConfig(): Promise<void>
```

清理沙箱应用配置信息。调用成功后，沙箱应用配置将被清除，恢复默认状态。使用Promise异步回调。

该接口用于清理沙箱应用的配置信息，恢复默认状态以防止配置残留影响后续使用。

**起始版本：** 11

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100007](../../errorcode-universal.md#19100007-No) | No permission to call this API,<br/>which is available only for non-DLP sandbox applications. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |
| [19100018](../../errorcode-universal.md#19100018-The) | The application is not authorized. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.cleanSandboxAppConfig().then((configInfo) => { // 清理沙箱应用配置信息。
  console.info('configInfo：', configInfo);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```

