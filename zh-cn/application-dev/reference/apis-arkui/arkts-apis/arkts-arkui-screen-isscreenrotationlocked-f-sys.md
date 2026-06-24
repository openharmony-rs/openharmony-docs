# isScreenRotationLocked（系统接口）

## isScreenRotationLocked

```TypeScript
function isScreenRotationLocked(callback: AsyncCallback<boolean>): void
```

��ѯ��ǰ�Զ�ת���Ƿ�������ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص�����������true��ʾ��ǰ�Զ�ת����������״̬������false��ʾ��ǰ�Զ�ת������������״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

screen.isScreenRotationLocked((err: BusinessError, isLocked: boolean) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to get the screen rotation lock status. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting the screen rotation lock status. isLocked: ${isLocked}`);
});

```


## isScreenRotationLocked

```TypeScript
function isScreenRotationLocked(): Promise<boolean>
```

��ѯ��ǰ�Զ�ת���Ƿ�������ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󡣷���true��ʾ��ǰ�Զ�ת����������״̬������false��ʾ��ǰ�Զ�ת������������״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

screen.isScreenRotationLocked().then((isLocked: boolean) => {
  console.info(`Succeeded in getting the screen rotation lock status. isLocked: ${isLocked}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get the screen rotation lock status. Code:${err.code}, message is ${err.message}`);
});

```

