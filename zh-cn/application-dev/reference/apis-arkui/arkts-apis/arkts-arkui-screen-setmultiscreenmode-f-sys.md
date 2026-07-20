# setMultiScreenMode（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

<a id="setmultiscreenmode"></a>
## setMultiScreenMode

```TypeScript
function setMultiScreenMode(primaryScreenId: number, secondaryScreenId: number,
    secondaryScreenMode: MultiScreenMode): Promise<void>
```

设置扩展屏幕的显示模式（镜像/扩展），使用Promise异步回调。primaryScreenId和secondaryScreenId均为0时，仅在扩展屏显示。

**起始版本：** 13

<!--Device-screen-function setMultiScreenMode(primaryScreenId: long, secondaryScreenId: long,
    secondaryScreenMode: MultiScreenMode): Promise<void>--><!--Device-screen-function setMultiScreenMode(primaryScreenId: long, secondaryScreenId: long,
    secondaryScreenMode: MultiScreenMode): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primaryScreenId | number | 是 | 主屏的id，该参数应为非负整数。如果输入的数字包含小数部分，向下取整。 |
| secondaryScreenId | number | 是 | 扩展屏幕的id，该参数应为非负整数。如果输入的数字包含小数部分，向下取整。 |
| secondaryScreenMode | [MultiScreenMode](arkts-arkui-screen-multiscreenmode-e-sys.md) | 是 | 扩展屏幕的显示模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, non-system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let primaryScreenId: number = 0; // 主屏ID
let secondaryScreenId: number = 12; // 扩展屏ID
let screenMode: screen.MultiScreenMode = screen.MultiScreenMode.SCREEN_MIRROR;
// 设置扩展屏幕的显示模式为镜像模式
screen.setMultiScreenMode(primaryScreenId, secondaryScreenId, screenMode).then(() => {
  console.info('Succeeded in setting multi screen mode. Data: ');
}).catch((err: BusinessError) => {
  console.error(`Failed to set multi screen mode. Code: ${err.code}, message: ${err.message}`);
});

```

