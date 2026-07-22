# setKeepAliveForBundle（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## setKeepAliveForBundle

```TypeScript
function setKeepAliveForBundle(bundleName: string, userId: number, enable: boolean): Promise<void>
```

为指定用户下的应用设置或取消保活。使用Promise异步回调。从API version 18开始，该接口仅在2in1和Wearable设备上生效。对于API version 18之前版本，该接口仅在2in1设备上生效。其他情况下调用该接口将返回错误码801。
> **说明：**  
>  
> - 应用如果需要支持保活，其[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的mainElement必须是UIAbility。只有当  
> mainElement启动后，系统才会执行应用保活操作。  
>  
> - 在2in1设备上，被保活的应用需要在启动后5秒内添加至状态栏。否则，系统将取消该应用的保活设置，并杀死保活重启的进程。  
>  
> - 当被保活的应用进程退出时，系统将尝试重启该进程，连续3次重启失败后将不再继续重启。

**起始版本：** 14

**需要权限：** ohos.permission.MANAGE_APP_KEEP_ALIVE

<!--Device-appManager-function setKeepAliveForBundle(bundleName: string, userId: int, enable: boolean): Promise<void>--><!--Device-appManager-function setKeepAliveForBundle(bundleName: string, userId: int, enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要设置保活的应用包名。 |
| userId | number | 是 | 表示要设置保活应用所属的用户ID。 |
| enable | boolean | 是 | 表示对应用保活或者取消保活。true表示对应用保活，false表示对应用取消保活。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16300005](../errorcode-ability.md#16300005-指定的包信息不存在) | The target bundle does not exist. |
| [16300008](../errorcode-ability.md#16300008-指定的包不存在主uiability) | The target bundle has no MainAbility. |
| [16300009](../errorcode-ability.md#16300009-指定的包不存在状态栏) | The target bundle has no status-bar ability. |
| [16300010](../errorcode-ability.md#16300010-指定的应用在运行中但没有绑定状态栏) | The target application is not attached to the status bar. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = "ohos.samples.keepaliveapp";
  let userId = 100;
  appManager.setKeepAliveForBundle(bundleName, userId, true).then(() => {
    console.info(`setKeepAliveForBundle success`);
  }).catch((err: BusinessError) => {
    console.error(`setKeepAliveForBundle fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] setKeepAliveForBundle error: ${code}, ${message}`);
}

```

