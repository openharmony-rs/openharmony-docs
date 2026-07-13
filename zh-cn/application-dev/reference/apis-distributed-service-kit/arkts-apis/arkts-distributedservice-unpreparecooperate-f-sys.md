# unprepareCooperate（系统接口）

## unprepareCooperate

```TypeScript
function unprepareCooperate(callback: AsyncCallback<void>): void
```

取消键鼠穿越准备，使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，取消键鼠穿越准备成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed.**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.unprepareCooperate((error: BusinessError) => {
    if (error) {
      console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
        [`code`, `message`])}`);
      return;
    }
    console.info(`Keyboard mouse crossing unprepareCooperate success.`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
    [`code`, `message`])}`);
}

```


## unprepareCooperate

```TypeScript
function unprepareCooperate(): Promise<void>
```

取消键鼠穿越准备，使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

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
  cooperate.unprepareCooperate().then(() => {
    console.info(`Keyboard mouse crossing unprepareCooperate success.`);
  }, (error: BusinessError) => {
    console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
      [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
    [`code`, `message`])}`);
}

```

