# hasPrivateWindow（系统接口）

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="hasprivatewindow"></a>
## hasPrivateWindow

```TypeScript
function hasPrivateWindow(displayId: number): boolean
```

查询指定display对象上是否有可见的隐私窗口。可通过[setWindowPrivacyMode()](docroot://reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9)接口设置隐私窗口。隐私窗口内容将无法被截屏或录屏。

**起始版本：** 9

<!--Device-display-function hasPrivateWindow(displayId: long): boolean--><!--Device-display-function hasPrivateWindow(displayId: long): boolean-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 屏幕ID，该参数仅支持整数输入。该参数大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询的display对象上是否有可见的隐私窗口。true表示此display对象上有可见的隐私窗口，false表示此display对象上没有可见的隐私窗口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { display } from '@kit.ArkUI';

let displayClass: display.Display | null = null;
try {
  // 获取默认Display对象
  displayClass = display.getDefaultDisplaySync();

  let ret: boolean | undefined = undefined;
  try {
    // 查询默认屏幕上是否有隐私窗口
    ret = display.hasPrivateWindow(displayClass.id);
  } catch (exception) {
    console.error(`Failed to check has privateWindow or not. Code: ${exception.code}, message: ${exception.message}`);
  }
  if (ret == undefined) {
    console.error('Failed to check has privateWindow or not.');
  }
  if (ret) {
    console.info('There has privateWindow.');
  } else if (!ret) {
    console.info('There has no privateWindow.');
  }
} catch (exception) {
  console.error(`Failed to obtain the default display object. Code: ${exception.code}, message: ${exception.message}`);
}

```

