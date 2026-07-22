# prepare（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## prepare

```TypeScript
function prepare(callback: AsyncCallback<void>): void
```

准备键鼠穿越，使用Callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [prepareCooperate(callback:](arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate)

<!--Device-cooperate-function prepare(callback: AsyncCallback<void>): void--><!--Device-cooperate-function prepare(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，准备键鼠穿越成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.prepare((error: BusinessError) => {
    if (error) {
      console.error(`Keyboard mouse crossing prepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
      return;
    }
    console.info(`Keyboard mouse crossing prepare success.`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing prepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```


## prepare

```TypeScript
function prepare(): Promise<void>
```

准备键鼠穿越，使用Promise异步方式返回结果。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [prepareCooperate()](arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate)

<!--Device-cooperate-function prepare(): Promise<void>--><!--Device-cooperate-function prepare(): Promise<void>-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.prepare().then(() => {
    console.info(`Keyboard mouse crossing prepare success.`);
  }, (error: BusinessError) => {
    console.error(`Keyboard mouse crossing prepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing prepare failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

