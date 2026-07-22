# setMultiScreenRelativePosition（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## setMultiScreenRelativePosition

```TypeScript
function setMultiScreenRelativePosition(mainScreenOptions: MultiScreenPositionOptions,
    secondaryScreenOptions: MultiScreenPositionOptions): Promise<void>
```

仅在扩展模式下，设置主屏和扩展屏幕的位置信息，使用Promise异步回调。

**起始版本：** 13

<!--Device-screen-function setMultiScreenRelativePosition(mainScreenOptions: MultiScreenPositionOptions,    secondaryScreenOptions: MultiScreenPositionOptions): Promise<void>--><!--Device-screen-function setMultiScreenRelativePosition(mainScreenOptions: MultiScreenPositionOptions,    secondaryScreenOptions: MultiScreenPositionOptions): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreenOptions | [MultiScreenPositionOptions](arkts-arkui-screen-multiscreenpositionoptions-i-sys.md) | 是 | 主屏的位置信息。 |
| secondaryScreenOptions | [MultiScreenPositionOptions](arkts-arkui-screen-multiscreenpositionoptions-i-sys.md) | 是 | 扩展屏幕的位置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, non-system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let mainScreenOptions: screen.MultiScreenPositionOptions = {
  id : 0,  // 主屏ID
  startX : 0,
  startY : 0
}; // 主屏的位置信息

let secondaryScreenOptions: screen.MultiScreenPositionOptions = {
  id : 12,  // 扩展屏ID
  startX : 1000,
  startY : 1000
}; // 扩展屏幕的位置信息

// 设置主屏和扩展屏幕的位置信息
screen.setMultiScreenRelativePosition(mainScreenOptions, secondaryScreenOptions).then(() => {
  console.info('Succeeded in setting multi screen relative position.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set multi screen relative position. Code: ${err.code}, message: ${err.message}`);
});

```

