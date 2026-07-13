# DlpConnManager

用于调用registerPlugin和unregisterPlugin接口，在SA（System Ability）中注册或注销回调能力。

> **说明：**
>
> registerPlugin接口将回调能力注册进SA（System Ability），而unregisterPlugin接口将回调能力从SA（System Ability）中注销。

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## constructor

```TypeScript
constructor()
```

[DlpConnManager](arkts-dataprotection-dlpconnmanager-c.md) 实例化时的构造函数。

**起始版本：** 21

**需要权限：** 
- API版本26.0.0+：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE
- API版本21 - 24：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let dlpConnManager: dlpPermission.DlpConnManager = new dlpPermission.DlpConnManager();

```

## registerPlugin

```TypeScript
static registerPlugin(plugin: DlpConnPlugin): number
```

该接口提供将回调注册到SA（System Ability）侧的功能。

> **说明：**
>
> registerPlugin将plugin注册到SA（System Ability）侧，待SA（System Ability）调用。

**起始版本：** 21

**需要权限：** 
- API版本26.0.0+：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE
- API版本21 - 24：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plugin | DlpConnPlugin | 是 | 回调插件对象，用于注册回调能力到SA（System Ability）侧。需要继承DlpConnPlugin接口并实现connectServer方法，以便SA侧调用时能够通过回调返回处理结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 注册结果，返回该回调的唯一标识ID。取值范围为[0, 2&lt;sup&gt;64&lt;/sup&gt;-1]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-加解密出错) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-加解密超时) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-凭据服务错误) | Credential service error. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { Callback } from '@kit.BasicServicesKit';

export default class DataCapsulePlugin implements dlpPermission.DlpConnPlugin {
  private accountId: string;
  private accountName: string;
  constructor() {
    this.accountId = 'accountId'; // 初始化账号信息。
    this.accountName = 'accountName';
  }

  connectServer(requestId: string, requestData: string, callback: Callback<string>): void {
    let callbackJson = JSON.stringify({
      'requestId': requestId,
    });
    callback(callbackJson);
  }
}
  
let pluginId: number = dlpPermission.DlpConnManager.registerPlugin(new DataCapsulePlugin());

```

## unregisterPlugin

```TypeScript
static unregisterPlugin(): void
```

提供将回调从SA（System Ability）侧注销的能力。

该接口可用于应用退出时注销回调释放资源，确保回调能力正确释放。

> **说明：**
>
> unregisterPlugin将plugin从SA（System Ability）侧注销。

**起始版本：** 21

**需要权限：** 
- API版本26.0.0+：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE
- API版本21 - 24：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-加解密出错) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-加解密超时) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-凭据服务错误) | Credential service error. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.DlpConnManager.unregisterPlugin();

```

