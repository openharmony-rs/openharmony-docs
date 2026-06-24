# setSandboxAppConfig

## setSandboxAppConfig

```TypeScript
function setSandboxAppConfig(configInfo: string): Promise<void>
```

设置沙箱应用配置信息，配置信息为JSON字符串格式，具体内容由应用自行设置。调用成功后，沙箱应用将按照配置信息运行。使用Promise异步回调。

该接口用于设置沙箱应用的配置信息，以便应用按需传递自定义参数。

**起始版本：** 11

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configInfo | string | 是 | 沙箱应用配置信息。长度范围[0, 4194304)字节，超出此范围抛出错误码19100001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100007](../../errorcode-universal.md#19100007-No) | No permission to call this API,<br/>which is available only for non-DLP sandbox applications. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |
| [19100018](../../errorcode-universal.md#19100018-The) | The application is not authorized. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.setSandboxAppConfig('configInfo').then((configInfo) => { // 设置沙箱应用配置信息。
  console.info('configInfo：', configInfo);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```

