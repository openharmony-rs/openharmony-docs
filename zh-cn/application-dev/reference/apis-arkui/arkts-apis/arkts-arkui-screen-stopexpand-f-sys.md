# stopExpand（系统接口）

## stopExpand

```TypeScript
function stopExpand(expandScreen:Array<number>, callback: AsyncCallback<void>): void
```

ֹͣ��Ļ����չģʽ��ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 20

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expandScreen | Array&lt;number&gt; | 是 | ��չ��ĻID���ϣ�����IDΪ������ expandScreen�����С��Ӧ����1000�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص���������ֹͣ��Ļ��չģʽ�ɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let expandScreenIds: Array<number> = [1, 2, 3];
screen.stopExpand(expandScreenIds, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to stop expand screens. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in stopping expand screens.');
});

```


## stopExpand

```TypeScript
function stopExpand(expandScreen:Array<number>): Promise<void>
```

ֹͣ��Ļ����չģʽ��ʹ��Promise�첽�ص���

**起始版本：** 10

**废弃版本：** 20

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expandScreen | Array&lt;number&gt; | 是 | ��չ��ĻID���ϣ�����IDΪ������expandScreen�����С��Ӧ����1000�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let expandScreenIds: Array<number> = [1, 2, 3];
screen.stopExpand(expandScreenIds).then(() => {
  console.info('Succeeded in stopping expand screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop expand screens. Code:${err.code}, message is ${err.message}`);
});

```

