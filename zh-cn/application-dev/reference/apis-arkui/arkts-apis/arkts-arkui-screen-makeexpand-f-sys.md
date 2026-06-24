# makeExpand（系统接口）

## makeExpand

```TypeScript
function makeExpand(options:Array<ExpandOption>, callback: AsyncCallback<number>): void
```

����Ļ����Ϊ��չģʽ��ʹ��callback�첽�ص���

**起始版本：** 9

**废弃版本：** 20

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Array&lt;ExpandOption&gt; | 是 | ������չ��Ļ�Ĳ������ϡ� |
| callback | AsyncCallback&lt;number&gt; | 是 | �ص�������������չ��Ļ��Ⱥ��id������idΪ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number | null = null;
class ExpandOption {
  screenId: number = 0;
  startX: number = 0;
  startY: number = 0;
}
let mainScreenOption: ExpandOption = { screenId: 0, startX: 0, startY: 0 };
let otherScreenOption: ExpandOption = { screenId: 1, startX: 1080, startY: 0 };
let expandOptionArray : ExpandOption[] = [ mainScreenOption, otherScreenOption ];
screen.makeExpand(expandOptionArray, (err: BusinessError, data: number) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to expand the screen. Code:${err.code}, message is ${err.message}`);
    return;
  }
  groupId = data;
  console.info(`Succeeded in expanding the screen. Data: ${data}`);
});

```


## makeExpand

```TypeScript
function makeExpand(options:Array<ExpandOption>): Promise<number>
```

����Ļ����Ϊ��չģʽ��ʹ��Promise�첽�ص���

**起始版本：** 9

**废弃版本：** 20

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Array&lt;ExpandOption&gt; | 是 | ������չ��Ļ�Ĳ������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󡣷�����չ��Ļ��Ⱥ��id������idΪ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class ExpandOption {
  screenId: number = 0;
  startX: number = 0;
  startY: number = 0;
}
let mainScreenOption: ExpandOption = { screenId: 0, startX: 0, startY: 0 };
let otherScreenOption: ExpandOption = { screenId: 1, startX: 1080, startY: 0 };
let expandOptionArray : ExpandOption[] = [ mainScreenOption, otherScreenOption ];
screen.makeExpand(expandOptionArray).then((
  data: number) => {
  console.info(`Succeeded in expanding the screen. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to expand the screen. Code:${err.code}, message is ${err.message}`);
});

```

