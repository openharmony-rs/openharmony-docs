# @ohos.accessibility.config (系统辅助功能配置)(系统接口)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->

本模块提供系统辅助功能的配置，包括辅助扩展的启用与关闭、高对比度文字显示、鼠标键、无障碍字幕配置等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从 API version 9 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口为系统接口。

## 导入模块

```ts
import { config } from '@kit.AccessibilityKit';
```

## 属性

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

| 名称                                 | 类型                                                                                     | 只读 | 可选 | 说明                         |
|------------------------------------|--------------------------------------------------------------------------------------------| -------- | -------- |-----------------------------------------------------------|
| highContrastText                   | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示高对比度文字功能启用状态。true表示已启用高对比度文字功能，false表示未启用高对比度文字功能，默认值为false。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23                   |
| invertColor                        | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示颜色反转功能启用状态。true表示已启用颜色反转功能，false表示未启用颜色反转功能，默认值为false。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23       |
| daltonizationState<sup>11+</sup>   | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示颜色滤镜功能启动状态。配合daltonizationColorFilter使用。true表示已启用颜色滤镜功能，false表示未启用颜色滤镜功能，默认值为false。<br>**ArkTS-Dyn起始版本**：11<br>**ArkTS-Sta起始版本**：23   |
| daltonizationColorFilter           | [Config](#config)&lt;[DaltonizationColorFilter](#daltonizationcolorfilter)&gt;             | 否 | 否 | 表示颜色滤镜功能配置。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23            |
| contentTimeout                     | ArkTS-Dyn: [Config](#config)\<number><br>ArkTS-Sta: [Config](#config)\<int>                | 否 | 否 | 表示内容显示建议时长配置。取值范围为0~5000，单位为毫秒。默认值为0。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23      |
| animationOff                       | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示关闭动画功能启用状态。true表示已启用关闭动画功能，false表示未启用关闭动画功能，默认值为false。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23                 |
| brightnessDiscount                 | ArkTS-Dyn: [Config](#config)\<number><br>ArkTS-Sta: [Config](#config)\<double>             | 否 | 否 | 表示亮度折扣系统配置。取值范围为0~1.0。默认值为1.0。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23          |
| mouseKey                           | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示鼠标键功能启用状态。true表示已启用鼠标键功能，false表示未启用鼠标键功能，默认值为false。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23                  |
| mouseAutoClick                     | ArkTS-Dyn: [Config](#config)\<number><br>ArkTS-Sta: [Config](#config)\<int>                | 否 | 否 | 表示鼠标自动点击操作的配置。取值范围0-5000，单位为毫秒，0表示不生效，其他值表示鼠标悬停相应的时长即触发自动点击操作，默认值为0，即默认不生效。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23     |
| shortkey                           | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示辅助扩展快捷键功能启用状态。true表示已启用辅助扩展快捷键功能，false表示未启用辅助扩展快捷键功能，默认值为false。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23               |
| shortkeyTarget                     | [Config](#config)\<string>                                                                 | 否 | 否 | 表示辅助扩展快捷键的目标配置。取值为辅助应用的名称，格式为：'bundleName/abilityName'。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23  |
| captions                           | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示辅助字幕功能启用状态。true表示已启用辅助字幕功能，false表示未启用辅助字幕功能，默认值为false。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23          |
| captionsStyle                      | [Config](#config)\<[accessibility.CaptionsStyle](js-apis-accessibility.md#captionsstyle8)> | 否 | 否 | 表示辅助字幕的配置。<br>**ArkTS-Dyn起始版本**：9<br>**ArkTS-Sta起始版本**：23            |
| audioMono<sup>10+</sup>            | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示单声道音频的配置。true表示已启用单声道音频，false表示未启用单声道音频，默认值为false。<br>**ArkTS-Dyn起始版本**：10<br>**ArkTS-Sta起始版本**：23               |
| audioBalance<sup>10+</sup>         | ArkTS-Dyn: [Config](#config)\<number><br>ArkTS-Sta: [Config](#config)\<double>             | 否 | 否 | 表示左右声道音量平衡的配置。取值范围为-1.0~1.0。默认值为0.0。<br>**ArkTS-Dyn起始版本**：10<br>**ArkTS-Sta起始版本**：23         |
| shortkeyMultiTargets<sup>11+</sup> | [Config](#config)&lt;Array\<string>&gt;                                                    | 否 | 否 | 表示辅助扩展快捷键的列表配置。取值为辅助应用的名称，格式为：['bundleName/abilityName']。<br>**ArkTS-Dyn起始版本**：11<br>**ArkTS-Sta起始版本**：23 |
| clickResponseTime<sup>11+</sup>    | [Config](#config)&lt;[ClickResponseTime](#clickresponsetime11)&gt;                         | 否 | 否 | 表示点击持续时间功能配置。<br>**ArkTS-Dyn起始版本**：11<br>**ArkTS-Sta起始版本**：23             |
| ignoreRepeatClick<sup>11+</sup>    | [Config](#config)\<boolean>                                                                | 否 | 否 | 表示忽略重复点击功能启用状态。配合repeatClickInterval使用。true表示已启用忽略重复点击功能，false表示未启用忽略重复点击功能，默认值为false。<br>**ArkTS-Dyn起始版本**：11<br>**ArkTS-Sta起始版本**：23    |
| repeatClickInterval<sup>11+</sup>  | [Config](#config)&lt;[RepeatClickInterval](#repeatclickinterval11)&gt;                     | 否 | 否 | 表示忽略重复点击功能配置。<br>**ArkTS-Dyn起始版本**：11<br>**ArkTS-Sta起始版本**：23          |

## config.enableAbility

enableAbility(name: string, capability: Array&lt;accessibility.Capability&gt;): Promise&lt;void&gt;

启用辅助扩展。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型                                                                           | 必填 | 说明 |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| name | string                                                                       | 是 | 辅助应用的名称，格式为：'bundleName/abilityName'。 |
| capability | Array&lt;[accessibility.Capability](js-apis-accessibility.md#capability)&gt; | 是 | 辅助应用的能力属性。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |
| 9300002 | Target ability already enabled. |

**示例：**

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];

config.enableAbility(name, capability).then(() => {
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`);
}).catch((err: BusinessError) => {
  console.error(`failed to enable ability, Code is ${err.code}, message is ${err.message}`);
});
```

## config.enableAbility

enableAbility(name: string, capability: Array&lt;accessibility.Capability&gt;, callback: AsyncCallback&lt;void&gt;): void

启用辅助扩展。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型                                                                              | 必填 | 说明 |
| -------- |---------------------------------------------------------------------------------| -------- | -------- |
| name | string                                                                          | 是 | 辅助应用的名称，格式为：'bundleName/abilityName'。 |
| capability | Array&lt;[accessibility.Capability](js-apis-accessibility.md#capability)&gt; | 是 | 辅助应用的能力属性。 |
| callback | AsyncCallback&lt;void&gt;                                                       | 是 | 回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |
| 9300002 | Target ability already enabled. |

**示例：**

ArkTS-Dyn示例：

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];

config.enableAbility(name, capability, (err: BusinessError) => {
  if (err) {
    console.error(`failed to enable ability, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`); 
});
```

ArkTS-Sta示例：

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];

config.enableAbility(name, capability, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to enable ability, Code is ${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`Succeeded in enable ability, name is ${name}, capability is ${capability}`); 
});
```

## config.enableAbilityWithCallback<sup>23+</sup>

enableAbilityWithCallback(name: string, capability: Array&lt;accessibility.Capability&gt;, connectCallback: ConnectCallback): Promise&lt;void&gt;

启用辅助扩展，并指定[ConnectCallback](#connectcallback23)作为辅助扩展应用状态变化的回调函数。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型                                                                           | 必填 | 说明 |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| name | string                                                                       | 是 | 辅助扩展应用的名称，格式为：'bundleName/abilityName'。 |
| capability | Array&lt;[accessibility.Capability](js-apis-accessibility.md#capability)&gt; | 是 | 辅助扩展应用的能力属性。 |
| connectCallback | [ConnectCallback](#connectcallback23)                             | 是 | 辅助扩展应用的状态发生变化时调用的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300001 | Invalid bundle name or ability name.  |
| 9300002 | Target ability already enabled. |

**示例：**

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];
let connectCallback: config.ConnectCallback = {
  onDisconnect: () => {
    console.info(`Ability is disconnected.`)
  }
}

config.enableAbilityWithCallback(name, capability, connectCallback).then(() => {
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`);
}).catch((err: BusinessError) => {
  console.error(`failed to enable ability, Code is ${err.code}, message is ${err.message}`);
});
```

## config.disableAbility

disableAbility(name: string): Promise&lt;void&gt;

关闭辅助扩展。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 辅助应用的名称，格式为：'bundleName/abilityName'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |

**示例：**

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';

config.disableAbility(name).then(() => {
  console.info(`Succeeded in disabling ability, name is ${name}`);
}).catch((err: BusinessError) => {
  console.error(`failed to disable ability, Code is ${err.code}, message is ${err.message}`);
})
```

## config.disableAbility

disableAbility(name: string, callback: AsyncCallback&lt;void&gt;): void

关闭辅助扩展。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 辅助应用的名称，格式为：'bundleName/abilityName'。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |

**示例：**

ArkTS-Dyn示例：

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';

config.disableAbility(name, (err: BusinessError) => {
  if (err) {
    console.error(`failed to disable ability, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in disabling, name is ${name}`);
});
```

ArkTS-Sta示例：

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';

config.disableAbility(name, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to disable ability, Code is ${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`Succeeded in disabling, name is ${name}`);
});
```

## config.on('enabledAccessibilityExtensionListChange')

on(type: 'enabledAccessibilityExtensionListChange', callback: Callback&lt;void&gt;): void

添加启用的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[config.onEnabledAccessibilityExtensionListChange](#configonenabledaccessibilityextensionlistchange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 参数固定为'enabledAccessibilityExtensionListChange'，监听启用的辅助扩展的列表变化。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数，在启用的辅助扩展的列表变化时通过此函数进行通知。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

config.on('enabledAccessibilityExtensionListChange', () => {
  console.info('subscribe enabled accessibility extension list change state success');
});
```

## config.onEnabledAccessibilityExtensionListChange<sup>23+</sup>

onEnabledAccessibilityExtensionListChange(callback: Callback&lt;void&gt;): void

添加启用的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[config.on('enabledAccessibilityExtensionListChange')](#configonenabledaccessibilityextensionlistchange)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;void&gt; | 是 | 回调函数，在启用的辅助扩展的列表变化时通过此函数进行通知。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: () => void = this.eventCallback;
  eventCallback(): void {
    console.info(`enabled accessibility extension list change`);
  }

  aboutToAppear(): void {
    config.onEnabledAccessibilityExtensionListChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## config.off('enabledAccessibilityExtensionListChange')

off(type: 'enabledAccessibilityExtensionListChange', callback?: Callback&lt;void&gt;): void

取消启用的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[config.offEnabledAccessibilityExtensionListChange](#configoffenabledaccessibilityextensionlistchange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type |  string | 是 | 参数固定为'enabledAccessibilityExtensionListChange'，监听启用的辅助扩展的列表变化。 |
| callback | Callback&lt;void&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与on('enabledAccessibilityExtensionListChange')的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

config.off('enabledAccessibilityExtensionListChange', () => {
  console.info('Unsubscribe enabled accessibility extension list change state success');
});
```

## config.offEnabledAccessibilityExtensionListChange<sup>23+</sup>

offEnabledAccessibilityExtensionListChange(callback?: Callback&lt;void&gt;): void

取消启用的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[config.off('enabledAccessibilityExtensionListChange')](#configoffenabledaccessibilityextensionlistchange)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;void&gt; | 否 | 取消指定callback对象的事件响应。需与onEnabledAccessibilityExtensionListChange的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: () => void = this.eventCallback;
  eventCallback(): void {
    console.info(`enabled accessibility extension list change`);
  }

  aboutToAppear(): void {
    config.onEnabledAccessibilityExtensionListChange(this.callback);
  }

  aboutToDisappear(): void {
    config.offEnabledAccessibilityExtensionListChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## config.on('installedAccessibilityListChange')<sup>12+</sup>

on(type: 'installedAccessibilityListChange', callback: Callback&lt;void&gt;): void

添加已安装的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[config.onInstalledAccessibilityListChange](#configoninstalledaccessibilitylistchange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 参数固定为'installedAccessibilityListChange'，监听已安装的辅助扩展的列表变化。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数，在已安装的辅助扩展的列表变化时通过此函数进行通知。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

config.on('installedAccessibilityListChange', () => {
  console.info('subscribe installed accessibility extension list change state success');
});
```

## config.onInstalledAccessibilityListChange<sup>23+</sup>

onInstalledAccessibilityListChange(callback: Callback&lt;void&gt;): void

添加已安装的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[config.on('installedAccessibilityListChange')](#configoninstalledaccessibilitylistchange12)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;void&gt; | 是 | 回调函数，在已安装的辅助扩展的列表变化时通过此函数进行通知。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: () => void = this.eventCallback;
  eventCallback(): void {
    console.info(`installed accessibility list change`);
  }

  aboutToAppear(): void {
    config.onInstalledAccessibilityListChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## config.off('installedAccessibilityListChange')<sup>12+</sup>

off(type: 'installedAccessibilityListChange', callback?: Callback&lt;void&gt;): void

取消已安装的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[config.offInstalledAccessibilityListChange](#configoffinstalledaccessibilitylistchange23)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type |  string | 是 | 参数固定为'installedAccessibilityListChange'，监听已安装的辅助扩展的列表变化。 |
| callback | Callback&lt;void&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与on('installedAccessibilityListChange')的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

config.off('installedAccessibilityListChange', () => {
  console.info('Unsubscribe installed accessibility extension list change state success');
});
```

## config.offInstalledAccessibilityListChange<sup>23+</sup>

offInstalledAccessibilityListChange(callback?: Callback&lt;void&gt;): void

取消已安装的辅助扩展的列表变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[config.off('installedAccessibilityListChange')](#configoffinstalledaccessibilitylistchange12)。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;void&gt; | 否 | 取消指定callback对象的事件响应。需与onInstalledAccessibilityListChange的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: () => void = this.eventCallback;
  eventCallback(): void {
    console.info(`installed accessibility list change`);
  }

  aboutToAppear(): void {
    config.onInstalledAccessibilityListChange(this.callback);
  }

  aboutToDisappear(): void {
    config.offInstalledAccessibilityListChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## config.setMagnificationState<sup>20+</sup>

setMagnificationState(state: boolean): void

触发或者关闭放大手势功能的放大效果，使用前需要保证放大手势功能已开启。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：20

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| state |  boolean | 是 | 表示放大手势功能的放大效果的启用状态。<br>-true：表示触发放大效果。<br>-false：表示关闭放大效果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 9300007  | Trigger magnification failed. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

try {
  config.setMagnificationState(true);
} catch (e) {
  console.error(`Set magnification failed,  error code: ${e?.code}, error msg: ${e?.message}`);
}
```

## config.setSeniorModeStateForApp

setSeniorModeStateForApp(appSeniorModeInfos: Array&lt;AppSeniorModeInfo&gt;): Promise&lt;void&gt;

设置应用状态为“长辈模式”。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名 | 类型                                                                           | 必填 | 说明 |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| appSeniorModeInfos | Array&lt;[AppSeniorModeInfo](#appseniormodeinfo)&gt; | 是 | 修改应用的“长辈模式”的状态信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300000 | System abnormality.  |
| 9300008 | The appIndex is invalid. Possible causes: 1. The appIndex is out of the valid range. 2. The application corresponding to the appIndex does not exist. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let infos: config.AppSeniorModeInfo[] = [{
  bundleName: 'com.example.myapplication',
  appIndex: 0,
  seniorModeState: true
}];

config.setSeniorModeStateForApp(infos).then(() => {
  console.info(`Succeeded in setting seniorModeState for App.`);
}).catch((err: BusinessError) => {
  console.error(`failed to call setSeniorModeStateForApp, Code is ${err.code}, message is ${err.message}`);
});
```

## config.getSeniorModeStateForApp

ArkTS-Dyn: getSeniorModeStateForApp(bundleName: string, appIndex?: number): Promise&lt;boolean&gt;

ArkTS-Sta: getSeniorModeStateForApp(bundleName: string, appIndex?: int): Promise&lt;boolean&gt;

查询应用“长辈模式”的状态。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名 | 类型                                                                           | 必填 | 说明 |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| bundleName | string | 是 | 查询“长辈模式”的应用包名。 |
| appIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 应用包的分身索引标识。<br>取值范围：大于等于0的整数。缺省时，appIndex默认为0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示应用“长辈模式”已启用；返回false表示应用“长辈模式”已关闭。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[无障碍子系统错误码](errorcode-accessibility.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300000 | System abnormality.  |
| 9300008 | The appIndex is invalid. Possible causes: 1. The appIndex is out of the valid range. 2. The application corresponding to the appIndex does not exist. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

config.getSeniorModeStateForApp("com.example.myapplication", 0).then((data: boolean) => {
  console.info(`Succeeded in getting seniorModeState for app, data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`failed to call getSeniorModeStateForApp, Code is ${err.code}, message is ${err.message}`);
});
```

## config.onSeniorModeStateChangeForApp

onSeniorModeStateChangeForApp(callback: Callback&lt;AppSeniorModeInfo&gt;): void

监听所有应用“长辈模式”的状态变化事件。使用callback异步回调。

> **说明：**
>
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> - 调用此方法后，务必在对象生命周期结束前使用[config.offSeniorModeStateChangeForApp](#configoffseniormodestatechangeforapp)取消监听，否则可能会导致崩溃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AppSeniorModeInfo](#appseniormodeinfo)&gt; | 是 | 回调函数。返回被修改的应用“长辈模式”信息。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.|
| 202 | Permission verification failed. A non-system application calls a system API.|

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: config.AppSeniorModeInfo) => {
    console.info(`callback data, name: ${data.bundleName}, appIndex: ${data.appIndex}, seniorModeState: ${data.seniorModeState}`);
  }

  aboutToAppear(): void {
    config.onSeniorModeStateChangeForApp(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## config.offSeniorModeStateChangeForApp

offSeniorModeStateChangeForApp(callback?: Callback\<AppSeniorModeInfo>): void

取消监听所有应用“长辈模式”的状态变化事件。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AppSeniorModeInfo](#appseniormodeinfo)&gt; | 是   | 回调函数。返回被修改的应用“长辈模式”信息。需与[config.onSeniorModeStateChangeForApp](#configonseniormodestatechangeforapp)的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: config.AppSeniorModeInfo) => {
    console.info(`callback data, name: ${data.bundleName}, appIndex: ${data.appIndex}, seniorModeState: ${data.seniorModeState}`);
  }

  aboutToAppear(): void {
    config.onSeniorModeStateChangeForApp(this.callback);
  }

  aboutToDisappear(): void {
    config.offSeniorModeStateChangeForApp(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## Config

用于属性的设置、获取与监听。

### set

set(value: T): Promise&lt;void&gt;

设置属性。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 设置的属性值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let value: boolean = true;

config.highContrastText.set(value).then(() => {
  console.info(`succeeded in setting highContrastText value is ${value}`);
}).catch((err: BusinessError) => {
  console.error(`failed to set highContrastText, Code is ${err.code}, message is ${err.message}`);
});
```

### set

set(value: T, callback: AsyncCallback&lt;void&gt;): void

设置属性。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 设置的属性值。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let value: boolean = true;

config.highContrastText.set(value, (err: BusinessError) => {
  if (err) {
    console.error(`failed to set highContrastText, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in setting highContrastText, value is ${value}`);
});
```

ArkTS-Sta示例：

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let value: boolean = true;

config.highContrastText.set(value, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to set highContrastText, Code is ${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`succeeded in setting highContrastText, value is ${value}`);
});
```

### get

get(): Promise&lt;T&gt;

获取属性。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;T&gt; | Promise对象，返回对应属性值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

config.highContrastText.get().then((data: boolean) => {
  console.info(`succeeded in getting highContrastText, data is ${data}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get highContrastText, Code is ${err.code}, message is ${err.message}`);
});
```

### get

get(callback: AsyncCallback&lt;T&gt;): void

获取属性。使用callback异步回调。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;T&gt; | 是 | 回调函数，返回属性值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

ArkTS-Dyn示例：

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

config.highContrastText.get((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`failed to get highContrastText, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting highContrastText, data is ${data}`);
});
```

ArkTS-Sta示例：

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

config.highContrastText.get((err: BusinessError | null, data: boolean | undefined) => {
  if (err?.code) {
    console.error(`failed to get highContrastText, Code is ${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`succeeded in getting highContrastText, data is ${data}`);
});
```

### on

on(callback: Callback&lt;T&gt;): void

添加属性变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;T&gt; | 是 | 回调函数，在属性变化时通过此函数进行通知。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

config.highContrastText.on((data: boolean) => {
  console.info(`subscribe highContrastText success, result: ${JSON.stringify(data)}`);
});
```

### off

off(callback?: Callback&lt;T&gt;): void

取消属性变化监听。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.READ_ACCESSIBILITY_CONFIG

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;T&gt; | 否 | 回调函数，取消指定callback对象的事件响应。需与on()的callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { config } from '@kit.AccessibilityKit';

config.highContrastText.off((data: boolean) => {
  console.info(`Unsubscribe highContrastText success, result: ${JSON.stringify(data)}`);
});
```

## ConnectCallback<sup>23+</sup>

通过[config.enableAbilityWithCallback](#configenableabilitywithcallback23)接口启用辅助扩展应用时提供的回调函数。辅助扩展应用连接断开时，回调函数将被调用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名         | 类型                                         | 只读 | 可选 | 描述                                     |
| ------------ | -------------------------------------------- | ---- | ---- | ---------------------------------------- |
| onDisconnect | [OnDisconnectCallback](#ondisconnectcallback23) | 否   | 否   | 辅助扩展应用的连接断开时调用的回调函数。 |


## OnDisconnectCallback<sup>23+</sup>

type OnDisconnectCallback = () => void

描述AccessibilityExtensionAbility断开连接的回调接口。

**系统接口**：此类型为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**模型约束**：此类型仅可在Stage模型下使用。

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23


## DaltonizationColorFilter

用于不同弱视类型的校正颜色滤镜。  

颜色滤镜功能开启时（[daltonizationState](#属性)设置为true)，颜色滤镜的配置(即设置的DaltonizationColorFilter的值)生效；颜色滤镜功能关闭时（[daltonizationState](#属性)设置为false)，显示为正常类型。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

| 名称 | 说明 |
| -------- | -------- |
| Normal | 表示正常类型。 |
| Protanomaly | 表示红色弱视类型。 |
| Deuteranomaly | 表示绿色弱视类型。 |
| Tritanomaly  | 表示蓝色弱视类型。 |

## ClickResponseTime<sup>11+</sup>

用于不同时间长短的点击重复时间。  

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：23

| 名称          | 说明         |
|-------------|------------|
| Short       | 表示短 (默认)。  |
| Medium      | 表示中。       |
| Long        | 表示长。       |

## RepeatClickInterval<sup>11+</sup>

用于不同时间间隔的忽略重复点击。  

忽略重复点击功能开启时（[ignoreRepeatClick](#属性)设置为true)，忽略重复点击的配置(即设置的RepeatClickInterval的值)生效；忽略重复点击功能关闭时（[ignoreRepeatClick](#属性)设置为false)，显示为正常类型。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：23

| 名称       | 说明    |
|----------|-------|
| Shortest | 表示最短。 |
| Short    | 表示短。  |
| Medium   | 表示中。  |
| Long     | 表示长。  |
| Longest  | 表示最长。 |

## AppSeniorModeInfo

“长辈模式”在应用中的状态信息。

**模型约束：** 此类型仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

| 参数名         | 类型                                         | 只读 | 可选 | 描述                                     |
| ------------ | -------------------------------------------- | ---- | ---- | ---------------------------------------- |
| bundleName | string | 否   | 否   | 应用包名。 |
| appIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 是   | 应用包的分身索引标识。<br>取值大于等于0的整数，缺省时默认为0。|
| seniorModeState | boolean | 否   | 否   | 应用是否开启状态为“长辈模式”，true表示开启，false表示未开启。|