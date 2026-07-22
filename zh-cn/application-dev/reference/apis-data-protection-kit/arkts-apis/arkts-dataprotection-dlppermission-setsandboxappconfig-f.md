# setSandboxAppConfig

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## setSandboxAppConfig

```TypeScript
function setSandboxAppConfig(configInfo: string): Promise<void>
```

设置沙箱应用配置信息，配置信息为JSON字符串格式，具体内容由应用自行设置。调用成功后，沙箱应用将按照配置信息运行。使用Promise异步回调。

该接口用于设置沙箱应用的配置信息，以便应用按需传递自定义参数。

**起始版本：** 11

<!--Device-dlpPermission-function setSandboxAppConfig(configInfo: string): Promise<void>--><!--Device-dlpPermission-function setSandboxAppConfig(configInfo: string): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configInfo | string | 是 | 沙箱应用配置信息。长度不超过2<sup>22</sup>-1字节，超出此范围抛出错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-dlp沙箱应用不允许调用此接口) | No permission to call this API,which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |
| [19100018](../errorcode-dlp.md#19100018-应用未授权) | The application is not authorized. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.setSandboxAppConfig('configInfo').then((configInfo) => { // 设置沙箱应用配置信息。
  console.info('configInfo：', configInfo);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```

