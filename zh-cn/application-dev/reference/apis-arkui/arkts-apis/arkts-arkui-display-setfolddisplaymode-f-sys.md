# setFoldDisplayMode（系统接口）

## setFoldDisplayMode

```TypeScript
function setFoldDisplayMode(mode: FoldDisplayMode): void
```

更改可折叠设备的显示模式。

**起始版本：** 10

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | FoldDisplayMode | 是 | 可折叠设备的显示模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_FULL;
  display.setFoldDisplayMode(mode);
} catch (exception) {
  console.error(`Failed to change the fold display mode. Code: ${exception.code} , message : ${exception.message}`);
}

```


## setFoldDisplayMode

```TypeScript
function setFoldDisplayMode(mode: FoldDisplayMode, reason: string): void
```

更改可折叠设备的显示模式，并指明更改原因。

**起始版本：** 19

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | FoldDisplayMode | 是 | 可折叠设备的显示模式。 |
| reason | string | 是 | 更改显示模式的原因。不设置，则默认为空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let mode: display.FoldDisplayMode = display.FoldDisplayMode.FOLD_DISPLAY_MODE_MAIN;
  display.setFoldDisplayMode(mode, 'backSelfie');
} catch (exception) {
  console.error(`Failed to change the fold display mode. Code: ${exception}`);
}

```

