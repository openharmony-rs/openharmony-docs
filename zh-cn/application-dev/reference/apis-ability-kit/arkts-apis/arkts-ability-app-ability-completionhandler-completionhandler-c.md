# CompletionHandler

CompletionHandler提供了 [onRequestSuccess](#onRequestSuccess)和 [onRequestFailure](#onRequestFailure)两个回调函数，分别用来处理拉 起应用成功和失败时的结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class CompletionHandler--><!--Device-unnamed-declare class CompletionHandler-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onRequestFailure

```TypeScript
onRequestFailure(elementName: ElementName, message: string): void
```

拉起应用失败时的回调函数。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CompletionHandler-onRequestFailure(elementName: ElementName, message: string): void--><!--Device-CompletionHandler-onRequestFailure(elementName: ElementName, message: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | 是 | ElementName信息用于标识被拉起应用。  - 通常，ElementName仅包含abilityName和bundleName。moduleName和deviceId信息是否存在取决于调用方是否传入。shortName和uri为空。  - 隐式启动失败时，无法获取ElementName信息。 |
| message | string | 是 | 拉起应用失败时的信息。该信息采用JSON格式，样式如下：  {  ?"errMsg": "xxx"  }  其中，"xxx"的取值说明如下：  Failed to call &lt;api-name&gt;：表示调用接口出错。其中，&lt;api-name&gt;为具体的接口名，比如startAbility。  User refused redirection：表示用户关闭了应用跳转弹框。  User closed the implicit startup picker：表示用户关闭了隐式启动时的应用选择弹框。  User closed the app clone picker：表示用户关闭了分身应用选择弹框。  Free installation failed：表示免安装失败。 |

## 示例

```TypeScript
import { UIAbility, Want, StartOptions, CompletionHandler, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // 定义拉起应用的Want参数
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    // 定义CompletionHandler对象，处理拉起应用成功和失败的回调
    let completionHandler: CompletionHandler = {
      onRequestSuccess: (elementName: bundleManager.ElementName, message: string): void => {
        console.info(`${elementName.bundleName}-${elementName.moduleName}-${elementName.abilityName} start succeeded: ${message}`);
      },
      onRequestFailure: (elementName: bundleManager.ElementName, message: string): void => {
        console.error(`${elementName.bundleName}-${elementName.moduleName}-${elementName.abilityName} start failed: ${message}`);
      }
    };

    let options: StartOptions = {
      completionHandler: completionHandler
    };

    try {
      // 拉起目标应用，options中的completionHandler会回调拉起结果
      this.context.startAbility(want, options).then(() => {
        console.info('startAbility succeed');
      }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`startAbility failed, code is ${code}, message is ${message}`);
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## onRequestSuccess

```TypeScript
onRequestSuccess(elementName: ElementName, message: string): void
```

拉起应用成功时的回调函数。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CompletionHandler-onRequestSuccess(elementName: ElementName, message: string): void--><!--Device-CompletionHandler-onRequestSuccess(elementName: ElementName, message: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | 是 | ElementName信息用于标识被拉起应用。通常，ElementName仅包含abilityName和bundleName。moduleName和deviceId信 息是否存在取决于调用方是否传入。shortName和uri为空。 |
| message | string | 是 | 成功拉起应用时的信息。该信息采用JSON格式，样式如下：  {  ?"errMsg": "Succeeded."  } |

## 示例

参见[onRequestFailure](#onRequestFailure)接口的示例。

## onRequestFailure

```TypeScript
onRequestFailure: OnRequestFailureFn
```

拉端失败时的回调函数。

**类型：** [OnRequestFailureFn](arkts-ability-onrequestfailurefn-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletionHandler-onRequestFailure: OnRequestFailureFn--><!--Device-CompletionHandler-onRequestFailure: OnRequestFailureFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onRequestSuccess

```TypeScript
onRequestSuccess: OnRequestSuccessFn
```

拉端成功时的回调函数。

**类型：** [OnRequestSuccessFn](arkts-ability-onrequestsuccessfn-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletionHandler-onRequestSuccess: OnRequestSuccessFn--><!--Device-CompletionHandler-onRequestSuccess: OnRequestSuccessFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

