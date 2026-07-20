# deactivateCooperate（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

<a id="deactivatecooperate"></a>
## deactivateCooperate

```TypeScript
function deactivateCooperate(isUnchained: boolean, callback: AsyncCallback<void>): void
```

停止键鼠穿越，使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function deactivateCooperate(isUnchained: boolean, callback: AsyncCallback<void>): void--><!--Device-cooperate-function deactivateCooperate(isUnchained: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isUnchained | boolean | 是 | 是否关闭跨设备链路。 true表示关闭跨设备链路，false表示不关闭。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，键鼠穿越停止成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed.  **ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.deactivateCooperate(false, (error: BusinessError) => {
    if (error) {
      console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
      return;
    }
    console.info(`Stop Keyboard mouse crossing success.`);
  });
} catch (error) {
  console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```


<a id="deactivatecooperate-1"></a>
## deactivateCooperate

```TypeScript
function deactivateCooperate(isUnchained: boolean): Promise<void>
```

停止键鼠穿越，使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function deactivateCooperate(isUnchained: boolean): Promise<void>--><!--Device-cooperate-function deactivateCooperate(isUnchained: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isUnchained | boolean | 是 | 是否关闭跨设备链路。 true表示关闭跨设备链路，false表示不关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.deactivateCooperate(false).then(() => {
    console.info(`Stop Keyboard mouse crossing success.`);
  }, (error: BusinessError) => {
    console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

