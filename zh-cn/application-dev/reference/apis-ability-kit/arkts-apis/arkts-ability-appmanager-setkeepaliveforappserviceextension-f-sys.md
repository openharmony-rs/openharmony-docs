# setKeepAliveForAppServiceExtension（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## setKeepAliveForAppServiceExtension

```TypeScript
function setKeepAliveForAppServiceExtension(bundleName: string, enabled: boolean): Promise<void>
```

为AppServiceExtensionAbility设置保活或取消保活。使用Promise异步回调。该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。
> **说明：**  
>  
> - 仅当应用安装在userId为1的用户下，且应用中entry类型的HAP的module.json5配置文件中的mainElement字段配置为AppServiceExtensionAbility时，该接口才生效。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_APP_KEEP_ALIVE

<!--Device-appManager-function setKeepAliveForAppServiceExtension(bundleName: string, enabled: boolean): Promise<void>--><!--Device-appManager-function setKeepAliveForAppServiceExtension(bundleName: string, enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要设置保活的应用包名。 |
| enabled | boolean | 是 | 表示是否进行应用保活。true表示保活，false表示不保活。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000081](../errorcode-ability.md#16000081-获取目标应用信息失败) | Failed to obtain the target application information. |
| [16000202](../errorcode-ability.md#16000202-仅支持为appservice类型的extensionability设置保活) | Invalid main element type. |
| [16000203](../errorcode-ability.md#16000203-无法更改appserviceextensionability保活状态) | Cannot change the keep-alive status. |
| [16000204](../errorcode-ability.md#16000204-指定的应用未安装在userid为1的用户下) | The target bundle is not in u1. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = "ohos.samples.keepaliveapp";
  appManager.setKeepAliveForAppServiceExtension(bundleName, true).then(() => {
    console.info(`setKeepAliveForAppServiceExtension success`);
  }).catch((err: BusinessError) => {
    console.error(`setKeepAliveForAppServiceExtension fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] setKeepAliveForAppServiceExtension error: ${code}, ${message}`);
}

```

