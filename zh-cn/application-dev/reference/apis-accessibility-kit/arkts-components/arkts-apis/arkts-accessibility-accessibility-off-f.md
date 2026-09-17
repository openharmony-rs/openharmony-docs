# off

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## off('accessibilityStateChange')

```TypeScript
function off(type: 'accessibilityStateChange', callback?: Callback<boolean>): void
```

取消监听辅助应用启用状态变化事件。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'accessibilityStateChange' | 是 | 取消监听的事件名，固定为‘accessibilityStateChange’，即辅助应用启用状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('accessibilityStateChange')](arkts-accessibility-accessibility-on-f.md#onaccessibilitystatechange)的callback一致。缺省时，表示注销所有已注册事件。<br>**适用版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## off('touchGuideStateChange')

```TypeScript
function off(type: 'touchGuideStateChange', callback?: Callback<boolean>): void
```

取消监听触摸浏览启用状态变化事件。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchGuideStateChange' | 是 | 取消监听的事件名，固定为‘touchGuideStateChange’，即触摸浏览启用状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('touchGuideStateChange')](arkts-accessibility-accessibility-on-f.md#ontouchguidestatechange)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## off('screenReaderStateChange')

```TypeScript
function off(type: 'screenReaderStateChange', callback?: Callback<boolean>): void
```

取消监听屏幕朗读启用状态变化事件。使用callback异步回调。

**起始版本：** 18

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'screenReaderStateChange' | 是 | 取消监听的事件名，固定为‘screenReaderStateChange’，即屏幕朗读启用状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('screenReaderStateChange')](arkts-accessibility-accessibility-on-f.md#onscreenreaderstatechange)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## off('touchModeChange')

```TypeScript
function off(type: 'touchModeChange', callback?: Callback<string>): void
```

取消监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。

**起始版本：** 20

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchModeChange' | 是 | 取消监听的事件名，固定为‘touchModeChange’，即触摸浏览功能下的单击/双击操作模式变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('touchModeChange')](arkts-accessibility-accessibility-on-f.md#ontouchmodechange)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
