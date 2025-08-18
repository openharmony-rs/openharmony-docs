# @ohos.window.floatingBall (闪控球窗口)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @betafringe007-->
<!--Designer: @zhoulin_-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

该模块提供闪控球的基础功能，包括判断设备是否支持闪控球功能，以及创建闪控球控制器来启动、更新或停止闪控球。适用于比价、搜题或抢单等场景，以小窗模式呈现内容。闪控球以悬浮小组件形式显示在其他应用之上，即时呈现应用的关键信息。

> **说明：**
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { floatingBall } from '@kit.ArkUI';
```

## floatingBall.isFloatingBallEnabled

isFloatingBallEnabled(): boolean

判断当前设备是否支持闪控球功能。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
|------------|------------|
| boolean  | 当前设备是否支持闪控球功能。true表示支持，false则表示不支持。 |

**示例：**

```ts
let enable: boolean = floatingBall.isFloatingBallEnabled();
console.info('Floating ball enabled is: ' + enable);
```

## floatingBall.create

create(config: FloatingBallConfiguration): Promise&lt;FloatingBallController&gt;

创建闪控球控制器，使用Promise异步回调。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| config | [FloatingBallConfiguration](#floatingballconfiguration) | 是 | 创建闪控球控制器的参数。该参数不能为空，并且构造该参数的context不能为空。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;[FloatingBallController](#floatingballcontroller)&gt; | Promise对象。返回当前创建的闪控球控制器。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 801 | Capability not supported.Failed to call the API due to limited device capabilities. |
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300023 | Floating ball internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

let floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
//请在组件内获取context，确保this.getUIContext().getHostContext()返回的结果为UIAbilityContext
let ctx = this.getUIContext().getHostContext() as common.UIAbilityContext; 
let config: floatingBall.FloatingBallConfiguration = {
  context: ctx,
};
try {
  floatingBall.create(config).then((data: floatingBall.FloatingBallController) => {
    floatingBallController = data;
    console.info(`Succeeded in creating floating ball controller. Data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create floating ball controller. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to create floating ball controller. Cause:${e.code}, message:${e.message}`);
}
```

## FloatingBallConfiguration

创建闪控球控制器时需要提供的参数配置。

**系统能力：** SystemCapability.Window.SessionManager

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | 否 | 否 | 表示上下文环境。|

## FloatingBallController

闪控球控制器实例，用于启动、更新、停止闪控球以及注册回调等操作。

下列API示例中都需先使用[floatingBall.create()](#floatingballcreate)方法获取到闪控球控制器实例（即floatingBallController），再通过此实例调用对应方法。

**系统能力：** SystemCapability.Window.SessionManager

### startFloatingBall

startFloatingBall(params: FloatingBallParams): Promise&lt;void&gt;

启动闪控球，使用Promise异步回调。

**需要权限：** ohos.permission.USE_FLOAT_BALL

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| params | [FloatingBallParams](#floatingballparams) | 是 | 启动闪控球的参数。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 201 | Permission verification failed, usually returned by VerifyAccessToken. |
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300020 | Failed to create the floating ball window. |
| 1300021 | Failed to start multiple floating ball windows. |
| 1300022 | Repeated floating ball operation. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |
| 1300025 | The floating ball state does not support this operation. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let startParams: floatingBall.FloatingBallParams = {
  template: floatingBall.FloatingBallTemplate.EMPHATIC,
  title: 'title',
  content: 'content'
};
try {
  floatingBallController.startFloatingBall(startParams).then(() => {
    console.info('Succeeded in starting floating ball.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to start floating ball. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to start floating ball. Cause:${e.code}, message:${e.message}`);
}
```

### updateFloatingBall

updateFloatingBall(params: FloatingBallParams): Promise&lt;void&gt;

更新闪控球，使用Promise异步回调。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| params | [FloatingBallParams](#floatingballparams) | 是 | 更新闪控球的参数。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. |
| 1300003 | This window manager service works abnormally. |
| 1300004 | Unauthorized operation. |
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |
| 1300025 | The floating ball state does not support this operation. |
| 1300027 | When updating the floating ball, the template type cannot be changed. |
| 1300028 | Updating static template-based floating balls is not supported. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let updateParams: floatingBall.FloatingBallParams = {
  template: floatingBall.FloatingBallTemplate.EMPHATIC,
  title: 'title2',
  content: 'content2'
};
try {
  floatingBallController.updateFloatingBall(updateParams).then(() => {
    console.info('Succeeded in updating floating ball.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to update floating ball. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to update floating ball. Cause:${e.code}, message:${e.message}`);
}
```

### stopFloatingBall

stopFloatingBall(): Promise&lt;void&gt;

停止闪控球，使用Promise异步回调。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300022 | Repeated floating ball operation. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

floatingBallController.stopFloatingBall().then(() => {
  console.info('Succeeded in stopping floating ball.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop floating ball. Cause:${err.code}, message:${err.message}`);
});
```

### on('stateChange')

on(type: 'stateChange', callback: Callback&lt;FloatingBallState&gt;): void

注册闪控球生命周期状态变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| type | string | 是 | 监听事件，固定为'stateChange'，即闪控球生命周期状态变化事件。 |
| callback | Callback&lt;[FloatingBallState](#floatingballstate)&gt; | 是 | 回调函数。返回当前的闪控球生命周期状态。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300022 | Repeated floating ball operation. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |

**示例：**

```ts
let onStateChange = (state: floatingBall.FloatingBallState) => {
  console.info('Floating ball stateChange: ' + state);
};
try {
  floatingBallController.on('stateChange', onStateChange);
} catch(e) {
  console.error(`Failed to on stateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

### off('stateChange')

off(type: 'stateChange', callback?: Callback&lt;FloatingBallState&gt;): void

取消闪控球生命周期状态变化的监听事件。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| type | string | 是 | 监听事件，固定为'stateChange'，即闪控球生命周期状态变化事件。 |
| callback | Callback&lt;[FloatingBallState](#floatingballstate)&gt; | 否 | 回调函数。返回当前的闪控球生命周期状态。若传入参数，则停止该监听。若未传入参数，则停止所有闪控球生命周期状态变化的监听。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |

**示例：**

```ts
let onStateChange = (state: floatingBall.FloatingBallState) => {
  console.info('Floating ball stateChange: ' + state);
};
try {
  floatingBallController.off('stateChange', onStateChange);
  floatingBallController.off('stateChange');
} catch(e) {
  console.error(`Failed to off stateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

### on('click')

on(type: 'click', callback: Callback&lt;void&gt;): void

注册闪控球的点击监听事件，不使用时，取消监听以避免内存泄漏。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| type | string | 是 | 监听事件，固定为'click'，即闪控球点击事件。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数。当点击闪控球事件发生时的回调。该回调函数不返回任何参数。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300022 | Repeated floating ball operation. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |

**示例：**

```ts
let onClick = () => {
  console.info('Floating ball onClick');
};
try {
  floatingBallController.on('click', onClick);
} catch(e) {
  console.error(`Failed to on click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

### off('click')

off(type: 'click', callback?: Callback&lt;void&gt;): void

取消闪控球点击的监听事件。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| type | string | 是 | 监听事件，固定为'click'，即闪控球点击事件。 |
| callback | Callback&lt;void&gt; | 否 | 回调函数。当点击闪控球事件发生时的回调。该回调函数不返回任何参数。若传入参数，则关闭特定的监听。若未传入参数，则关闭所有闪控球点击的监听。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |

**示例：**

```ts
let onClick = () => {
  console.info('Floating ball onClick');
};
try {
  floatingBallController.off('click', onClick);
  floatingBallController.off('click');
} catch(e) {
  console.error(`Failed to off click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

### getFloatingBallWindowInfo

getFloatingBallWindowInfo(): Promise&lt;FloatingBallWindowInfo&gt;

获得闪控球窗口信息，使用Promise异步回调。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;[FloatingBallWindowInfo](#floatingballwindowinfo)&gt; | Promise对象，返回闪控球窗口信息。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. |
| 1300003 | This window manager service works abnormally. |
| 1300004 | Unauthorized operation. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |
| 1300025 | The floating ball state does not support this operation. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

floatingBallController.getFloatingBallWindowInfo().then((data: floatingBall.FloatingBallWindowInfo) => {
  console.info('Succeeded in getting floating ball window info. Info: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to get floating ball window info. Cause code: ${err.code}, message: ${err.message}`);
});
```

### restoreMainWindow

restoreMainWindow(want: Want): Promise&lt;void&gt;

恢复应用主窗口并加载指定页面。仅支持在闪控球点击事件回调上下文的5秒内调用，使用Promise异步回调。

**需要权限：** ohos.permission.USE_FLOAT_BALL

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是 | 加载指定页面的Want。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 201 | Permission verification failed, usually returned by VerifyAccessToken. |
| 1300002 | This window state is abnormal. |
| 1300003 | This window manager service works abnormally. |
| 1300004 | Unauthorized operation. |
| 1300019 | Wrong parameters for operating the floating ball. |
| 1300023 | Floating ball internal error. |
| 1300024 | The floating ball window state is abnormal. |
| 1300025 | The floating ball state does not support this operation. |
| 1300026 | Failed to restore the main window. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  bundleName: 'xxx.xxx.xxx',
  abilityName: 'EntryAbility'
};
try {
  floatingBallController.restoreMainWindow(want).then(() => {
    console.info('Succeeded in restoring floating ball main window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore floating ball main window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch(e) {
  console.error(`Failed to create floating ball controller. Cause:${e.code}, message:${e.message}`);
}
```

## FloatingBallParams

启动和更新闪控球的配置参数。

**系统能力：** SystemCapability.Window.SessionManager

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| template | [FloatingBallTemplate](#floatingballtemplate) | 否 | 否 | 闪控球模板。静态布局时，icon必选，content无效；普通文本布局和强调文本布局时，icon无效；纯文本布局时，content和icon均无效。 |
| title | string | 否 | 否 | 闪控球标题，不可为空字符串，大小不超过64字节。 |
| content | string | 否 | 是 | 闪控球内容，可选字段，大小不超过64字节。不传入时默认为空字符串，不显示闪控球内容。 |
| backgroundColor | string | 否 | 是 | 闪控球背景颜色，可选字段，为不带透明度的十六进制颜色格式（例如'#008EF5'或'#FF008EF5'），不传入时闪控球使用默认颜色（浅色模式'#FFFFFF'，深色模式'#000000'）。 |
| icon | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 否 | 是 | 闪控球图标，可选字段，图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../apis-image-kit/arkts-apis-image-PixelMap.md#getpixelbytesnumber7)获取）。建议图标像素宽高为128px*128px。实际显示效果依赖于设备能力和闪控球UI样式，不传入时不显示闪控球图标。 |

## FloatingBallState

闪控球生命周期状态的枚举。

**系统能力：** SystemCapability.Window.SessionManager

| 名称 | 值 | 说明 |
|------------|------------|------------|
| STARTED | 1 | 表示闪控球启动。 |
| STOPPED | 2 | 表示闪控球停止。 |

## FloatingBallTemplate

闪控球模板类型的枚举。

**系统能力：** SystemCapability.Window.SessionManager

| 名称 | 值 | 说明 |
|------------|------------|------------|
| STATIC | 1 | 静态布局，支持图标和标题。 |
| NORMAL | 2 | 普通文本布局，支持标题和内容。 |
| EMPHATIC | 3 | 强调文本布局，支持标题和内容，使用不同字号区分。 |
| SIMPLE | 4 | 纯文本布局，只支持标题，可双行展示。 |

## FloatingBallWindowInfo

闪控球窗口信息。

**系统能力：** SystemCapability.Window.SessionManager

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| windowId | number | 是 | 否 | 闪控球窗口ID。 |