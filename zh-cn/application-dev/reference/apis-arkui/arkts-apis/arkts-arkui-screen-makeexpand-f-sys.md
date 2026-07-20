# makeExpand（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

<a id="makeexpand"></a>
## makeExpand

```TypeScript
function makeExpand(options:Array<ExpandOption>, callback: AsyncCallback<number>): void
```

将屏幕设置为扩展模式，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

<!--Device-screen-function makeExpand(options:Array<ExpandOption>, callback: AsyncCallback<long>): void--><!--Device-screen-function makeExpand(options:Array<ExpandOption>, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Array&lt;ExpandOption&gt; | 是 | 设置扩展屏幕的参数集合。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。返回扩展屏幕的群组id，其中id为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

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
// 将屏幕设置为扩展模式
screen.makeExpand(expandOptionArray, (err: BusinessError, data: number) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to expand the screen. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  groupId = data;
  console.info(`Succeeded in expanding the screen. Data: ${data}`);
});

```


<a id="makeexpand-1"></a>
## makeExpand

```TypeScript
function makeExpand(options:Array<ExpandOption>): Promise<number>
```

将屏幕设置为扩展模式，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

<!--Device-screen-function makeExpand(options:Array<ExpandOption>): Promise<long>--><!--Device-screen-function makeExpand(options:Array<ExpandOption>): Promise<long>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Array&lt;ExpandOption&gt; | 是 | 设置扩展屏幕的参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回扩展屏幕的群组id，其中id为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

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
// 将屏幕设置为扩展模式
screen.makeExpand(expandOptionArray).then((data: number) => {
  console.info(`Succeeded in expanding the screen. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to expand the screen. Code: ${err.code}, message: ${err.message}`);
});

```

