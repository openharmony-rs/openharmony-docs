# CaptionsManager

字幕配置管理，在调用CaptionsManager的方法前，需要先通过 [accessibility.getCaptionsManager()](arkts-accessibility-accessibility-getcaptionsmanager-f.md#getCaptionsManager)获取 CaptionsManager实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-accessibility-interface CaptionsManager--><!--Device-accessibility-interface CaptionsManager-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## offEnableChange

```TypeScript
offEnableChange(callback?: Callback<boolean>): void
```

Unregister the observe of the enable state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CaptionsManager-offEnableChange(callback?: Callback<boolean>): void--><!--Device-CaptionsManager-offEnableChange(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 |  |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`caption state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.onEnableChange(this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.offEnableChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## offStyleChange

```TypeScript
offStyleChange(callback?: Callback<CaptionsStyle>): void
```

Unregister the observer of the style.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CaptionsManager-offStyleChange(callback?: Callback<CaptionsStyle>): void--><!--Device-CaptionsManager-offStyleChange(callback?: Callback<CaptionsStyle>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt; | 否 |  |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`caption style change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.onStyleChange(this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.offStyleChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## off_enableChange

```TypeScript
off(type: 'enableChange', callback?: Callback<boolean>): void
```

取消监听字幕配置启用状态变化事件，使用callback异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 12

<!--Device-CaptionsManager-off(type: 'enableChange', callback?: Callback<boolean>): void--><!--Device-CaptionsManager-off(type: 'enableChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'enableChange' | 是 | 取消监听的事件名，固定为‘enableChange’，即字幕配置启用状态变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与 [on('enableChange')](#on_enableChange) 的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## off_styleChange

```TypeScript
off(type: 'styleChange', callback?: Callback<CaptionsStyle>): void
```

取消字幕风格变化监听事件，使用callback异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 12

<!--Device-CaptionsManager-off(type: 'styleChange', callback?: Callback<CaptionsStyle>): void--><!--Device-CaptionsManager-off(type: 'styleChange', callback?: Callback<CaptionsStyle>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'styleChange' | 是 | 取消监听的事件名，固定为‘styleChange’，即字幕风格变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与 [on('styleChange')](#on_enableChange) 的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## onEnableChange

```TypeScript
onEnableChange(callback: Callback<boolean>): void
```

Register the observe of the enable state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CaptionsManager-onEnableChange(callback: Callback<boolean>): void--><!--Device-CaptionsManager-onEnableChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 |  |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`caption state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.onEnableChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## onStyleChange

```TypeScript
onStyleChange(callback: Callback<CaptionsStyle>): void
```

Register the observer of the style.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CaptionsManager-onStyleChange(callback: Callback<CaptionsStyle>): void--><!--Device-CaptionsManager-onStyleChange(callback: Callback<CaptionsStyle>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt; | 是 |  |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`caption style change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.onStyleChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## on_enableChange

```TypeScript
on(type: 'enableChange', callback: Callback<boolean>): void
```

监听字幕配置启用状态变化事件，使用callback异步回调。 > **说明：** > > - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。 > > - 调用此方法后，务必在对象生命周期结束前使用 > [off('enableChange')](#off_enableChange) > 取消监听，否则可能会导致崩溃。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 12

<!--Device-CaptionsManager-on(type: 'enableChange', callback: Callback<boolean>): void--><!--Device-CaptionsManager-on(type: 'enableChange', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'enableChange' | 是 | 监听的事件名，固定为‘enableChange’，即字幕配置启用状态变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | 回调函数，在启用状态变化时将状态通过此函数进行通知。返回true表示字幕配置开启，返回false表示字幕配置关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## on_styleChange

```TypeScript
on(type: 'styleChange', callback: Callback<CaptionsStyle>): void
```

监听字幕风格变化事件，使用callback异步回调。 > **说明：** > > - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。 > > - 调用此方法后，务必在对象生命周期结束前使用 > [off('styleChange')](#off_enableChange) > 取消监听，否则可能会导致崩溃。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 12

<!--Device-CaptionsManager-on(type: 'styleChange', callback: Callback<CaptionsStyle>): void--><!--Device-CaptionsManager-on(type: 'styleChange', callback: Callback<CaptionsStyle>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'styleChange' | 是 | 监听的事件名，固定为‘styleChange’，即字幕风格变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt; | 是 | 回调函数，在字幕风格变化时通过此函数进行通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## enabled

```TypeScript
enabled: boolean
```

表示是否启用字幕配置。true表示字幕配置开启，false表示字幕配置关闭。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsManager-enabled: boolean--><!--Device-CaptionsManager-enabled: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## style

```TypeScript
style: CaptionsStyle
```

表示字幕风格。

**类型：** [CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsManager-style: CaptionsStyle--><!--Device-CaptionsManager-style: CaptionsStyle-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

