# acquireShareData（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## acquireShareData

```TypeScript
function acquireShareData(missionId: number, callback: AsyncCallback<Record<string, Object>>): void
```

系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的 [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare)回调并返回分享数据。使用 callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 目标应用的missionId，最大为2 & lt;sup & gt;31 & lt;/sup & gt;-1。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | 回调函数。当接口调用成功，err为undefined，data为获取到的分享数据；否则为错误对象。可进行错误处理或其他自 定义处理。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  abilityManager.acquireShareData(1, (err: BusinessError, wantParam: Record<string, Object>) => {
    if (err) {
      console.error(`acquireShareData fail, err: ${JSON.stringify(err)}`);
    } else {
      console.info(`acquireShareData success, data: ${JSON.stringify(wantParam)}`);
    }
  });
} catch (paramError) {
  let code: number = (paramError as BusinessError).code;
  let message: string = (paramError as BusinessError).message;
  console.error(`error.code: ${code}, error.message: ${message}`);
}
```


## acquireShareData

```TypeScript
function acquireShareData(missionId: number): Promise<Record<string, Object>>
```

系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的 [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare)回调并返回分享数据。使用 Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 目标应用的missionId，最大为2 & lt;sup & gt;31 & lt;/sup & gt;-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;{ [key: string]: Object | > } The promise returned by the function.<br>**适用版本：** 10 |
| Promise & lt;Record & lt;string, Object & gt; & gt; | Promise used to return the API call result and the shared data. You can perform error handling or other custom processing.<br>**适用版本：** 11+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  abilityManager.acquireShareData(1).then((wantParam: Record<string, Object>) => {
    console.info(`acquireShareData success, data: ${JSON.stringify(wantParam)}`);
  }).catch((err: BusinessError) => {
    console.error(`acquireShareData fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code: number = (paramError as BusinessError).code;
  let message: string = (paramError as BusinessError).message;
  console.error(`error.code: ${code}, error.message: ${message}`);
}
```
