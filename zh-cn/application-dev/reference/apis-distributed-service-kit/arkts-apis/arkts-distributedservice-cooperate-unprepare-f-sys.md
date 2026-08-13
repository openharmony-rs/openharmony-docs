# unprepare（系统接口）

## unprepare

```TypeScript
function unprepare(callback: AsyncCallback<void>): void
```

取消键鼠穿越准备，使用Callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unprepareCooperate)(callback: AsyncCallback&lt;void&gt;)

<!--Device-cooperate-function unprepare(callback: AsyncCallback<void>): void--><!--Device-cooperate-function unprepare(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，取消键鼠穿越准备成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. &lt;br&gt;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.unprepare((error: BusinessError) => {
    if (error) {
      console.error(`Keyboard mouse crossing unprepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
      return;
    }
    console.info(`Keyboard mouse crossing unprepare success.`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing unprepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```


## unprepare

```TypeScript
function unprepare(): Promise<void>
```

取消键鼠穿越准备，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unprepareCooperate（系统接口）)()

<!--Device-cooperate-function unprepare(): Promise<void>--><!--Device-cooperate-function unprepare(): Promise<void>-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. &lt;br&gt;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.unprepare().then(() => {
    console.info(`Keyboard mouse crossing unprepare success.`);
  }, (error: BusinessError) => {
    console.error(`Keyboard mouse crossing unprepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing unprepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

