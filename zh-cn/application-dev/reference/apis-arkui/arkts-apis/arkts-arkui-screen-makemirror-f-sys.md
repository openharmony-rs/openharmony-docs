# makeMirror（系统接口）

## makeMirror

```TypeScript
function makeMirror(mainScreen:number, mirrorScreen:Array<number>, callback: AsyncCallback<number>): void
```

����Ļ����Ϊ����ģʽ��ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreen | number | 是 | ����ĻID���ò�����֧���������롣 |
| mirrorScreen | Array&lt;number&gt; | 是 | ������ĻID���ϣ�����IDӦΪ������ |
| callback | AsyncCallback&lt;number&gt; | 是 | �ص����������ؾ�����Ļ��Ⱥ��id������idΪ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: number = 0;
let mirrorScreenIds: Array<number> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds, (err: BusinessError, data: number) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set screen mirroring. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
});

```


## makeMirror

```TypeScript
function makeMirror(mainScreen:number, mirrorScreen:Array<number>): Promise<number>
```

����Ļ����Ϊ����ģʽ��ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreen | number | 是 | ����ĻID���ò�����֧���������롣 |
| mirrorScreen | Array&lt;number&gt; | 是 | ������ĻID���ϡ�����IDӦΪ������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󡣷��ؾ�����Ļ��Ⱥ��id������idΪ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: number = 0;
let mirrorScreenIds: Array<number> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen mirroring. Code:${err.code}, message is ${err.message}`);
});

```

