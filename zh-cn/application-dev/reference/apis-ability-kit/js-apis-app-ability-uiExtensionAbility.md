# @ohos.app.ability.UIExtensionAbility (带界面的ExtensionAbility组件)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhangyafei-echo; @xuzhihao666-->
<!--Designer: @zhangyafei-echo-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

UIExtensionAbility组件是带界面的ExtensionAbility组件，继承自[ExtensionAbility](js-apis-app-ability-extensionAbility.md)，提供了组件创建、销毁、前后台切换等基础生命周期。和UIAbility组件不同，UIExtensionAbility组件不会作为单独的任务在任务视图中体现。UIExtensionAbility组件被宿主窗口启动，其前后台切换和显隐跟随宿主窗口。不支持开发者直接继承UIExtensionAbility组件，支持开发者根据业务功能使用相应的垂类UIExtensionAbility组件。例如，开发者处理其他应用分享的数据时，可以使用[ShareExtensionAbility组件](./js-apis-app-ability-shareExtensionAbility.md)；开发者提供卡片编辑功能时，可以使用[FormEditExtensionAbility组件](../apis-form-kit/js-apis-app-form-formEditExtensionAbility.md)。各类Ability组件的继承关系详见[继承关系说明](./js-apis-app-ability-ability.md#ability的继承关系说明)。

> **说明：**
>
> 本模块首批接口从API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { UIExtensionAbility } from '@kit.AbilityKit';
```

## UIExtensionAbility

表示包含UI界面的扩展组件，提供组件创建、销毁、前后台切换等生命周期回调。

### 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [UIExtensionContext](js-apis-inner-application-uiExtensionContext.md) | 否 | 否 | UIExtensionAbility组件的上下文。 |

### onCreate

onCreate(launchParam: AbilityConstant.LaunchParam): void

当UIExtensionAbility组件实例完成创建时，系统会触发该回调。开发者可在该回调中执行初始化逻辑（如定义变量、加载资源等）。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| launchParam<sup>12+</sup> | [AbilityConstant.LaunchParam](js-apis-app-ability-abilityConstant.md#launchparam) | 是 | 应用启动参数，包含应用启动原因、应用上次退出原因等。 |

**示例：**

```ts
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { ShareExtensionAbility, AbilityConstant } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onCreate(launchParam: AbilityConstant.LaunchParam) {
    console.info(TAG, `onCreate, launchParam: ${JSON.stringify(launchParam)}`);
  }
}
```

### onSessionCreate

onSessionCreate(want: Want, session: UIExtensionContentSession): void

当[UIExtensionContentSession](js-apis-app-ability-uiExtensionContentSession.md)实例创建完成后，系统会触发该回调。开发者可在该回调中通过UIExtensionContentSession实例加载页面。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | 是 | 调用方拉起该UIExtensionAbility组件时传递的数据。 |
| session | [UIExtensionContentSession](js-apis-app-ability-uiExtensionContentSession.md) | 是 | UIExtensionContentSession实例对象。 |

**示例：**

```ts
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { ShareExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
    try {
      session.loadContent('pages/Index');
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`Failed to load content, code: ${code}, msg: ${message}`);
    }
  }
}
```

### onSessionDestroy

onSessionDestroy(session: UIExtensionContentSession): void

当UIExtensionContentSession实例销毁后，系统触发该回调。该回调用于通知开发者UIExtensionContentSession实例已被销毁，不能再继续使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| session | [UIExtensionContentSession](js-apis-app-ability-uiExtensionContentSession.md) | 是 | UIExtensionContentSession实例对象。 |

**示例：**

```ts
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { ShareExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    console.info(TAG, `onSessionDestroy`);
  }
}
```

### onForeground

onForeground(): void

当UIExtensionAbility组件首次启动到前台或者从后台转入到前台时，系统触发该回调。开发者可在该回调中实现UI可见时的资源申请操作。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```ts
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { ShareExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onForeground() {
    console.info(TAG, `onForeground`);
  }
}
```

### onBackground

onBackground(): void

当UIExtensionAbility组件从前台转入到后台时，系统触发该回调。开发者可在该回调中实现UI不可见时的资源释放操作。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```ts
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { ShareExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onBackground() {
    console.info(TAG, `onBackground`);
  }
}
```

### onDestroy

onDestroy(): void | Promise&lt;void&gt;

当UIExtensionAbility组件被销毁时，系统触发该回调。开发者可以在该生命周期中执行资源清理、数据保存等相关操作。使用同步回调或Promise异步回调。

在执行完onDestroy生命周期回调后，应用可能会退出，从而可能导致onDestroy中的异步函数未能正确执行，比如异步写入数据库。推荐使用Promise异步回调，避免因应用退出导致onDestroy中的异步函数（比如异步写入数据库）未能正确执行。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| void \| Promise\<void> | 无返回结果或无返回结果的Promise对象。                     |

**示例：**

- 同步回调示例如下：
  ```ts
  // UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
  import { ShareExtensionAbility } from '@kit.AbilityKit';

  const TAG: string = '[testTag] ShareExtAbility';

  export default class ShareExtAbility extends ShareExtensionAbility {
    onDestroy() {
      console.info(TAG, `onDestroy`);
    }
  }
  ```

- 异步回调示例如下：
  ```ts
  // UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
  import { ShareExtensionAbility } from '@kit.AbilityKit';

  const TAG: string = '[testTag] ShareExtAbility';

  export default class ShareExtAbility extends ShareExtensionAbility {
    // 实现异步回调需要使用async/await语法糖，通过async声明onDestroy是一个异步函数。
    async onDestroy(): Promise<void> {
      console.info(TAG, `onDestroy begin`);
      try {
        const result: string = await new Promise((resolve: Function) => {
          setTimeout(() => {
            resolve('Hello, world!');
          }, 3000);
        });
        console.info(TAG, result); // result is 'Hello, world!'
      } catch (e) {
        console.error(TAG, `Get exception: ${e}`);
      }
      console.info(TAG, `onDestroy end`);
    }
  }
  ```