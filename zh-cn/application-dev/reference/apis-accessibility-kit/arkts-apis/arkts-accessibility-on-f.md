# on

## on('accessibilityStateChange')

```TypeScript
function on(type: 'accessibilityStateChange', callback: Callback<boolean>): void
```

监听辅助应用启用状态变化事件，使用callback异步回调。如需获取系统内辅助应用信息，推荐使用
[accessibility.getAccessibilityExtensionListSync](arkts-accessibility-getaccessibilityextensionlistsync-f.md#getaccessibilityextensionlistsync-1)。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
>
> - 调用此方法后，务必在对象生命周期结束前使用
> [accessibility.off('accessibilityStateChange')](arkts-accessibility-off-f.md#off-1)
> 取消监听，否则可能会导致崩溃。

**起始版本：** 7

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'accessibilityStateChange' | 是 | 监听的事件名，固定为‘accessibilityStateChange’，即辅助应用启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是 | 回调函数，在辅助应用启用状态变化时将状态通过此函数进行通知。此状态为全局辅助应用启用状态。返回true表示已启用辅助应用，返回false表示已禁用辅助应用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

// 系统内已安装一个或多个辅助应用时:
// 1. 启用辅助应用场景：第一个辅助应用启用后，回调函数会返回true。
// 2. 禁用辅助应用场景：若一个或多个辅助应用已启用，最后一个已启用的辅助应用被禁用时，回调函数会返回false。
accessibility.on('accessibilityStateChange', (data: boolean) => {
  console.info(`subscribe accessibility state change, result: ${JSON.stringify(data)}`);
});

```


## on('touchGuideStateChange')

```TypeScript
function on(type: 'touchGuideStateChange', callback: Callback<boolean>): void
```

监听触摸浏览功能启用状态变化事件，使用callback异步回调。如需获取系统内辅助应用信息，推荐使用
[accessibility.getAccessibilityExtensionListSync](arkts-accessibility-getaccessibilityextensionlistsync-f.md#getaccessibilityextensionlistsync-1)。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
>
> - 调用此方法后，务必在对象生命周期结束前使用
> [accessibility.off('touchGuideStateChange')](arkts-accessibility-off-f.md#off-2)
> 取消监听，否则可能会导致崩溃。

**起始版本：** 7

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Vision

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchGuideStateChange' | 是 | 监听的事件名，固定为‘touchGuideStateChange’，即触摸浏览启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是 | 回调函数，在触摸浏览启用状态变化时将状态通过此函数进行通知。返回true表示触摸浏览功能已开启，返回false表示触摸浏览功能已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

// 系统内已安装一个或多个具备触摸浏览能力的辅助应用（Capability配置中含有'touchGuide'的辅助应用）时：
// 1. 启用触摸浏览辅助应用场景：第一个触摸浏览辅助应用启用后，回调函数会返回true。
// 2. 禁用触摸浏览辅助应用场景：若一个或多个触摸浏览辅助应用已启用，最后一个已启用的触摸浏览辅助应用被禁用时，回调函数会返回false。
accessibility.on('touchGuideStateChange', (data: boolean) => {
  console.info(`subscribe touch guide state change, result: ${JSON.stringify(data)}`);
});

```


## on('screenReaderStateChange')

```TypeScript
function on(type: 'screenReaderStateChange', callback: Callback<boolean>): void
```

监听屏幕朗读功能启用状态变化事件，使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
>
> - 调用此方法后，务必在对象生命周期结束前使用
> [accessibility.off('screenReaderStateChange')](arkts-accessibility-off-f.md#off-3)
> 取消监听，否则可能会导致崩溃。

**起始版本：** 18

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'screenReaderStateChange' | 是 | 监听的事件名，固定为‘screenReaderStateChange’，即屏幕朗读启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是 | 回调函数，在屏幕朗读启用状态变化时将状态通过此函数进行通知。返回true表示屏幕朗读功能已开启，返回false表示屏幕朗读功能已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

accessibility.on('screenReaderStateChange', (data: boolean) => {
  console.info(`subscribe screen reader state change, result: ${JSON.stringify(data)}`);
});

```


## on('touchModeChange')

```TypeScript
function on(type: 'touchModeChange', callback: Callback<string>): void
```

监听触摸浏览功能下的单击/双击操作模式变化事件，使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
>
> - 调用此方法后，务必在对象生命周期结束前使用
> [accessibility.off('touchModeChange')](arkts-accessibility-off-f.md#off-4)
> 取消监听，否则可能会导致崩溃。

**起始版本：** 20

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchModeChange' | 是 | 监听的事件名，固定为‘touchModeChange’，即触摸浏览功能下的单击/双击操作模式变化事件。 |
| callback | Callback&lt;string&gt; | 是 | 回调函数，在触摸浏览功能下的单击/双击操作模式变化时将状态通过此函数进行通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) |  |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`current touch mode: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchModeChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}

```

