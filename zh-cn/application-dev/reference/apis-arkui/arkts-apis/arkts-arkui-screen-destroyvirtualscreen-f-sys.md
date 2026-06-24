# destroyVirtualScreen（系统接口）

## destroyVirtualScreen

```TypeScript
function destroyVirtualScreen(screenId:number, callback: AsyncCallback<void>): void
```

����������Ļ��ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | ��Ļ��id���ò�����֧���������롣 |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص�������������������Ļ�ɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400002](../../errorcode-universal.md#1400002-Unauthorized) | Unauthorized operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: number = 1;
screen.destroyVirtualScreen(screenId, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to destroy the virtual screen. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying the virtual screen.');
});

```


## destroyVirtualScreen

```TypeScript
function destroyVirtualScreen(screenId:number): Promise<void>
```

����������Ļ��ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | ��Ļ��id���ò�����֧���������롣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400002](../../errorcode-universal.md#1400002-Unauthorized) | Unauthorized operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: number = 1;
screen.destroyVirtualScreen(screenId).then(() => {
  console.info('Succeeded in destroying the virtual screen.');
}).catch((err: BusinessError) => {
  console.error(`Failed to destroy the virtual screen.Code:${err.code}, message is ${err.message}`);
});

```

