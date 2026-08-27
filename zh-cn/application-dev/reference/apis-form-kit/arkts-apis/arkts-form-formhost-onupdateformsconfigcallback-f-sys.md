# onUpdateFormsConfigCallback（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## onUpdateFormsConfigCallback

```TypeScript
function onUpdateFormsConfigCallback(callback: formInfo.UpdateFormsConfigCallback): void
```

订阅更新卡片配置事件。使用callback异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | formInfo.UpdateFormsConfigCallback | 是 | 回调函数，返回卡片配置更新信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |

**示例**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const callback = (configInfo: formInfo.FormCustomConfig[]): void => {
    console.info(`onUpdateFormsConfigCallback configInfo length: ${configInfo.length}`);
    for (let config of configInfo) {
      console.info(`bundleName: ${config.bundleName}, moduleName: ${config.moduleName}`);
    }
  };
  formHost.onUpdateFormsConfigCallback(callback);
  console.info(`onUpdateFormsConfigCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
