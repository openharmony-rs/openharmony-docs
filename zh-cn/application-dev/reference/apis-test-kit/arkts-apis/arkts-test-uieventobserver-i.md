# UIEventObserver

UI事件监听器。

**起始版本：** 10

**系统能力：** SystemCapability.Test.UiTest

## once('toastShow')

```TypeScript
once(type: 'toastShow', callback: Callback<UIElementInfo>): void
```

开始监听toast控件出现的事件，使用callback的形式返回结果。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'toastShow' | 是 | 订阅的事件类型，取值为'toastShow'。 |
| callback | Callback&lt;UIElementInfo&gt; | 是 | 事件发生时执行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UIElementInfo, UIEventObserver } from '@kit.TestKit';

async function demo() {
  // 创建Driver对象
  let driver: Driver = Driver.create();
  // 创建UI事件监听器
  let observer: UIEventObserver = driver.createUIEventObserver();
  // 定义回调函数，输出toast控件的属性信息
  let callback = (UIElementInfo: UIElementInfo) => {
    console.info(UIElementInfo.bundleName);
    console.info(UIElementInfo.text);
    console.info(UIElementInfo.type);
  }
  // 订阅toast控件出现事件
  observer.once('toastShow', callback);
}

```

## once('dialogShow')

```TypeScript
once(type: 'dialogShow', callback: Callback<UIElementInfo>): void
```

开始监听dialog控件出现的事件，使用callback的形式返回结果。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dialogShow' | 是 | 订阅的事件类型，取值为'dialogShow'。 |
| callback | Callback&lt;UIElementInfo&gt; | 是 | 事件发生时执行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UIElementInfo, UIEventObserver } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let observer: UIEventObserver = driver.createUIEventObserver();
  let callback = (UIElementInfo: UIElementInfo) => {
    console.info(UIElementInfo.bundleName);
    console.info(UIElementInfo.text);
    console.info(UIElementInfo.type);
  }
  observer.once('dialogShow', callback);
}

```

## once('windowChange')

```TypeScript
once(type: 'windowChange', windowChangeType: WindowChangeType, options: WindowChangeOptions, callback: Callback<UIElementInfo>): void
```

开始监听指定类型的窗口变化事件，支持设置事件监听的扩展配置，监听到指定窗口变化事件时触发callback回调。仅支持
[自由多窗模式](../../../../windowmanager/window-terminology.md#自由多窗模式)的窗口监听。

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowChange' | 是 | 订阅的事件类型，支持的事件为'windowChange'。当监听到窗口变化时，触发该事件。 |
| windowChangeType | WindowChangeType | 是 | 窗口变化事件类型。 |
| options | WindowChangeOptions | 是 | 窗口变化事件监听的扩展配置，包括监听超时时间和监听窗口对应包名。 |
| callback | Callback&lt;UIElementInfo&gt; | 是 | 事件发生时执行的回调函数，返回事件的相关信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UIElementInfo, UIEventObserver, WindowChangeOptions, WindowChangeType } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let observer: UIEventObserver = driver.createUIEventObserver();
  let options: WindowChangeOptions = {
    timeout: 20000,
    bundleName: 'com.example.myapplication'  // 请开发者替换为实际包名
  }
  let callback = (UIElementInfo: UIElementInfo) => {
    console.info(UIElementInfo.bundleName);
    console.info(UIElementInfo.text);
    console.info(UIElementInfo.type);
    console.info(UIElementInfo.windowChangeType?.toString());
    console.info(UIElementInfo.windowId?.toString());
  }
  observer.once('windowChange', WindowChangeType.WINDOW_ADDED, options, callback);
}

```

## once('componentEventOccur')

```TypeScript
once(type: 'componentEventOccur', componentEventType: ComponentEventType, options: ComponentEventOptions, callback: Callback<UIElementInfo>): void
```

开始监听指定类型的控件操作事件，支持设置事件监听的扩展配置，监听到指定控件操作事件时触发callback回调。

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'componentEventOccur' | 是 | 订阅的事件类型，支持的事件为'componentEventOccur'。当监听到控件操作时，触发该事件。 |
| componentEventType | ComponentEventType | 是 | 控件操作事件类型。 |
| options | ComponentEventOptions | 是 | 控件操作事件监听的扩展配置，包括监听超时时间和监听控件匹配条件。 |
| callback | Callback&lt;UIElementInfo&gt; | 是 | 事件发生时执行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UIElementInfo, UIEventObserver, ComponentEventOptions, ComponentEventType, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let observer: UIEventObserver = driver.createUIEventObserver();
  let option: ComponentEventOptions = {
    timeout: 20000,
    on: ON.id('123')  // 请开发者替换为实际存在的控件id值
  };
  let callback = (UIElementInfo: UIElementInfo) => {
    console.info(UIElementInfo.bundleName);
    console.info(UIElementInfo.text);
    console.info(UIElementInfo.type);
    console.info(UIElementInfo.componentEventType?.toString());
    console.info(UIElementInfo.windowId?.toString());
    console.info(UIElementInfo.componentId);
    console.info(UIElementInfo.componentRect?.left.toString());
    console.info(UIElementInfo.componentRect?.top.toString());
    console.info(UIElementInfo.componentRect?.right.toString());
    console.info(UIElementInfo.componentRect?.bottom.toString());
  };
  observer.once('componentEventOccur', ComponentEventType.COMPONENT_CLICKED, option, callback);
}

```

