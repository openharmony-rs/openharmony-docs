# setFoldStatusLocked（系统接口）

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="setfoldstatuslocked"></a>
## setFoldStatusLocked

```TypeScript
function setFoldStatusLocked(locked: boolean): void
```

设置可折叠设备当前折叠状态的锁定状态。

**起始版本：** 11

<!--Device-display-function setFoldStatusLocked(locked: boolean): void--><!--Device-display-function setFoldStatusLocked(locked: boolean): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locked | boolean | 是 | 可折叠设备的折叠状态是否锁定。true表示锁定，false表示不锁定。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { display } from '@kit.ArkUI';

try {
  let locked: boolean = false;
  // 设置折叠状态不锁定
  display.setFoldStatusLocked(locked);
} catch (exception) {
  console.error(`Failed to change the fold status locked mode. Code: ${exception.code}, message: ${exception.message}`);
}

```

