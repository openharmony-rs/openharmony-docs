# off（系统接口）

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## off('privateModeChange')

```TypeScript
function off(type: 'privateModeChange', callback?: Callback<boolean>): void
```

关闭屏幕隐私模式变化的监听。当屏幕前台有隐私窗口，则屏幕处于隐私模式，屏幕中的隐私窗口内容无法被截屏或录屏。

**起始版本：** 10

<!--Device-display-function off(type: 'privateModeChange', callback?: Callback<boolean>): void--><!--Device-display-function off(type: 'privateModeChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'privateModeChange' | 是 | 监听事件，固定为'privateModeChange'，表示屏幕隐私模式状态发生变化。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt; | 否 | 需要取消注册的回调函数。表示屏幕隐私模式是否改变。true表示屏幕由非隐私窗口模式变为隐私模式，false表示屏幕由隐私模式变为非隐私模式。若无此参数，则取消注册屏幕隐私模式变化监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

**示例：**

```TypeScript
try {
  // 取消隐私模式变化监听
  display.off('privateModeChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Code: ${exception.code}, message: ${exception.message}`);
}

```

