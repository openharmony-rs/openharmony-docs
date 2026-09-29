# getAvailableFormHostServices（系统接口）

## 导入模块

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## getAvailableFormHostServices

```TypeScript
function getAvailableFormHostServices(): Promise<Array<formInfo.PeerFormHostServiceInfo>>
```

获取可用的卡片使用方服务信息列表。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.AGENT_REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formAgent-function getAvailableFormHostServices(): Promise<Array<formInfo.PeerFormHostServiceInfo>>--><!--Device-formAgent-function getAvailableFormHostServices(): Promise<Array<formInfo.PeerFormHostServiceInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[formInfo.PeerFormHostServiceInfo](arkts-form-forminfo-peerformhostserviceinfo-i-sys.md)&gt;&gt; | Promise对象，返回可用的卡片使用方服务信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |

**示例**

```TypeScript
import { formAgent, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formAgent.getAvailableFormHostServices().then((data: formInfo.PeerFormHostServiceInfo[]) => {
    console.info(`formAgent getAvailableFormHostServices success, service count: ${data.length}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
