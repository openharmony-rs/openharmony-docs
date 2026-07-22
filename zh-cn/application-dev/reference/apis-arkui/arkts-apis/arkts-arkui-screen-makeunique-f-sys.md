# makeUnique（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## makeUnique

```TypeScript
function makeUnique(uniqueScreen: Array<number>): Promise<Array<number>>
```

将屏幕设置为异源模式，使用Promise异步回调。

**起始版本：** 18

<!--Device-screen-function makeUnique(uniqueScreen: Array<long>): Promise<Array<long>>--><!--Device-screen-function makeUnique(uniqueScreen: Array<long>): Promise<Array<long>>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueScreen | Array&lt;number&gt; | 是 | 异源屏幕ID集合。其中ID应为大于0的整数，否则返回401错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise对象。返回异源屏幕的displayId集合，其中id为大于0的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, non-system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let uniqueScreenIds: Array<number> = [1001, 1002, 1003]; // 异源屏ID集合
// 设置屏幕为异源模式
screen.makeUnique(uniqueScreenIds).then((data: Array<number>) => {
  console.info('Succeeded in making unique screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to make unique screens. Code: ${err.code}, message: ${err.message}`);
});

```

