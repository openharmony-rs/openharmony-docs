# clearUpAppData（系统接口）

## clearUpAppData

```TypeScript
function clearUpAppData(bundleName: string, appCloneIndex?: number): Promise<void>
```

根据Bundle名称和应用分身索引，清除指定应用的数据。使用Promise异步回调。

**起始版本：** 13

**需要权限：** ohos.permission.CLEAN_APPLICATION_DATA

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |
| appCloneIndex | number | 否 | 表示应用分身索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = 'com.ohos.demo';
let appCloneIndex: number = 0;

try {
  appManager.clearUpAppData(bundleName, appCloneIndex).then(() => {
    console.info(`clearUpAppData success.`);
  }).catch((err: BusinessError) => {
    console.error(`clearUpAppData fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

```

