# on（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## on('enabledAccessibilityExtensionListChange')

```TypeScript
function on(type: 'enabledAccessibilityExtensionListChange', callback: Callback<void>): void
```

添加启用的辅助扩展的列表变化监听。使用callback异步回调。需与 config.off('enabledAccessibilityExtensionListChange') 配对使用，在不需要监听时调用off取消注册，避免资源泄漏。

**起始版本：** 9

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'enabledAccessibilityExtensionListChange' | 是 | 参数固定为'enabledAccessibilityExtensionListChange'，指定监听启用的辅 助扩展的列表变化事件类型。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，在启用的辅助扩展的列表变化时通过此函数进行通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { config } from '@kit.AccessibilityKit';

config.highContrastText.on((data: boolean) => {
  console.info(`subscribe highContrastText success, result: ${JSON.stringify(data)}`);
});
```


## on('installedAccessibilityListChange')

```TypeScript
function on(type: 'installedAccessibilityListChange', callback: Callback<void>): void
```

添加已安装的辅助扩展的列表变化监听。使用callback异步回调。需与 config.off('installedAccessibilityListChange') 配对使用，在不需要监听时调用off取消注册，避免资源泄漏。

**起始版本：** 12

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'installedAccessibilityListChange' | 是 | 参数固定为'installedAccessibilityListChange'，监听已安装的辅助扩展的列表变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，在已安装的辅助扩展的列表变化时通过此函数进行通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

参见 on
