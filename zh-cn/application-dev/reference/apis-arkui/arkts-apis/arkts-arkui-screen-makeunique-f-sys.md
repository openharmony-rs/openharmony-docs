# makeUnique（系统接口）

## makeUnique

```TypeScript
function makeUnique(uniqueScreen: Array<number>): Promise<Array<number>>
```

����Ļ����Ϊ��Դģʽ��ʹ��Promise�첽�ص���

**起始版本：** 18

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueScreen | Array&lt;number&gt; | 是 | ��Դ��ĻID���ϡ�����IDӦΪ����0�����������򷵻�401�����롣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise���󡣷�����Դ��Ļ��displayId���ϣ�����idΪ����0�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, non-system application uses system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uniqueScreenIds: Array<number> = [1001, 1002, 1003];
screen.makeUnique(uniqueScreenIds).then((data: Array<number>) => {
  console.info('Succeeded in making unique screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to make unique screens. Code:${err.code}, message is ${err.message}`);
});

```

