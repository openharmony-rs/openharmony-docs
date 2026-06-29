# AbilityStartCallback
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

定义拉起UIExtensionAbility执行结果的回调。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 从API version 11开始，本模块接口支持在原子化服务中使用。

## 导入模块

```ts
import { common } from '@kit.AbilityKit';
```

## AbilityStartCallback

### 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                            | 类型                                                         | 只读 | 可选 | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| completionHandler<sup>21+</sup> | [CompletionHandlerForAbilityStartCallback](js-apis-app-ability-CompletionHandlerForAbilityStartCallback.md) | 否   | 是   | 用于返回拉起指定类型的Ability组件的回调结果。 <br>**原子化服务API（仅ArkTS-Dyn）**：从API version 21开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 21<br>**ArkTS-Sta起始版本：** 23 |
| onResult<sup>23+</sup>          | [onResultFn](#onresultfn23)                                  | 否   | 是   | 拉起UIExtensionAbility终止时的回调。<br>**ArkTS模式：** 此接口仅适用于ArkTS-Sta。<br>**ArkTS-Sta起始版本：** 23 |

### onError

ArkTS-Dyn: onError(code: number, name: string, message: string): void

ArkTS-Sta: onError(code: int, name: string, message: string): void

拉起UIExtensionAbility执行失败的回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                     | 必填   | 说明            |
| -------- | ---------------------- | ---- | ------------- |
| code | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是    | 拉起UIExtensionAbility执行失败时返回的结果码。 |
| name | string | 是    | 拉起UIExtensionAbility执行失败时返回的名称。 |
| message | string | 是    | 拉起UIExtensionAbility执行失败时返回的错误信息。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, Object> = {
      'time': '2023-10-23 20:45',
    };
    let abilityStartCallback: common.AbilityStartCallback = {
      onError: (code: number, name: string, message: string) => {
        console.info(`code: ${code}, name: ${name}, message: ${message}`);
      },
      onResult: (abilityResult: common.AbilityResult) => {
        console.info(`resultCode: ${abilityResult.resultCode}, bundleName: ${abilityResult.want?.bundleName}`);
      }
    };

    this.context.startAbilityByType('photoEditor', wantParam, abilityStartCallback, (err: BusinessError) => {
      if (err) {
        console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`success`);
      }
    });
  }
}
```

ArkTS-Sta示例：

```ts
'use static'
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

class MyAbilityStartCallback implements common.AbilityStartCallback {
  onError(code: int, name: string, message: string): void {
    console.info(`startAbilityByType Error:` + "code:" + code + "name:" + name + "message:" + message);
  }

  onResult?: (abilityResult: common.AbilityResult) => void = (parameter: common.AbilityResult) => {
    console.info(`startAbilityByType resultCode:` + parameter.resultCode + `bundleName:` + parameter.want?.bundleName);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, RecordData> = {
      'time': '2023-10-23 20:45',
    };

    let abilityStartCallback = new MyAbilityStartCallback();

    this.context.startAbilityByType("photoEditor", wantParam, abilityStartCallback, (err: BusinessError | null) => {
      if (err) {
        console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`success`);
      }
    });
  }
}
```

### onResult<sup>12+</sup>

onResult?(parameter: AbilityResult): void

拉起UIExtensionAbility终止时的回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名       | 类型                     | 必填   | 说明            |
| -------- | ---------------------- | ---- | ------------- |
| parameter | [AbilityResult](js-apis-inner-ability-abilityResult.md) | 是    | 当调用[terminateSelfWithResult](js-apis-inner-application-uiExtensionContext.md#terminateselfwithresult12)方法终止UIExtensionAbility时返回的结果。 |

**示例：**

```ts
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, Object> = {
      'time': '2023-10-23 20:45',
    };
    let abilityStartCallback: common.AbilityStartCallback = {
      onError: (code: number, name: string, message: string) => {
        console.info(`code:` + code + `name:` + name + `message:` + message);
      },
      onResult: (abilityResult: common.AbilityResult) => {
        console.info(`resultCode:` + abilityResult.resultCode + `bundleName:` + abilityResult.want?.bundleName);
      }
    };

    this.context.startAbilityByType('photoEditor', wantParam, abilityStartCallback, (err: BusinessError) => {
      if (err) {
        console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`success`);
      }
    });
  }
}
```

## OnResultFn<sup>23+</sup>

type OnResultFn = (parameter: AbilityResult) => void

拉起UIExtensionAbility终止时的回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                                    | 必填 | 说明                                                         |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| parameter | [AbilityResult](js-apis-inner-ability-abilityResult.md) | 是   | 当调用[terminateSelfWithResult](js-apis-inner-application-uiExtensionContext.md#terminateselfwithresult12)方法终止UIExtensionAbility时返回的结果。 |

**示例：**

ArkTS-Sta示例：

```ts
'use static'
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

class MyAbilityStartCallback implements common.AbilityStartCallback {
  onError(code: int, name: string, message: string): void {
    console.info(`startAbilityByType Error:` + "code:" + code + "name:" + name + "message:" + message);
  }

  onResult?: (abilityResult: common.AbilityResult) => void = (parameter: common.AbilityResult) => {
    console.info(`startAbilityByType resultCode:` + parameter.resultCode + `bundleName:` + parameter.want?.bundleName);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, RecordData> = {
      'time': '2023-10-23 20:45',
    };

    let abilityStartCallback = new MyAbilityStartCallback();

    this.context.startAbilityByType("photoEditor", wantParam, abilityStartCallback, (err: BusinessError | null) => {
      if (err) {
        console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`success`);
      }
    });
  }
}
```
