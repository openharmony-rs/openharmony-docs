# registerFormHostService（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## registerFormHostService

```TypeScript
function registerFormHostService(service: formInfo.FormHostServiceInfo): Promise<string>
```

注册卡片使用方服务信息。注册成功后，可用于跨设备卡片发布。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function registerFormHostService(service: formInfo.FormHostServiceInfo): Promise<string>--><!--Device-formHost-function registerFormHostService(service: formInfo.FormHostServiceInfo): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| service | [formInfo.FormHostServiceInfo](arkts-form-forminfo-formhostserviceinfo-i-sys.md) | 是 | 注册到卡片管理服务的卡片使用方服务信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回注册成功的卡片使用方服务的服务Id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |

**示例**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let service: formInfo.FormHostServiceInfo = {
  serviceName: 'serviceName',
  serviceDisplayName: 'serviceDisplayName',
  displayId: '0'
};
try {
  formHost.registerFormHostService(service).then((data: string) => {
    console.info(`formHost registerFormHostService success, service ID is: ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
