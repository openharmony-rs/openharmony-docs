# getExtensionRunningInfos（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## getExtensionRunningInfos

```TypeScript
function getExtensionRunningInfos(upperLimit: number): Promise<Array<ExtensionRunningInfo>>
```

获取关于运行扩展能力的信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_RUNNING_INFO

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upperLimit | number | 是 | 获取消息数量的最大限制，最大为2 &lt;sup&gt;31 &lt;/sup&gt;-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;ExtensionRunningInfo&gt;&gt; | Promise对象，返回接口运行结果及运行扩展能力的信息。开发者可在此进行错误处理或其他自定义处理。 |

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

let upperLimit = 10;

try {
  abilityManager.getExtensionRunningInfos(upperLimit).then((data: Array<abilityManager.ExtensionRunningInfo>) => {
    console.info(`getExtensionRunningInfos success, data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`getExtensionRunningInfos fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code: number = (paramError as BusinessError).code;
  let message: string = (paramError as BusinessError).message;
  console.error(`error.code: ${code}, error.message: ${message}`);
}
```


## getExtensionRunningInfos

```TypeScript
function getExtensionRunningInfos(upperLimit: number, callback: AsyncCallback<Array<ExtensionRunningInfo>>): void
```

获取关于运行扩展能力的信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_RUNNING_INFO

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upperLimit | number | 是 | 获取消息数量的最大限制，最大为2 &lt;sup&gt;31 &lt;/sup&gt;-1。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;ExtensionRunningInfo&gt;&gt; | 是 | 回调函数。当获取运行扩展能力的信息成功，err为undefined，data为获取到的运行扩展能力信息；否则为 错误对象。可进行错误处理或其他自定义处理。 |

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

// 设置获取消息数量的最大限制
let upperLimit = 10;

try {
  abilityManager.getExtensionRunningInfos(upperLimit, (err: BusinessError, data: Array<abilityManager.ExtensionRunningInfo>) => {
    if (err) {
      console.error(`getExtensionRunningInfos fail, err: ${JSON.stringify(err)}`);
    } else {
      console.info(`getExtensionRunningInfos success, data: ${JSON.stringify(data)}`);
    }
  });
} catch (paramError) {
  let code: number = (paramError as BusinessError).code;
  let message: string = (paramError as BusinessError).message;
  console.error(`error.code: ${code}, error.message: ${message}`);
}
```
