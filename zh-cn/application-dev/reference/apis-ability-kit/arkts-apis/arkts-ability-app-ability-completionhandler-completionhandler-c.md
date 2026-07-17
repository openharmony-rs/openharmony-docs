# CompletionHandler

CompletionHandler提供了[onRequestSuccess](arkts-ability-app-ability-completionhandler-completionhandler-c.md#onrequestsuccess-1)和[onRequestFailure](arkts-ability-app-ability-completionhandler-completionhandler-c.md#onrequestfailure-1)两个回调函数，分别用来处理拉起应用成功和失败时的结果。

**起始版本：** 20

<!--Device-unnamed-declare class CompletionHandler--><!--Device-unnamed-declare class CompletionHandler-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { CompletionHandler } from '@kit.AbilityKit';
```

## onRequestFailure

```TypeScript
onRequestFailure(elementName: ElementName, message: string): void
```

拉起应用失败时的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CompletionHandler-onRequestFailure(elementName: ElementName, message: string): void--><!--Device-CompletionHandler-onRequestFailure(elementName: ElementName, message: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-bundlemanager-elementname-t.md) | 是 | ElementName信息用于标识被拉起应用。* - 通常，ElementName仅包含abilityName和bundleName。moduleName和deviceId信息是否存在取决于调用方是否传入。shortName和uri为空。* - 隐式启动失败时，无法获取ElementName信息。 |
| message | string | 是 | 拉起应用失败时的信息。该信息采用JSON格式，样式如下：* {* ?"errMsg": "xxx"* }* 其中，"xxx"的取值说明如下：* Failed to call &lt;api-name&gt;：表示调用接口出错。其中，&lt;api-name&gt;为具体的接口名，比如startAbility。* User refused redirection：表示用户关闭了应用跳转弹框。* User closed the implicit startup picker：表示用户关闭了隐式启动时的应用选择弹框。* User closed the app clone picker：表示用户关闭了分身应用选择弹框。* Free installation failed：表示免安装失败。 |

**示例：**

参见[CompletionHandler使用](#completionhandler使用)。

## onRequestSuccess

```TypeScript
onRequestSuccess(elementName: ElementName, message: string): void
```

拉起应用成功时的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CompletionHandler-onRequestSuccess(elementName: ElementName, message: string): void--><!--Device-CompletionHandler-onRequestSuccess(elementName: ElementName, message: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-bundlemanager-elementname-t.md) | 是 | ElementName信息用于标识被拉起应用。通常，ElementName仅包含abilityName和bundleName。moduleName和deviceId信息是否存在取决于调用方是否传入。shortName和uri为空。 |
| message | string | 是 | 成功拉起应用时的信息。该信息采用JSON格式，样式如下：* {* ?"errMsg": "Succeeded."* } |

**示例：**

参见[CompletionHandler使用](#completionhandler使用)。

