# getAbilityRunningInfos（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## getAbilityRunningInfos

```TypeScript
function getAbilityRunningInfos(callback: AsyncCallback<Array<AbilityRunningInfo>>): void
```

获取UIAbility运行相关信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_RUNNING_INFO

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;AbilityRunningInfo&gt;&gt; | 是 | 回调函数。当获取UIAbility运行相关信息成功，err为undefined，data为获取到的 UIAbility运行相关信息；否则为错误对象。可进行错误处理或其他自定义处理。 |

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
  abilityManager.getAbilityRunningInfos((err: BusinessError, data: Array<abilityManager.AbilityRunningInfo>) => {
    if (err) {
      console.error(`getAbilityRunningInfos fail, error: ${JSON.stringify(err)}`);
    } else {
      console.info(`getAbilityRunningInfos success, data: ${JSON.stringify(data)}`);
    }
  });
} catch (paramError) {
  let code: number = (paramError as BusinessError).code;
  let message: string = (paramError as BusinessError).message;
  console.error(`error.code: ${code}, error.message: ${message}`);
}
```
