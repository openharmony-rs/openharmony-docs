# off（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

<a id="off"></a>
## off('enabledAccessibilityExtensionListChange')

```TypeScript
function off(type: 'enabledAccessibilityExtensionListChange', callback?: Callback<void>): void
```

取消启用的辅助扩展的列表变化监听，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

<!--Device-config-function off(type: 'enabledAccessibilityExtensionListChange', callback?: Callback<void>): void--><!--Device-config-function off(type: 'enabledAccessibilityExtensionListChange', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'enabledAccessibilityExtensionListChange' | 是 | 参数固定为'enabledAccessibilityExtensionListChange'，监听启用的辅助扩展的列表变化。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与on('enabledAccessibilityExtensionListChange')的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例：**

```TypeScript
import { config } from '@kit.AccessibilityKit';

config.off('enabledAccessibilityExtensionListChange', () => {
  console.info('Unsubscribe enabled accessibility extension list change state success');
});

```


<a id="off-1"></a>
## off('installedAccessibilityListChange')

```TypeScript
function off(type: 'installedAccessibilityListChange', callback?: Callback<void>): void
```

取消已安装的辅助扩展的列表变化监听，使用callback异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

<!--Device-config-function off(type: 'installedAccessibilityListChange', callback?: Callback<void>): void--><!--Device-config-function off(type: 'installedAccessibilityListChange', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'installedAccessibilityListChange' | 是 | 参数固定为'installedAccessibilityListChange'，监听已安装的辅助扩展的列表变化。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与on('installedAccessibilityListChange')的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例：**

```TypeScript
import { config } from '@kit.AccessibilityKit';

config.off('installedAccessibilityListChange', () => {
  console.info('Unsubscribe installed accessibility extension list change state success');
});

```

