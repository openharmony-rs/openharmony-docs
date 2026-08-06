# AbilityStage

AbilityStage是一个\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_级别的组件管理器，用于进行Module级别的资源 预加载、线程创建等初始化操作，以及维护Module下的应用状态。AbilityStage与Module一一对应，即一个Module拥有一个AbilityStage。 应用的\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_/\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_在首次加载时会创建一个AbilityStage实例。当一 个Module中存在AbilityStage和其他组件（UIAbility/ExtensionAbility组件），AbilityStage实例会早于其他组件实例创建。 AbilityStage拥有[onCreate()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、[onDestroy()]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_生命周期回调和 [onAcceptWant()]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_、[onConfigurationUpdate()]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_ 、[onMemoryLevel()]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_事件回调等。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class AbilityStage--><!--Device-unnamed-declare class AbilityStage-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAboutToCreateAbility

```TypeScript
onAboutToCreateAbility(): void
```

无

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityStage-onAboutToCreateAbility(): void--><!--Device-AbilityStage-onAboutToCreateAbility(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onAboutToCreateAbility(): void {
    console.info('About to create first ability, preparing...');
    // 在此添加创建第一个Ability前的准备工作
  }
}
```

## onAcceptWant

```TypeScript
onAcceptWant(want: Want): string
```

当启动模式配置为\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的UIAbility被拉起时，会触发该回调，并返回一个 string作为待启动的UIAbility实例的唯一标识。同步接口，不支持异步回调。 如果系统中已经有相同标识的UIAbility实例存在，则复用已有实例，否则创建新的实例。 > **说明：** > > 从API version 20开始，当[AbilityStage.onAcceptWantAsync]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_实现时，本回调函数将不会被触发。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onAcceptWant(want: Want): string--><!--Device-AbilityStage-onAcceptWant(want: Want): string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Want类型参数，此处表示调用方传入的启动参数，如Ability名称，Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回开发者自定义的UIAbility标识。如果已经启动了相同标识的UIAbility，则复用该UIAbility，否则创建新的实例并启动。 |

**示例：**

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onAcceptWant(want: Want) {
    console.info('MyAbilityStage.onAcceptWant called');
    return 'com.example.test';
  }
}
```

## onAcceptWantAsync

```TypeScript
onAcceptWantAsync(want: Want): Promise<string>
```

当启动模式配置为\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的UIAbility被拉起时，会触发该回调，并返回一个 string作为待启动的UIAbility实例的唯一标识。使用Promise异步回调。 如果系统中已经有相同标识的UIAbility实例存在，则复用已有实例，否则创建新的实例。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onAcceptWantAsync(want: Want): Promise<string>--><!--Device-AbilityStage-onAcceptWantAsync(want: Want): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Want类型参数，传入需要启动的UIAbility的信息，如UIAbility名称、Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回一个string作为待启动的UIAbility实例的唯一标识。如果系统中已经有该标识的UIAbility实例存在，则复用已有实例，否则创建新的实例。 |

**示例：**

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';

class MyAbilityStage extends AbilityStage {
  async onAcceptWantAsync(want: Want): Promise<string> {
    await new Promise<string>((res, rej) => {
      setTimeout(res, 1000); // 延时1秒后执行
      console.info(`onAcceptWantAsync, want: ${JSON.stringify(want)}`);
    });
    return 'default';
  }
}
```

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

当系统全局配置（例如系统语言、深浅色等）发生变更时，会触发该回调。配置项均定义在[Configuration]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_类中。同步接口 ，不支持异步回调。 > **说明：** > > 该回调方法在实际触发时存在一定限制。例如如果开发者通过[setLanguage]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口 > 设置应用的语言，即便系统语言发生变化，系统也不再触发onConfigurationUpdate回调。详见 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onConfigurationUpdate(newConfig: Configuration): void--><!--Device-AbilityStage-onConfigurationUpdate(newConfig: Configuration): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newConfig | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 发生全局配置变更时触发回调，当前全局配置包括系统语言、深浅色模式。 |

**示例：**

```TypeScript
import { AbilityStage, Configuration } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onConfigurationUpdate(config: Configuration) {
    console.info(`MyAbilityStage.onConfigurationUpdate, language: ${config.language}`);
  }
}
```

## onCreate

```TypeScript
onCreate(): void
```

在加载Module的第一个Ability实例前，系统会先创建对应的AbilityStage实例，并在AbilityStage创建完成后，自动触发该回调。 开发者可以在该回调中执行Module的初始化操作（如资源预加载、线程创建等）。同步接口，不支持异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onCreate(): void--><!--Device-AbilityStage-onCreate(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    console.info('MyAbilityStage.onCreate is called');
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

在对应Module的最后一个Ability实例退出后会触发该回调。此方法将在正常的调度生命周期中调用，当应用程序异常退出或被终止时，将不会调用此方法。同步接口，不支持异步回调。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onDestroy(): void--><!--Device-AbilityStage-onDestroy(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onDestroy() {
    console.info('MyAbilityStage.onDestroy is called');
  }
}
```

## onLaunchFromHyperSnap

```TypeScript
onLaunchFromHyperSnap(): void
```

进程从镜像启动时调用

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityStage-onLaunchFromHyperSnap(): void--><!--Device-AbilityStage-onLaunchFromHyperSnap(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onLaunchFromHyperSnap(): void {
    console.info('Launched from Hyper Snap, reinitializing resources...');
    // 在此添加快启启动时的初始化逻辑
  }
}
```

## onMemoryLevel

```TypeScript
onMemoryLevel(level: AbilityConstant.MemoryLevel): void
```

该接口用于监听系统内存状态变化。当整机可用内存变化到指定程度时，系统会触发该回调。开发者可通过实现此接口，在收到内存紧张事件时，及时释放非必要资源（如缓存数据、临时对象等），以避免应用进程被系统强制终止。 同步接口，不支持异步回调。 > **说明：** > > onMemoryLevel回调运行在当前进程的主线程中，如果在该回调中做耗时的UI组件释放，会阻塞主线程任务，因此不建议在该回调中释放UI组件。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onMemoryLevel(level: AbilityConstant.MemoryLevel): void--><!--Device-AbilityStage-onMemoryLevel(level: AbilityConstant.MemoryLevel): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | AbilityConstant.MemoryLevel | 是 | 整机可用内存级别，对应的触发场景详见[AbilityConstant.MemoryLevel]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**示例：**

```TypeScript
import { AbilityStage, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`MyAbilityStage.onMemoryLevel, level: ${JSON.stringify(level)}`);
  }
}
```

## onNewProcessRequest

```TypeScript
onNewProcessRequest(want: Want): string
```

如果UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_4\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_5\_\_\_配置了在独立进程中运行（即 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_6\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_7\_\_\_的isolationProcess字段取值为true），当该UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_8\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_9\_\_\_被拉起时，会触发该回调，并返回一个string作为 进程唯一标识。同步接口，不支持异步回调。 如果该应用已有相同标识的进程存在，则待启动的UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_10\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_11\_\_\_运行在此进程中，否则创建新的进程。 如果开发者同时实现onNewProcessRequest和[onAcceptWant]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_，将先收到onNewProcessRequest回调，再收到 onAcceptWant回调。 \_\_\_MD\_COMMENT\_DESC\_USD\_12\_\_\_ 仅支持sys/commonUI类型的UIExtensionAbility组件在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_配置文件中配 置isolationProcess字段为true。 \_\_\_MD\_COMMENT\_DESC\_USD\_13\_\_\_ > **说明：** > > - 在API version 19及之前版本，仅支持在指定进程中启动UIAbility。\_\_\_MD\_COMMENT\_DESC\_USD\_14\_\_\_从API version 20开始，新增支持在指定进程中启动UIExtensionAbility。\_\_\_MD\_COMMENT\_DESC\_USD\_15\_\_\_ > > - 从API version 20开始，当[AbilityStage.onNewProcessRequestAsync]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_实现时，本回调函 > 数将不执行。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityStage-onNewProcessRequest(want: Want): string--><!--Device-AbilityStage-onNewProcessRequest(want: Want): string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Want类型参数，此处表示调用方传入的启动参数，如UIAbility\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或UIExtensionAbility\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_名称、Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回一个由开发者自行决定的进程字符串标识，如果之前此标识对应的进程已被创建，就让ability在此进程中运行，否则创建新的进程。 |

**示例：**

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onNewProcessRequest(want: Want) {
    console.info('MyAbilityStage.onNewProcessRequest called');
    return 'com.example.test';
  }
}
```

## onNewProcessRequestAsync

```TypeScript
onNewProcessRequestAsync(want: Want): Promise<string>
```

如果UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_2\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_3\_\_\_配置了在独立进程中运行（即 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_4\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_5\_\_\_的isolationProcess字段取值为true），当该UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_6\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_7\_\_\_被拉起时，会触发该回调，并返回一个string作为 进程唯一标识。使用Promise异步回调。 如果该应用已有相同标识的进程存在，则待启动的UIAbility\_\_\_MD\_COMMENT\_DESC\_USD\_8\_\_\_或UIExtensionAbility\_\_\_MD\_COMMENT\_DESC\_USD\_9\_\_\_运行在此进程中，否则创建新的进程。 \_\_\_MD\_COMMENT\_DESC\_USD\_10\_\_\_ 仅支持sys/commonUI类型的UIExtensionAbility组件在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中配置 isolationProcess字段为true。 \_\_\_MD\_COMMENT\_DESC\_USD\_11\_\_\_

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onNewProcessRequestAsync(want: Want): Promise<string>--><!--Device-AbilityStage-onNewProcessRequestAsync(want: Want): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Want类型参数，此处表示调用方传入的启动参数，如UIAbility\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或UIExtensionAbility\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_名称、Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回一个由开发者自定义的进程字符串标识。如果该应用已有相同标识的进程存在，则UIAbility\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或UIExtensionAbility |

**示例：**

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';

class MyAbilityStage extends AbilityStage {
  async onNewProcessRequestAsync(want: Want): Promise<string> {
    await new Promise<string>((res, rej) => {
      setTimeout(res, 1000); // 延时1秒后执行
      console.info(`onNewProcessRequestAsync, want: ${JSON.stringify(want)}`);
    });
    return '';
  }
}
```

## onPrepareTermination

```TypeScript
onPrepareTermination(): AbilityConstant.PrepareTermination
```

当应用被用户关闭时调用，可用于询问用户选择立即执行操作还是取消操作。同步接口，不支持异步回调。 > **说明：** > > - 仅当应用正常退出（例如，通过doc栏/托盘关闭应用，或者应用随设备关机而退出）时会调用该接口。如果应用被强制关闭，则不会调用该接口。 > > - 当[AbilityStage.onPrepareTerminationAsync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_实现时，本回调函数将不执行。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.PREPARE_APP_TERMINATE

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onPrepareTermination(): AbilityConstant.PrepareTermination--><!--Device-AbilityStage-onPrepareTermination(): AbilityConstant.PrepareTermination-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AbilityConstant.PrepareTermination | The user's choice. |

**示例：**

```TypeScript
import { AbilityConstant, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onPrepareTermination(): AbilityConstant.PrepareTermination {
    console.info('MyAbilityStage.onPrepareTermination is called');
    return AbilityConstant.PrepareTermination.CANCEL;
  }
}
```

## onPrepareTerminationAsync

```TypeScript
onPrepareTerminationAsync(): Promise<AbilityConstant.PrepareTermination>
```

当应用被用户关闭时调用，可用于询问用户选择立即执行操作还是取消操作。使用Promise异步回调。 > **说明：** > > - 仅当应用正常退出（例如，通过doc栏/托盘关闭应用，或者应用随设备关机而退出）时会调用该接口。如果应用被强制关闭，则不会调用该接口。 > > - 若异步回调内发生crash，按超时处理，执行等待超过10秒未响应，应用将被强制关闭。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.PREPARE_APP_TERMINATE

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-onPrepareTerminationAsync(): Promise<AbilityConstant.PrepareTermination>--><!--Device-AbilityStage-onPrepareTerminationAsync(): Promise<AbilityConstant.PrepareTermination>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityConstant.PrepareTermination&gt; | Promise used to return the user's choice. |

**示例：**

```TypeScript
import { AbilityConstant, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  async onPrepareTerminationAsync(): Promise<AbilityConstant.PrepareTermination> {
    await new Promise<AbilityConstant.PrepareTermination>((res, rej) => {
      setTimeout(res, 3000); // 延时3秒后执行
    });
    return AbilityConstant.PrepareTermination.CANCEL;
  }
}
```

## context

```TypeScript
context: AbilityStageContext
```

AbilityStage上下文。

**类型：** AbilityStageContext

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStage-context: AbilityStageContext--><!--Device-AbilityStage-context: AbilityStageContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

