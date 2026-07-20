# getSandboxAppConfig

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

<a id="getsandboxappconfig"></a>
## getSandboxAppConfig

```TypeScript
function getSandboxAppConfig(): Promise<string>
```

获取沙箱应用配置信息，使用Promise异步回调。

该接口用于获取沙箱应用的配置信息，便于读取或验证当前的配置状态。

**起始版本：** 11

<!--Device-dlpPermission-function getSandboxAppConfig(): Promise<string>--><!--Device-dlpPermission-function getSandboxAppConfig(): Promise<string>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回沙箱应用配置信息。长度小于4194304字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |
| [19100018](../errorcode-dlp.md#19100018-应用未授权) | The application is not authorized. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getSandboxAppConfig().then((configInfo) => { // 获取沙箱应用配置信息。
  console.info('configInfo', configInfo);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```

