# setScreenRotationLocked（系统接口）

## setScreenRotationLocked

```TypeScript
function setScreenRotationLocked(isLocked:boolean, callback: AsyncCallback<void>): void
```

�����Զ�ת�������Ƿ�������ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLocked | boolean | 是 | �Զ�ת�������Ƿ�������trueΪ������falseΪδ������ |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������������Զ�ת���Ƿ������ɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
screen.setScreenRotationLocked(isLocked, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to unlock auto rotate. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in unlocking auto rotate.');
});

```


## setScreenRotationLocked

```TypeScript
function setScreenRotationLocked(isLocked:boolean): Promise<void>
```

�����Զ�ת�������Ƿ�������ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLocked | boolean | 是 | �Զ�ת�������Ƿ�������trueΪ������falseΪδ������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
screen.setScreenRotationLocked(isLocked).then(() => {
  console.info('Succeeded in unlocking auto rotate');
}).catch((err: BusinessError) => {
  console.error(`Failed to unlock auto rotate. Code:${err.code}, message is ${err.message}`);
});

```

