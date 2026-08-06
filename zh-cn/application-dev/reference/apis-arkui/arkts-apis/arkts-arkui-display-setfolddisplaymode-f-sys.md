# setFoldDisplayMode（系统接口）

## setFoldDisplayMode

```TypeScript
function setFoldDisplayMode(mode: FoldDisplayMode): void
```

更改可折叠设备的显示模式。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-display-function setFoldDisplayMode(mode: FoldDisplayMode): void--><!--Device-display-function setFoldDisplayMode(mode: FoldDisplayMode): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 可折叠设备的显示模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_FULL;
  // 设置折叠显示模式为全屏显示
  display.setFoldDisplayMode(mode);
} catch (exception) {
  console.error(`Failed to change the fold display mode. Code: ${exception.code}, message: ${exception.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_FULL;
  display.setFoldDisplayMode(mode);
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to change the fold display mode. Code: ${error.code} , message: ${error.message}`);
}
```


## setFoldDisplayMode

```TypeScript
function setFoldDisplayMode(mode: FoldDisplayMode, reason: string): void
```

更改可折叠设备的显示模式，并指明更改原因。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-display-function setFoldDisplayMode(mode: FoldDisplayMode, reason: string): void--><!--Device-display-function setFoldDisplayMode(mode: FoldDisplayMode, reason: string): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 可折叠设备的显示模式。 |
| reason | string | 是 | 更改显示模式的原因。不设置，则默认为空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_MAIN;
  // 设置折叠显示模式为主屏幕显示并指定原因为“backSelfie”
  display.setFoldDisplayMode(mode, 'backSelfie');
} catch (exception) {
  console.error(`Failed to change the fold display mode. Code: ${exception.code}, message: ${exception.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_MAIN;
  display.setFoldDisplayMode(mode, 'backSelfie');
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to change the fold display mode. Code: ${error.code} , message: ${error.message}`);
}
```

