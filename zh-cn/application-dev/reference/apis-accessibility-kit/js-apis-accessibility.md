# @ohos.accessibility (辅助功能)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->

本模块提供辅助应用查询能力，包括获取辅助应用列表、获取辅助应用启用状态、获取无障碍字幕配置等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从 API version 7 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { accessibility } from '@kit.AccessibilityKit';
```

## AbilityState

type AbilityState = 'enable' | 'disable' | 'install'

辅助应用状态类型。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：23

| 类型      | 说明       |
| ------- | -------- |
| 'enable'  | 表示辅助应用已启用。 |
| 'disable'  | 表示辅助应用已禁用。 |
| 'install'  | 表示辅助应用已安装。 |

## AbilityType

type AbilityType = 'audible' | 'generic' | 'haptic' | 'spoken' | 'visual' | 'all'

无障碍辅助应用类型。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

| 类型               | 说明        |
| ---------------- | --------- |
| audible          | 表示具有听觉反馈。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23|
| generic          | 表示具有通用反馈。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| haptic           | 表示具有触觉反馈。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| spoken           | 表示具有语音反馈。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| visual           | 表示具有视觉反馈。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| all<sup>9+</sup> | 表示以上所有类别。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23 |

## AccessibilityAbilityInfo

辅助应用信息。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

### 属性

| 名称                             | 类型                                       | 只读   | 可选   | 说明               |
| ------------------------------ | ---------------------------------------- | ---- | ---- | ---------------- |
| id                             | string                                   | 是    | 否    | ability&nbsp;id。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| name                           | string                                   | 是    | 否    | ability 名。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23       |
| bundleName                     | string                                   | 是    | 否    | Bundle名称。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23        |
| targetBundleNames<sup>9+</sup> | Array&lt;string&gt;                      | 是    | 否    | 关注的目标Bundle名称。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23   |
| abilityTypes                   | Array&lt;[AbilityType](#abilitytype)&gt; | 是    | 否    | 辅助应用类型。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23          |
| capabilities                   | Array&lt;[Capability](#capability)&gt;   | 是    | 否    | 辅助应用能力列表。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23        |
| description                    | string                                   | 是    | 否    | 辅助应用描述。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23          |
| eventTypes                     | Array&lt;[EventType](#eventtype)&gt;     | 是    | 否    | 辅助应用关注的无障碍事件列表。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23  |
| needHide<sup>12+</sup>                     | boolean     | 是    | 否    | 辅助应用是否在已安装的扩展服务列表中被隐藏，true表示隐藏服务，false表示显示服务。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23  |
| label<sup>12+</sup>                     | string     | 是    | 否    | 扩展应用在扩展服务列表中的名称。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23  |

## Action

type Action = 'accessibilityFocus' | 'clearAccessibilityFocus' | 'focus' | 'clearFocus' | 'clearSelection' |
  'click' | 'longClick' | 'cut' | 'copy' | 'paste' | 'select' | 'setText' | 'delete' |
  'scrollForward' | 'scrollBackward' | 'setSelection' | 'setCursorPosition' | 'home' |
  'back' | 'recentTask' | 'notificationCenter' | 'controlCenter' | 'common' | 'injectAction' | 'executeCustomAction'

应用所支持的目标动作，需要配置参数的目标动作已在描述中标明。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

| 类型                      | 说明                 |
| ----------------------- |--------------------|
| 'click'                   | 表示点击操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'longClick'               | 表示长按操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'scrollForward'           | 表示向前滚动操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'scrollBackward'          | 表示向后滚动操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'focus'                   | 表示获得焦点操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'clearFocus'              | 表示清除焦点操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'clearSelection'          | 表示清除选择操作。当前版本暂不支持。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'accessibilityFocus'      | 表示获得无障碍焦点操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'clearAccessibilityFocus'      | 表示清除无障碍焦点操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'cut'                     | 表示剪切操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'copy'                    | 表示复制操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'paste'                   | 表示粘贴操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'select'                  | 表示选择操作。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'setText'                 | 表示设置文本操作，需配置参数setText。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'delete'                  | 表示删除操作。当前版本暂不支持。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'setSelection'            | 表示选择操作，需配置参数selectTextBegin、selectTextEnd、selectTextInForWard。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'common'<sup>12+</sup>            | 表示没有特定操作，用于主动聚焦、主动播报等场景。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'home'<sup>12+</sup>                | 表示返回桌面操作。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'back'<sup>12+</sup>                | 表示返回上一级操作。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'recentTask'<sup>12+</sup>          | 表示打开最近任务操作。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'notificationCenter'<sup>12+</sup>      | 表示打开通知栏操作。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'controlCenter'<sup>12+</sup>       | 表示打开控制中心操作。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'setCursorPosition'<sup>12+</sup>     | 表示设置光标位置操作，需配置参数offset。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'injectAction'          | 表示注入动作，需配置参数injectActionType。<br>**模型约束**：此接口仅可在Stage模型下使用。<br>**ArkTS-Dyn起始版本**：26.0.0<br>**ArkTS-Sta起始版本**：26.0.0 |
| 'executeCustomAction'     | 表示执行自定义操作，需配置参数customAction。<br>**模型约束**：此接口仅可在Stage模型下使用。<br>**ArkTS-Dyn起始版本**：26.0.0<br>**ArkTS-Sta起始版本**：26.0.0 |

## Capability

type Capability = 'retrieve' | 'touchGuide' | 'keyEventObserver' | 'zoom' | 'gesture'

辅助应用能力类型。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：23

| 类型               | 说明                    |
| ---------------- |-----------------------|
| 'retrieve'         | 具有检索窗口内容的能力。          |
| 'touchGuide'       | 具有触摸探索模式的能力。          |
| 'keyEventObserver' | 具有过滤按键事件的能力。          |
| 'zoom'             | 具有控制显示放大的能力，当前版本暂不支持。 |
| 'gesture'          | 具有执行手势动作的能力。          |

## CaptionsFontEdgeType<sup>8+</sup>

type CaptionsFontEdgeType = 'none' | 'raised' | 'depressed' | 'uniform' | 'dropShadow'

字幕字体边缘类型。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：23

| 类型         | 说明    |
| ---------- | ----- |
| 'none'       | 表示无效果。  |
| 'raised'     | 表示凸起效果。 |
| 'depressed'  | 表示凹陷效果。 |
| 'uniform'    | 表示轮廓效果。 |
| 'dropShadow' | 表示阴影效果。 |

## CaptionsFontFamily<sup>8+</sup>

type CaptionsFontFamily = 'default' | 'monospacedSerif' | 'serif' | 'monospacedSansSerif' |
  'sansSerif' | 'casual' | 'cursive' | 'smallCapitals'

字幕字体。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：23

| 类型                  | 说明                |
| ------------------- | ----------------- |
| 'default'             | 表示默认字体。             |
| 'monospacedSerif'         | 表示等宽 Serif 字体。      |
| 'serif'               | 表示Serif 字体。         |
| 'monospacedSansSerif'        | 表示等宽 Sans Serif 字体。 |
| 'sansSerif'           | 表示Sans Serif 字体。    |
| 'casual'              | 表示非正式字体。            |
| 'cursive'             | 表示手写字体。             |
| 'smallCapitals'       | 表示小型大写字母字体。         |

## CaptionsStyle<sup>8+</sup>

字幕风格。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：23

| 名称              | 类型                                    | 只读   | 可选   | 说明          |
| --------------- | ---------------------------------------- | ---- | ---- | ----------- |
| fontFamily      | [CaptionsFontFamily](#captionsfontfamily8) | 否    | 否    | 描述字幕字体。     |
| fontScale       | ArkTS-Dyn: number<br>ArkTS-Sta: int        | 否    | 否    | 描述字幕字体缩放系数，单位%，参数范围1~200。 |
| fontColor       | ArkTS-Dyn: number \| string<br>ArkTS-Sta: int \| string        | 否    | 否    | 描述字幕字体颜色。<br>number \| int：HEX 格式颜色，支持 rgb 或 argb。<br>string：支持 '#rrggbb', '#rrggbbaa', '#rgb', '#rgba' 格式。<br>例：不透明红色，number: 0xffff0000，string: '#ff0000', '#ff0000ff', '#f00', '#f00f'。 |
| fontEdgeType    | [CaptionsFontEdgeType](#captionsfontedgetype8) | 否    | 否    | 描述字幕字体边缘。   |
| backgroundColor | ArkTS-Dyn: number \| string<br>ArkTS-Sta: int \| string        | 否    | 否    | 描述字幕背景颜色。<br>number \| int：HEX 格式颜色，支持 rgb 或 argb。<br>string：支持 '#rrggbb', '#rrggbbaa', '#rgb', '#rgba' 格式。<br>例：不透明红色，number: 0xffff0000，string: '#ff0000', '#ff0000ff', '#f00', '#f00f'。   |
| windowColor     | ArkTS-Dyn: number \| string<br>ArkTS-Sta: int \| string        | 否    | 否    | 描述字幕窗口颜色。<br>number \| int：HEX 格式颜色，支持 rgb 或 argb。<br>string：支持 '#rrggbb', '#rrggbbaa', '#rgb', '#rgba' 格式。<br>例：不透明红色，number: 0xffff0000，string: '#ff0000', '#ff0000ff', '#f00', '#f00f'。   |

## CaptionsManager<sup>8+</sup>

字幕配置管理，在调用CaptionsManager的方法前，需要先通过 [accessibility.getCaptionsManager() ](#accessibilitygetcaptionsmanagerdeprecated)获取 CaptionsManager实例。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：23

### 属性

| 名称      | 类型                               | 只读   | 可选   | 说明          |
| ------- | -------------------------------- | ---- | ---- | ----------- |
| enabled | boolean                          | 否    | 否    | 表示是否启用字幕配置。true表示字幕配置开启，false表示字幕配置关闭。 |
| style   | [CaptionsStyle](#captionsstyle8) | 否    | 否    | 表示字幕风格。     |

### on('enableChange')<sup>(deprecated)</sup>

on(type: 'enableChange', callback: Callback&lt;boolean&gt;): void

监听字幕配置启用状态变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[off('enableChange')](#offenablechangedeprecated)取消监听，否则可能会导致崩溃。
> - 从API version 8开始支持，从API version 12开始废弃。系统不再开放相关功能。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[onEnableChange](#onenablechange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                      |
| -------- | ----------------------- | ---- | --------------------------------------- |
| type     | string                  | 是    | 监听的事件名，固定为‘enableChange’，即字幕配置启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是    | 回调函数，在启用状态变化时将状态通过此函数进行通知。返回true表示字幕配置开启，返回false表示字幕配置关闭。              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
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

### onEnableChange<sup>23+</sup>

onEnableChange(callback: Callback\<boolean\>): void

监听字幕配置启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[on('enableChange')](#onenablechangedeprecated)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                      |
| -------- | ----------------------- | ---- | --------------------------------------- |
| callback | Callback&lt;boolean&gt; | 是    | 回调函数，在启用状态变化时将状态通过此函数进行通知。              |

**示例：**

```ts
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

### on('styleChange')<sup>(deprecated)</sup>

on(type: 'styleChange', callback: Callback&lt;CaptionsStyle&gt;): void

监听字幕风格变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[off('styleChange')](#offstylechangedeprecated)取消监听，否则可能会导致崩溃。
> - 从API version 8开始支持，从API version 12开始废弃。系统不再开放相关功能。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[onStyleChange](#onstylechange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                 |
| -------- | ---------------------------------------- | ---- | ---------------------------------- |
| type     | string                                   | 是    | 监听的事件名，固定为‘styleChange’，即字幕风格变化事件。 |
| callback | Callback&lt;[CaptionsStyle](#captionsstyle8)&gt; | 是    | 回调函数，在字幕风格变化时通过此函数进行通知。            |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
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

### onStyleChange<sup>23+</sup>

onStyleChange(callback: Callback\<CaptionsStyle\>): void

监听字幕风格变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[on('styleChange')](#onstylechangedeprecated)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                 |
| -------- | ---------------------------------------- | ---- | ---------------------------------- |
| callback | Callback&lt;[CaptionsStyle](#captionsstyle8)&gt; | 是    | 回调函数，在字幕风格变化时通过此函数进行通知。            |

**示例：**

```ts
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

### off('enableChange')<sup>(deprecated)</sup>

off(type: 'enableChange', callback?: Callback&lt;boolean&gt;): void

取消监听字幕配置启用状态变化事件。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 12开始废弃。系统不再开放相关功能。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[offEnableChange](#offenablechange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | 是   | 取消监听的事件名，固定为‘enableChange’，即字幕配置启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与[on('enableChange')](#onenablechangedeprecated)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
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

### offEnableChange<sup>23+</sup>

offEnableChange(callback?: Callback\<boolean\>): void

取消监听字幕配置启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[off('enableChange')](#offenablechangedeprecated)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与onEnableChange的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
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

### off('styleChange')<sup>(deprecated)</sup>

off(type: 'styleChange', callback?: Callback&lt;CaptionsStyle&gt;): void

取消字幕风格变化监听事件。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 12开始废弃。系统不再开放相关功能。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[offStyleChange](#offstylechange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**参数：**

| 参数名   | 类型                                             | 必填 | 说明                                                         |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                           | 是   | 取消监听的事件名，固定为‘styleChange’，即字幕风格变化事件。  |
| callback | Callback&lt;[CaptionsStyle](#captionsstyle8)&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与[on('styleChange')](#onstylechangedeprecated)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
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

### offStyleChange<sup>23+</sup>

offStyleChange(callback?: Callback\<CaptionsStyle\>): void

取消字幕风格变化监听事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[off('styleChange')](#offstylechangedeprecated)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                                             | 必填 | 说明                                                         |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[CaptionsStyle](#captionsstyle8)&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与onStyleChange的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
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

## EventInfo

界面变更事件。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

### 属性

| 名称             | 类型                                   | 只读 | 可选 | 说明            |
| ---------------- | ------------------------------------- |----- |------|-----------------------|
| type             | [EventType](#eventtype)               | 否   | 否   | 无障碍事件类型，不可缺省。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23    |
| windowUpdateType | [WindowUpdateType](#windowupdatetype) | 否   | 是   | 窗口变化类型。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23      |
| bundleName       | string                                | 否   | 否   | 目标应用名；不可缺省。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23   |
| componentType    | string                                | 否   | 是   | 事件源组件类型，如按钮、图表。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23   |
| pageId           | ArkTS-Dyn: number<br>ArkTS-Sta: int   | 否   | 是   | 事件源的页面ID。默认值为0。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23   |
| description      | string                                | 否   | 是   | 事件描述。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23   |
| triggerAction    | [Action](#action)                     | 否   | 否   | 触发事件的Action，不可缺省。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23  |
| textMoveUnit     | [TextMoveUnit](#textmoveunit)         | 否   | 是   | 文本移动粒度。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23  |
| contents         | Array&lt;string&gt;                   | 否   | 是   | 内容列表。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23     |
| lastContent      | string                                | 否   | 是   | 最新内容。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23   |
| beginIndex       | ArkTS-Dyn: number<br>ArkTS-Sta: int   | 否   | 是   | 画面显示条目的开始序号。默认值为0。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| currentIndex     | ArkTS-Dyn: number<br>ArkTS-Sta: int   | 否   | 是   | 当前条目序号。默认值为0。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23   |
| endIndex         | ArkTS-Dyn: number<br>ArkTS-Sta: int   | 否   | 是   | 画面显示条目的结束序号。默认值为0。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| itemCount        | ArkTS-Dyn: number<br>ArkTS-Sta: int   | 否   | 是   | 条目总数。默认值为0。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23   |
| elementId<sup>12+</sup> | ArkTS-Dyn: number<br>ArkTS-Sta: int    | 否   | 是   | 组件elementId。默认值为0。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23  |
| textAnnouncedForAccessibility<sup>12+</sup>     | string     | 否   | 是   | 主动播报的内容。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23    |
| textResourceAnnouncedForAccessibility<sup>18+</sup>      | Resource   | 否   | 是   | 主动播报的内容支持传入Resource类型，Resource类型只支持传入string。<br>**ArkTS-Dyn起始版本**：18<br>**ArkTS-Sta起始版本**：23  |
| customId<sup>12+</sup>        | string                                | 否   | 是   | 主动聚焦的组件ID。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23  |

### constructor

constructor(jsonObject: Object)

构造函数，通过JSON对象构造EventInfo实例。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[constructor](#constructor23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名        | 类型     | 必填   | 说明                   |
| ---------- | ------ | ---- | -------------------- |
| jsonObject | Object | 是    | 包含 type、bundleName 和 triggerAction 三个字段的 JSON对象，详见示例。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});
```

### constructor<sup>23+</sup>

constructor()

构造函数。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[constructor](#constructor)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});
```

### constructor<sup>11+</sup>

constructor(type: EventType, bundleName: string, triggerAction: Action)

构造函数，通过独立参数构造EventInfo实例。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名  | 类型                | 必填 | 说明            |
|------|-------------------|---|---------------|
| type | [EventType](#eventtype)          | 是 | 无障碍事件类型。      |
| bundleName | string | 是 | 目标应用名。        |
| triggerAction | [Action](#action) | 是 | 触发事件的 Action。 |

**示例：**

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';

  let eventInfo = new accessibility.EventInfo('click', 'com.example.MyApplication', 'click');
  ```

## EventType

type EventType = 'accessibilityFocus' | 'accessibilityFocusClear' |
'click' | 'longClick' | 'focus' | 'select' | 'hoverEnter' | 'hoverExit' |
'textUpdate' | 'textSelectionUpdate' | 'scroll' | 'requestFocusForAccessibility' |
'announceForAccessibility' | 'requestFocusForAccessibilityNotInterrupt' |
'announceForAccessibilityNotInterrupt' | 'scrolling' | 'pageActive' | 'notificationUpdate' | 'focusInvisible'

无障碍事件类型。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

| 类型                      | 说明                     |
| ----------------------- |------------------------|
| 'accessibilityFocus'      | 表示获得无障碍焦点的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'accessibilityFocusClear' | 表示清除无障碍焦点的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'click'                   | 表示点击组件的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'longClick'               | 表示长按组件的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'select'                  | 表示选择组件的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'hoverEnter'              | 表示悬停进入组件的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'hoverExit'               | 表示悬停离开组件的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'focus'                   | 表示组件获得焦点的事件，当前版本暂不支持。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'textUpdate'              | 表示组件文本已更改的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'textSelectionUpdate'     | 表示选定文本已更改的事件，当前版本暂不支持。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'scroll'                  | 表示滚动视图的事件。<br>**ArkTS-Dyn起始版本**：7<br>**ArkTS-Sta起始版本**：23 |
| 'requestFocusForAccessibility'<sup>12+</sup>     | 表示主动聚焦的事件。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'announceForAccessibility'<sup>12+</sup>         | 表示主动播报的事件。<br>**ArkTS-Dyn起始版本**：12<br>**ArkTS-Sta起始版本**：23 |
| 'requestFocusForAccessibilityNotInterrupt'<sup>18+</sup> | 表示主动聚焦不打断的事件。<br>**ArkTS-Dyn起始版本**：18<br>**ArkTS-Sta起始版本**：23 |
| 'announceForAccessibilityNotInterrupt'<sup>18+</sup>  | 表示主动播报不打断的事件。<br>**ArkTS-Dyn起始版本**：18<br>**ArkTS-Sta起始版本**：23 |
| 'scrolling'<sup>18+</sup>   | 表示滚动视图中有item被滚出屏幕的事件。<br>**ArkTS-Dyn起始版本**：18<br>**ArkTS-Sta起始版本**：23 |
| 'pageActive'<sup>23+</sup> | 表示页面变化的事件，值固定为'pageActive'字符串。<br>**ArkTS-Dyn起始版本**：23<br>**ArkTS-Sta起始版本**：23 |
| 'notificationUpdate' | 表示通知变化的事件，值固定为'notificationUpdate'字符串。<br>**模型约束**：此接口仅可在Stage模型下使用。<br>**ArkTS-Dyn起始版本**：26.0.0<br>**ArkTS-Sta起始版本**：26.0.0 |
| 'focusInvisible' | 表示焦点变为不可见状态，值固定为'focusInvisible'字符串。<br>**模型约束**：此接口仅可在Stage模型下使用。<br>**ArkTS-Dyn起始版本**：26.0.0<br>**ArkTS-Sta起始版本**：26.0.0 |

## TextMoveUnit

type TextMoveUnit = 'char' | 'word' | 'line' | 'page' | 'paragraph'

文本无障碍导航移动粒度。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：23

| 类型        | 说明              |
| --------- | --------------- |
| 'char'      | 表示以字符为移动粒度遍历节点文本。 |
| 'word'      | 表示以词为移动粒度遍历节点文本。  |
| 'line'      | 表示以行为移动粒度遍历节点文本。  |
| 'page'      | 表示以页为移动粒度遍历节点文本。  |
| 'paragraph' | 表示以段落为移动粒度遍历节点文本。 |

## WindowUpdateType

type WindowUpdateType = 'add' | 'remove' | 'bounds' | 'active' | 'focus'

窗口变化类型。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：23

| 类型     | 说明                 |
| ------ | ------------------ |
| 'add'    | 表示添加窗口的窗口变化事件，值固定为'add'字符串。       |
| 'remove' | 表示一个窗口被删除的窗口变化事件，值固定为'remove'字符串。    |
| 'bounds' | 表示窗口边界已更改的窗口变化事件，值固定为'bounds'字符串。    |
| 'active' | 表示窗口变为活动或不活动的窗口变化事件，值固定为'active'字符串。 |
| 'focus'  | 表示窗口焦点发生变化的窗口变化事件，值固定为'focus'字符串。   |

## accessibility.getAbilityLists<sup>(deprecated)</sup>

getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;

查询辅助应用列表。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用[accessibility.getAccessibilityExtensionList](#accessibilitygetaccessibilityextensionlist9)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名         | 类型                            | 必填   | 说明       |
| ----------- | ----------------------------- | ---- | -------- |
| abilityType | [AbilityType](#abilitytype)   | 是    | 辅助应用的类型。 |
| stateType   | [AbilityState](#abilitystate) | 是    | 辅助应用的状态。 |

**返回值：**

| 类型                                       | 说明                    |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | Promise对象，返回辅助应用信息列表。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.getAbilityLists<sup>(deprecated)</sup>

getAbilityLists(abilityType: AbilityType, stateType: AbilityState,callback: AsyncCallback&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;): void

查询辅助应用列表。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用[accessibility.getAccessibilityExtensionList](#accessibilitygetaccessibilityextensionlist9-1)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名         | 类型                                       | 必填   | 说明               |
| ----------- | ---------------------------------------- | ---- | ---------------- |
| abilityType | [AbilityType](#abilitytype)              | 是    | 辅助应用的类型。         |
| stateType   | [AbilityState](#abilitystate)            | 是    | 辅助应用的状态。         |
| callback    | AsyncCallback&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | 是    | 回调函数，返回辅助应用信息列表。若返回成功，err为undefined，data为辅助应用信息列表；否则为错误对象。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
})
```

## accessibility.getAccessibilityExtensionList<sup>9+</sup>

getAccessibilityExtensionList(abilityType: AbilityType, stateType: AbilityState): Promise&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;

查询辅助应用列表。使用Promise异步回调。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名         | 类型                            | 必填   | 说明       |
| ----------- | ----------------------------- | ---- | -------- |
| abilityType | [AbilityType](#abilitytype)   | 是    | 辅助应用的类型。 |
| stateType   | [AbilityState](#abilitystate) | 是    | 辅助应用的状态。 |

**返回值：**

| 类型                                       | 说明                    |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | Promise对象，返回辅助应用信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**参数示例：**
| 辅助应用类型 \ 辅助应用状态      | enable       | disable |install|
| ------- | -------- |----|----|
| **audible**  | 查询已启用的具有听觉反馈的辅助应用 |查询已禁用的具有听觉反馈的辅助应用|查询已安装的具有听觉反馈的辅助应用|
|**generic**| 查询已启用的具有通用反馈的辅助应用 |查询已禁用的具有通用反馈的辅助应用|查询已安装的具有通用反馈的辅助应用|
|**haptic**| 查询已启用的具有触觉反馈的辅助应用 |查询已禁用的具有触觉反馈的辅助应用|查询已安装的具有触觉反馈的辅助应用|
|**spoken**| 查询已启用的具有语音反馈的辅助应用 |查询已禁用的具有语音反馈的辅助应用|查询已安装的具有语音反馈的辅助应用|
|**visual**| 查询已启用的具有视觉反馈的辅助应用 |查询已禁用的具有视觉反馈的辅助应用|查询已安装的具有视觉反馈的辅助应用|
|**all**| 查询所有已启用的辅助应用 |查询所有已禁用的辅助应用|查询所有已安装的辅助应用|

**示例：**

- 查询所有已安装的辅助应用。

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'all'; // 辅助应用类型为所有类型。
  let abilityState: accessibility.AbilityState = 'install'; // 辅助应用状态为已安装。

  accessibility.getAccessibilityExtensionList(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
  });

  // 例如：系统内安装一个包名为com.example.myaccessibilityapp的辅助应用。
  // 日志打印结果为：
  // [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
  // "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
  // "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
  // "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
  // "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
  // "announceForAccessibility","announceForAccessibilityNotInterrupt",
  // "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
  ```

- 查询所有已启用的具有语音反馈的辅助应用。

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'spoken'; // 辅助应用类型为具有语音反馈类型。
  let abilityState: accessibility.AbilityState = 'enable'; // 辅助应用状态为已启用。

  accessibility.getAccessibilityExtensionList(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
  });
  ```

## accessibility.getAccessibilityExtensionList<sup>9+</sup>

getAccessibilityExtensionList(abilityType: AbilityType, stateType: AbilityState, callback: AsyncCallback&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;): void

查询辅助应用列表。使用callback异步回调。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名         | 类型                                       | 必填   | 说明               |
| ----------- | ---------------------------------------- | ---- | ---------------- |
| abilityType | [AbilityType](#abilitytype)              | 是    | 辅助应用的类型。         |
| stateType   | [AbilityState](#abilitystate)            | 是    | 辅助应用的状态。         |
| callback    | AsyncCallback&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | 是    | 回调函数，返回辅助应用信息列表。若返回成功，err为undefined，data为辅助应用信息列表；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**参数示例：**
| 辅助应用类型 \ 辅助应用状态      | enable       | disable |install|
| ------- | -------- |----|----|
| **audible**  | 查询已启用的具有听觉反馈的辅助应用 |查询已禁用的具有听觉反馈的辅助应用|查询已安装的具有听觉反馈的辅助应用|
|**generic**| 查询已启用的具有通用反馈的辅助应用 |查询已禁用的具有通用反馈的辅助应用|查询已安装的具有通用反馈的辅助应用|
|**haptic**| 查询已启用的具有触觉反馈的辅助应用 |查询已禁用的具有触觉反馈的辅助应用|查询已安装的具有触觉反馈的辅助应用|
|**spoken**| 查询已启用的具有语音反馈的辅助应用 |查询已禁用的具有语音反馈的辅助应用|查询已安装的具有语音反馈的辅助应用|
|**visual**| 查询已启用的具有视觉反馈的辅助应用 |查询已禁用的具有视觉反馈的辅助应用|查询已安装的具有视觉反馈的辅助应用|
|**all**| 查询所有已启用的辅助应用 |查询所有已禁用的辅助应用|查询所有已安装的辅助应用|

**示例：**

- 查询所有已安装的辅助应用ArkTS-Dyn示例。

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'all'; // 辅助应用类型为所有类型。
let abilityState: accessibility.AbilityState = 'install'; // 辅助应用状态为已安装。

accessibility.getAccessibilityExtensionList(abilityType, abilityState,(err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});

// 例如：系统内安装一个包名为com.example.myaccessibilityapp的辅助应用。
// 日志打印结果为：
// [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
// "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
// "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
// "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
// "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
// "announceForAccessibility","announceForAccessibilityNotInterrupt",
// "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
```

- 查询所有已安装的辅助应用ArkTS-Sta示例。

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'all'; // 辅助应用类型为所有类型。
let abilityState: accessibility.AbilityState = 'install'; // 辅助应用状态为已安装。

accessibility.getAccessibilityExtensionList(abilityType, abilityState,(err: BusinessError | null, data: accessibility.AccessibilityAbilityInfo[] | undefined) => {
  if (err?.code) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});
```

- 查询所有已启用的具有语音反馈的辅助应用ArkTS-Dyn示例。

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken'; // 辅助应用类型为具有语音反馈类型。
let abilityState: accessibility.AbilityState = 'enable'; // 辅助应用状态为已启用。

accessibility.getAccessibilityExtensionList(abilityType, abilityState,(err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});
```

- 查询所有已启用的具有语音反馈的辅助应用ArkTS-Sta示例。

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken'; // 辅助应用类型为具有语音反馈类型。
let abilityState: accessibility.AbilityState = 'enable'; // 辅助应用状态为已启用。

accessibility.getAccessibilityExtensionList(abilityType, abilityState,(err: BusinessError | null, data: accessibility.AccessibilityAbilityInfo[] | undefined) => {
  if (err?.code) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});
```

## accessibility.getAccessibilityExtensionListSync<sup>12+</sup>

getAccessibilityExtensionListSync(abilityType: AbilityType, stateType: AbilityState): Array&lt;AccessibilityAbilityInfo&gt;

查询当前系统内辅助应用列表，支持按条件查询。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名         | 类型                            | 必填   | 说明       |
| ----------- | ----------------------------- | ---- | -------- |
| abilityType | [AbilityType](#abilitytype)   | 是    | 辅助应用的类型。 |
| stateType   | [AbilityState](#abilitystate) | 是    | 辅助应用的状态。 |

**返回值：**

| 类型                                       | 说明                    |
| ---------------------------------------- | --------------------- |
| Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt; | 返回辅助应用信息列表。 |

**参数示例：**
| 辅助应用类型 \ 辅助应用状态      | enable       | disable |install|
| ------- | -------- |----|----|
| **audible**  | 查询已启用的具有听觉反馈的辅助应用 |查询已禁用的具有听觉反馈的辅助应用|查询已安装的具有听觉反馈的辅助应用|
|**generic**| 查询已启用的具有通用反馈的辅助应用 |查询已禁用的具有通用反馈的辅助应用|查询已安装的具有通用反馈的辅助应用|
|**haptic**| 查询已启用的具有触觉反馈的辅助应用 |查询已禁用的具有触觉反馈的辅助应用|查询已安装的具有触觉反馈的辅助应用|
|**spoken**| 查询已启用的具有语音反馈的辅助应用 |查询已禁用的具有语音反馈的辅助应用|查询已安装的具有语音反馈的辅助应用|
|**visual**| 查询已启用的具有视觉反馈的辅助应用 |查询已禁用的具有视觉反馈的辅助应用|查询已安装的具有视觉反馈的辅助应用|
|**all**| 查询所有已启用的辅助应用 |查询所有已禁用的辅助应用|查询所有已安装的辅助应用|

**示例：**

- 查询所有已安装的辅助应用。

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'all'; // 辅助应用类型为所有类型。
  let abilityState: accessibility.AbilityState = 'install'; // 辅助应用状态为已安装。
  let data: accessibility.AccessibilityAbilityInfo[];

  try {
    data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
  }

  // 例如：系统内安装一个包名为com.example.myaccessibilityapp的辅助应用。
  // 日志打印结果为：
  // [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
  // "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
  // "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
  // "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
  // "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
  // "announceForAccessibility","announceForAccessibilityNotInterrupt",
  // "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
  ```

- 查询所有已启用的具有语音反馈的辅助应用。

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'spoken'; // 辅助应用类型为具有语音反馈类型。
  let abilityState: accessibility.AbilityState = 'enable'; // 辅助应用状态为已启用。
  let data: accessibility.AccessibilityAbilityInfo[];

  try {
    data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
  }
  ```

<!--RP1-->
<!--RP1End-->

## accessibility.getCaptionsManager<sup>(deprecated)</sup>

getCaptionsManager(): CaptionsManager

获取无障碍字幕配置管理实例。

> **说明：**
>
> 从API version 8开始支持，从API version 12开始废弃。系统不再开放相关功能。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Hearing

**ArkTS-Dyn起始版本**：8

**返回值：**

| 类型                                   | 说明         |
| ------------------------------------ | ---------- |
| [CaptionsManager](#captionsmanager8) | 无障碍字幕配置管理。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let captionsManager = accessibility.getCaptionsManager();
```

## accessibility.on('accessibilityStateChange')

on(type: 'accessibilityStateChange', callback: Callback&lt;boolean&gt;): void

监听辅助应用启用状态变化事件。使用callback异步回调。如需获取系统内辅助应用信息，推荐使用[accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12)。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.off('accessibilityStateChange')](#accessibilityoffaccessibilitystatechange)取消监听，否则可能会导致崩溃。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[onAccessibilityStateChange](#accessibilityonaccessibilitystatechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | 是   | 监听的事件名，固定为‘accessibilityStateChange’，即辅助应用启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数，在辅助应用启用状态变化时将状态通过此函数进行通知。此状态为全局辅助应用启用状态。返回true表示已启用辅助应用，返回false表示已禁用辅助应用。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// 系统内已安装一个或多个辅助应用时:
// 1. 启用辅助应用场景：第一个辅助应用启用后，回调函数会返回true。
// 2. 禁用辅助应用场景：若一个或多个辅助应用已启用，最后一个已启用的辅助应用被禁用时，回调函数会返回false。
accessibility.on('accessibilityStateChange', (data: boolean) => {
  console.info(`subscribe accessibility state change, result: ${JSON.stringify(data)}`);
});
```

<!--RP2-->
<!--RP2End-->

## accessibility.onAccessibilityStateChange<sup>23+</sup>

onAccessibilityStateChange(callback: Callback&lt;boolean&gt;): void

监听辅助应用启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[on('accessibilityStateChange')](#accessibilityonaccessibilitystatechange)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数，在辅助应用启用状态变化时将状态通过此函数进行通知。此状态为全局辅助应用启用状态。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`accessibility state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAccessibilityStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.on('touchGuideStateChange')

on(type: 'touchGuideStateChange', callback: Callback&lt;boolean&gt;): void

监听触摸浏览功能启用状态变化事件。使用callback异步回调。如需获取系统内辅助应用信息，推荐使用[accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12)。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.off('touchGuideStateChange')](#accessibilityofftouchguidestatechange)取消监听，否则可能会导致崩溃。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[onTouchGuideStateChange](#accessibilityontouchguidestatechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Vision

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                       |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| type     | string                  | 是    | 监听的事件名，固定为‘touchGuideStateChange’，即触摸浏览启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是    | 回调函数，在触摸浏览启用状态变化时将状态通过此函数进行通知。返回true表示触摸浏览功能已开启，返回false表示触摸浏览功能已关闭。           |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// 系统内已安装一个或多个具备触摸浏览能力的辅助应用（Capability配置中含有'touchGuide'的辅助应用）时：
// 1. 启用触摸浏览辅助应用场景：第一个触摸浏览辅助应用启用后，回调函数会返回true。
// 2. 禁用触摸浏览辅助应用场景：若一个或多个触摸浏览辅助应用已启用，最后一个已启用的触摸浏览辅助应用被禁用时，回调函数会返回false。
accessibility.on('touchGuideStateChange', (data: boolean) => {
  console.info(`subscribe touch guide state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.onTouchGuideStateChange<sup>23+</sup>

onTouchGuideStateChange(callback: Callback&lt;boolean&gt;): void

监听触摸浏览功能启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[on('touchGuideStateChange')](#accessibilityontouchguidestatechange)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Vision

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                       |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| callback | Callback&lt;boolean&gt; | 是    | 回调函数，在触摸浏览启用状态变化时将状态通过此函数进行通知。           |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`touch guide state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onTouchGuideStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.on('screenReaderStateChange')<sup>18+</sup>

on(type: 'screenReaderStateChange', callback: Callback&lt;boolean&gt;): void

监听屏幕朗读功能启用状态变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.off('screenReaderStateChange')](#accessibilityoffscreenreaderstatechange18)取消监听，否则可能会导致崩溃。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[onScreenReaderStateChange](#accessibilityonscreenreaderstatechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：18

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                       |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| type     | string                  | 是    | 监听的事件名，固定为‘screenReaderStateChange’，即屏幕朗读启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是    | 回调函数，在屏幕朗读启用状态变化时将状态通过此函数进行通知。返回true表示屏幕朗读功能已开启，返回false表示屏幕朗读功能已关闭。           |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.on('screenReaderStateChange', (data: boolean) => {
  console.info(`subscribe screen reader state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.onScreenReaderStateChange<sup>23+</sup>

onScreenReaderStateChange(callback: Callback&lt;boolean&gt;): void

监听屏幕朗读功能启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[on('screenReaderStateChange')](#accessibilityonscreenreaderstatechange18)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                       |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| callback | Callback&lt;boolean&gt; | 是    | 回调函数，在屏幕朗读启用状态变化时将状态通过此函数进行通知。           |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`screen reader state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onScreenReaderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.on('touchModeChange')<sup>20+</sup>

on(type: 'touchModeChange', callback: Callback&lt;string&gt;): void

监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.off('touchModeChange')](#accessibilityofftouchmodechange20)取消监听，否则可能会导致崩溃。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[onTouchModeChange](#accessibilityontouchmodechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：20

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                       |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| type     | string                  | 是    | 监听的事件名，固定为‘touchModeChange’，即触摸浏览功能下的单击/双击操作模式变化事件。 |
| callback | Callback&lt;string&gt; | 是    | 回调函数，在触摸浏览功能下的单击/双击操作模式变化时将状态通过此函数进行通知。           |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
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

## accessibility.onTouchModeChange<sup>23+</sup>

onTouchModeChange(callback: Callback&lt;string&gt;): void

监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[on('touchModeChange')](#accessibilityontouchmodechange20)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名      | 类型                      | 必填   | 说明                                       |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| callback | Callback&lt;string&gt; | 是    | 回调函数，在触摸浏览功能下的单击/双击操作模式变化时将状态通过此函数进行通知。           |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`current touch mode: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.onTouchModeChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onAnimationReduceStateChange<sup>23+</sup>

onAnimationReduceStateChange(callback: Callback&lt;boolean&gt;): void

监听减弱动效功能启用状态变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.offAnimationReduceStateChange](#accessibilityoffanimationreducestatechange23)取消监听，否则可能会导致崩溃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数。返回true表示减弱动效模式已开启；返回false表示减弱动效模式已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe animationReduce state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAnimationReduceStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onFlashReminderStateChange<sup>23+</sup>

onFlashReminderStateChange(callback: Callback&lt;boolean&gt;): void

监听闪烁提醒功能启用状态变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.offFlashReminderStateChange](#accessibilityoffflashreminderstatechange23)取消监听，否则可能会导致崩溃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数。返回true表示闪烁提醒模式已开启；返回false表示闪烁提醒模式已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe flashReminder state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onFlashReminderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onAudioMonoStateChange<sup>23+</sup>

onAudioMonoStateChange(callback: Callback&lt;boolean&gt;): void

监听单声道音频功能启用状态变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.offAudioMonoStateChange](#accessibilityoffaudiomonostatechange23)取消监听，否则可能会导致崩溃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数。返回true表示单声道音频模式已开启；返回false表示单声道音频模式已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe audioMono state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAudioMonoStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onSeniorModeStateChange

onSeniorModeStateChange(callback: Callback&lt;boolean&gt;): void

监听系统关怀模式启用状态变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.offSeniorModeStateChange](#accessibilityoffseniormodestatechange)取消监听，否则可能会导致崩溃。


**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数。返回true表示系统关怀模式已开启；返回false表示系统关怀模式已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onSeniorModeStateChangeForSelf

onSeniorModeStateChangeForSelf(callback: Callback&lt;boolean&gt;): void

监听应用自身“长辈模式”变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[accessibility.offSeniorModeStateChangeForSelf](#accessibilityoffseniormodestatechangeforself)取消监听，否则可能会导致崩溃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数。返回true表示应用自身“长辈模式”已开启；返回false表示应用自身“长辈模式”已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: boolean): void => {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('accessibilityStateChange')

off(type: 'accessibilityStateChange', callback?: Callback&lt;boolean&gt;): void

取消监听辅助应用启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[offAccessibilityStateChange](#accessibilityoffaccessibilitystatechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | 是   | 取消监听的事件名，固定为‘accessibilityStateChange’，即辅助应用启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('accessibilityStateChange')](#accessibilityonaccessibilitystatechange)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.off('accessibilityStateChange', (data: boolean) => {
  console.info(`Unsubscribe accessibility state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.offAccessibilityStateChange<sup>23+</sup>

offAccessibilityStateChange(callback?: Callback&lt;boolean&gt;): void

取消监听辅助应用启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[off('accessibilityStateChange')](#accessibilityoffaccessibilitystatechange)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与accessibility.onAccessibilityStateChange的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`accessibility state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAccessibilityStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAccessibilityStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('touchGuideStateChange')

off(type: 'touchGuideStateChange', callback?: Callback&lt;boolean&gt;): void

取消监听触摸浏览启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[offTouchGuideStateChange](#accessibilityofftouchguidestatechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | 是   | 取消监听的事件名，固定为‘touchGuideStateChange’，即触摸浏览启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('touchGuideStateChange')](#accessibilityontouchguidestatechange)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.off('touchGuideStateChange', (data: boolean) => {
  console.info(`Unsubscribe touch guide state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.offTouchGuideStateChange<sup>23+</sup>

offTouchGuideStateChange(callback?: Callback&lt;boolean&gt;): void

取消监听触摸浏览启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[off('touchGuideStateChange')](#accessibilityofftouchguidestatechange)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与accessibility.onTouchGuideStateChange的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`touch guide state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onTouchGuideStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offTouchGuideStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('screenReaderStateChange')<sup>18+</sup>

off(type: 'screenReaderStateChange', callback?: Callback&lt;boolean&gt;): void

取消监听屏幕朗读启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[offScreenReaderStateChange](#accessibilityoffscreenreaderstatechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：18

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | 是   | 取消监听的事件名，固定为‘screenReaderStateChange’，即屏幕朗读启用状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('screenReaderStateChange')](#accessibilityonscreenreaderstatechange18)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.off('screenReaderStateChange', (data: boolean) => {
  console.info(`Unsubscribe screen reader state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.offScreenReaderStateChange<sup>23+</sup>

offScreenReaderStateChange(callback?: Callback&lt;boolean&gt;): void

取消监听屏幕朗读启用状态变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[off('screenReaderStateChange')](#accessibilityoffscreenreaderstatechange18)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与accessibility.onScreenReaderStateChange的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`screen reader state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onScreenReaderStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offScreenReaderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('touchModeChange')<sup>20+</sup>

off(type: 'touchModeChange', callback?: Callback&lt;string&gt;): void

取消监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[offTouchModeChange](#accessibilityofftouchmodechange23)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：20

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | 是   | 取消监听的事件名，固定为‘touchModeChange’，即触摸浏览功能下的单击/双击操作模式变化事件。 |
| callback | Callback&lt;string&gt; | 否   | 回调函数，取消指定callback对象的事件响应。需与[accessibility.on('touchModeChange')](#accessibilityontouchmodechange20)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
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

  aboutToDisappear(): void {
    accessibility.off('touchModeChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offTouchModeChange<sup>23+</sup>

offTouchModeChange(callback?: Callback&lt;string&gt;): void

取消监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[off('touchModeChange')](#accessibilityofftouchmodechange20)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;string&gt; | 否   | 回调函数。取消指定callback对象的事件响应。需与accessibility.onTouchModeChange的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`touch mode change, result: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.onTouchModeChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offTouchModeChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offAnimationReduceStateChange<sup>23+</sup>

offAnimationReduceStateChange(callback?: Callback&lt;boolean&gt;): void

取消监听减弱动效模式变化事件。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数。取消指定callback对象的事件响应。需与[accessibility.onAnimationReduceStateChange](#accessibilityonanimationreducestatechange23)的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe animationReduce state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAnimationReduceStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAnimationReduceStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offFlashReminderStateChange<sup>23+</sup>

offFlashReminderStateChange(callback?: Callback&lt;boolean&gt;): void

取消监听闪烁提醒模式变化事件。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数。取消指定callback对象的事件响应。需与[accessibility.onFlashReminderStateChange](#accessibilityonflashreminderstatechange23)的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe flashReminder state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onFlashReminderStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offFlashReminderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offAudioMonoStateChange<sup>23+</sup>

offAudioMonoStateChange(callback?: Callback&lt;boolean&gt;): void

取消监听单声道音频模式变化事件。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数。取消指定callback对象的事件响应。需与[accessibility.onAudioMonoStateChange](#accessibilityonaudiomonostatechange23)的callback一致。缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe audioMono state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAudioMonoStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAudioMonoStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offSeniorModeStateChange

offSeniorModeStateChange(callback?: Callback&lt;boolean&gt;): void

取消监听系统关怀模式变化事件。使用callback异步回调。


**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数。返回true表示系统关怀模式已开启；返回false表示系统关怀模式已关闭。<br>取消指定callback对象的事件响应。需与[accessibility.onSeniorModeStateChange](#accessibilityonseniormodestatechange)的callback一致。<br>缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offSeniorModeStateChangeForSelf

offSeniorModeStateChangeForSelf(callback?: Callback&lt;boolean&gt;): void

取消监听应用自身“长辈模式”变化事件。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | 否   | 回调函数。返回true表示应用自身“长辈模式”已开启；返回false表示应用自身“长辈模式”已关闭。<br>取消指定callback对象的事件响应。需与[accessibility.onSeniorModeStateChangeForSelf](#accessibilityonseniormodestatechangeforself)的callback一致。<br>缺省时，表示注销所有已注册事件。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: boolean): void => {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChangeForSelf(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isOpenAccessibility<sup>(deprecated)</sup>

isOpenAccessibility(): Promise&lt;boolean&gt;

判断是否启用了辅助应用。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 10开始废弃，建议使用[accessibility.isOpenAccessibilitySync](#accessibilityisopenaccessibilitysync10)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**返回值：**

| 类型                     | 说明                                       |
| ---------------------- | ---------------------------------------- |
| Promise&lt;boolean&gt; | Promise对象，如果辅助应用已启用，则返回 true；否则返回 false。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility().then((data: boolean) => {
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`)
}).catch((err: BusinessError) => {
  console.error(`failed to  isOpenAccessibility, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.isOpenAccessibility<sup>(deprecated)</sup>

isOpenAccessibility(callback: AsyncCallback&lt;boolean&gt;): void

判断是否启用了辅助应用。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 10开始废弃，建议使用[accessibility.isOpenAccessibilitySync](#accessibilityisopenaccessibilitysync10)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名      | 类型                           | 必填   | 说明                                  |
| -------- | ---------------------------- | ---- | ----------------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | 是    | 回调函数，如果辅助应用已启用，则返回 true；否则返回 false。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`failed to isOpenAccessibility, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
});
```

## accessibility.isOpenAccessibilitySync<sup>10+</sup>

isOpenAccessibilitySync(): boolean

查询当前系统内是否存在已开启的辅助应用。如需获取系统内辅助应用信息，推荐使用[accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12)。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值：**
<!--RP3-->
| 类型        | 说明                                  |
| ----------- | ------------------------------------- |
| boolean | 表示当前系统内是否有辅助应用开启。true表示启用了一个或多个辅助应用，false表示未启用任何辅助应用。|
<!--RP3End-->

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 1、系统内已安装多个辅助应用，若都没有开启，返回false。
// 2、系统内已安装多个辅助应用，若开启任意一个，返回true。
let status: boolean = accessibility.isOpenAccessibilitySync();
```

## accessibility.isOpenTouchGuide<sup>(deprecated)</sup>

isOpenTouchGuide(): Promise&lt;boolean&gt;

判断触摸浏览模式是否开启。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 10开始废弃，建议使用[accessibility.isOpenTouchGuideSync](#accessibilityisopentouchguidesync10)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Vision

**ArkTS-Dyn起始版本**：7

**返回值：**

| 类型                     | 说明                                       |
| ---------------------- | ---------------------------------------- |
| Promise&lt;boolean&gt; | Promise对象，如果触摸浏览模式已开启，则返回 true；否则返回 false。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide().then((data: boolean) => {
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to  isOpenTouchGuide, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.isOpenTouchGuide<sup>(deprecated)</sup>

isOpenTouchGuide(callback: AsyncCallback&lt;boolean&gt;): void

判断触摸浏览模式是否开启。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 10开始废弃，建议使用[accessibility.isOpenTouchGuideSync](#accessibilityisopentouchguidesync10)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Vision

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名      | 类型                           | 必填   | 说明                                    |
| -------- | ---------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | 是    | 回调函数，如果触摸浏览模式已开启，则返回 true；否则返回 false。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`failed to isOpenTouchGuide, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
});
```

## accessibility.isOpenTouchGuideSync<sup>10+</sup>

isOpenTouchGuideSync(): boolean

是否开启了触摸浏览模式。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Vision

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型    | 说明                                  |
| ------- | ------------------------------------- |
| boolean | 表示是否开启了触摸浏览模式。true表示开启了触摸浏览，false表示未开启触摸浏览。|

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isOpenTouchGuideSync();
```

## accessibility.isScreenReaderOpenSync<sup>18+</sup>

isScreenReaderOpenSync(): boolean

是否开启了屏幕朗读模式。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Vision

**ArkTS-Dyn起始版本**：18

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型    | 说明                                  |
| ------- | ------------------------------------- |
| boolean | 表示是否开启了屏幕朗读。true表示开启了屏幕朗读，false表示未开启屏幕朗读。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isScreenReaderOpenSync();
```

## accessibility.isAnimationReduceEnabled<sup>23+</sup>

isAnimationReduceEnabled(): Promise&lt;boolean&gt;

判断减弱动效模式是否开启。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示减弱动效模式已开启；返回false表示减弱动效模式已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isAnimationReduceEnabled().then((data: boolean) => {
      console.info(`success data:isAnimationReduceEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to isAnimationReduceEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAnimationReduceEnabledSync<sup>23+</sup>

isAnimationReduceEnabledSync(): boolean

使用同步方法判断减弱动效模式是否开启。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 表示是否开启减弱动效模式。返回true表示开启减弱动效模式；返回false表示未开启减弱动效模式。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isAnimationReduceEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isFlashReminderEnabled<sup>23+</sup>

isFlashReminderEnabled(): Promise&lt;boolean&gt;

判断闪烁提醒模式是否开启。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示闪烁提醒模式已开启；返回false表示闪烁提醒模式已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isFlashReminderEnabled().then((data: boolean) => {
      console.info(`success data:isFlashReminderEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to isFlashReminderEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isFlashReminderEnabledSync<sup>23+</sup>

isFlashReminderEnabledSync(): boolean

使用同步方法判断闪烁提醒模式是否开启。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 表示是否开启闪烁提醒模式。true表示开启闪烁提醒模式，false表示未开启闪烁提醒模式。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isFlashReminderEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAudioMonoEnabled<sup>23+</sup>

isAudioMonoEnabled(): Promise&lt;boolean&gt;

判断单声道音频模式是否开启。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示单声道音频模式已开启；返回false表示单声道音频模式已关闭。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isAudioMonoEnabled().then((data: boolean) => {
      console.info(`success data:isAudioMonoEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to isAudioMonoEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAudioMonoEnabledSync<sup>23+</sup>

isAudioMonoEnabledSync(): boolean

使用同步方法判断单声道音频模式是否开启。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 表示是否开启单声道音频模式。true表示开启单声道音频模式，false表示未开启单声道音频模式。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isAudioMonoEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isSeniorModeEnabled

isSeniorModeEnabled(): Promise&lt;boolean&gt;

判断系统关怀模式是否开启。使用Promise异步回调。


**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示系统关怀模式已开启；返回false表示系统关怀模式已关闭。 |

**错误码：**

以下错误码的详细介绍请参见[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID   | 错误信息                                     |
| ------- | ---------------------------------------- |
| 9300000 | System abnormality. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isSeniorModeEnabled().then((data: boolean) => {
      console.info(`success data:isSeniorModeEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to call isSeniorModeEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.getSeniorModeStateForSelf

getSeniorModeStateForSelf(): Promise&lt;boolean&gt;

判断应用是否开启“长辈模式”。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示应用自身“长辈模式”已开启；返回false表示应用自身“长辈模式”已关闭。 |

**错误码：**

以下错误码的详细介绍请参见[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID   | 错误信息                                     |
| ------- | ---------------------------------------- |
| 9300000 | System abnormality. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.getSeniorModeStateForSelf().then((data: boolean) => {
      console.info(`Succeeded in getting seniorModeStateForSelf, data: ${data}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to call getSeniorModeStateForSelf, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.setSeniorModeStateForSelf

setSeniorModeStateForSelf(state: boolean): Promise&lt;void&gt;

设置应用是否开启“长辈模式”。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名      | 类型                           | 必填   | 说明                                    |
| -------- | ---------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    | 设置应用是否开启“长辈模式”状态，true表示开启“长辈模式”，false表示关闭“长辈模式”。 |

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID   | 错误信息                                     |
| ------- | ---------------------------------------- |
| 9300000 | System abnormality. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.setSeniorModeStateForSelf(true).then(() => {
      console.info(`Succeeded in setting seniorModeStateForSelf`);
    }).catch((err: BusinessError) => {
      console.error(`failed to call setSeniorModeStateForSelf, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.sendEvent<sup>(deprecated)</sup>

sendEvent(event: EventInfo): Promise&lt;void&gt;

发送无障碍事件。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用[accessibility.sendAccessibilityEvent](#accessibilitysendaccessibilityevent9)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名   | 类型                      | 必填   | 说明       |
| ----- | ----------------------- | ---- | -------- |
| event | [EventInfo](#eventinfo) | 是    | 无障碍事件对象。 |

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`failed to sendEvent, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.sendEvent<sup>(deprecated)</sup>

sendEvent(event: EventInfo, callback: AsyncCallback&lt;void&gt;): void

发送无障碍事件。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用[accessibility.sendAccessibilityEvent](#accessibilitysendaccessibilityevent9-1)替代。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名      | 类型                        | 必填   | 说明                                       |
| -------- | ------------------------- | ---- | ---------------------------------------- |
| event    | [EventInfo](#eventinfo)   | 是    | 辅助事件对象。                                  |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数，如果发送无障碍事件失败，则 AsyncCallback中err有数据返回。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to sendEvent, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

## accessibility.sendAccessibilityEvent<sup>9+</sup>

sendAccessibilityEvent(event: EventInfo): Promise&lt;void&gt;

发送无障碍事件。使用Promise异步回调。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                      | 必填   | 说明       |
| ----- | ----------------------- | ---- | -------- |
| event | [EventInfo](#eventinfo) | 是    | 无障碍事件对象。 |

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`failed to send event , Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.sendAccessibilityEvent<sup>9+</sup>

sendAccessibilityEvent(event: EventInfo, callback: AsyncCallback&lt;void&gt;): void

发送无障碍事件。使用callback异步回调。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名      | 类型                        | 必填   | 说明                                       |
| -------- | ------------------------- | ---- | ---------------------------------------- |
| event    | [EventInfo](#eventinfo)   | 是    | 辅助事件对象。                                  |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数，如果发送无障碍事件失败，则 AsyncCallback中err有数据返回。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Sta示例：

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

**主动聚焦示例：**

ArkTS-Dyn示例：

```ts
@Entry
@Component
struct Index {

  build() {
    Column() {
      // 待聚焦组件添加id属性，id唯一性由使用者保证。
      Button('待聚焦组件').id('click')
    }
  }
}
```
```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'requestFocusForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  customId: 'click' // 对应待聚焦组件id属性值。
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Sta示例：

```ts
@Entry
@Component
struct Index {

  build() {
    Column() {
      // 待聚焦组件添加id属性，id唯一性由使用者保证。
      Button('待聚焦组件').id('click')
    }
  }
}
```
```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'requestFocusForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  customId: 'click' // 对应待聚焦组件id属性值。
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

**主动播报支持Resource示例<sup>18+</sup>：**

ArkTS-Dyn示例：

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'announceForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  textResourceAnnouncedForAccessibility: $r('app.string.ResourceName'),
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Sta示例：

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'announceForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  textResourceAnnouncedForAccessibility: $r('app.string.ResourceName'),
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

## accessibility.getTouchModeSync<sup>20+</sup>

getTouchModeSync(): string

查询触摸浏览功能下的单击/双击操作模式。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：20

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型        | 说明                                  |
| ----------- | ------------------------------------- |
| string | 表示当前操作模式。<br>- singleTouchMode：表示单击操作模式。<br>- doubleTouchMode：表示双击操作模式。<br>- none：表示未开启触摸浏览功能。 |

**示例：**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let touchMode: string = accessibility.getTouchModeSync();
    console.info(`current touch mode: ${JSON.stringify(touchMode)}`);
  }

  build() {
    Column() {
    }
  }
}
```