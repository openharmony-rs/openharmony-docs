# InsightIntentContext

本模块提供意图执行上下文，是[意图执行基类](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md)和[@InsightIntentEntry的意图执行基类](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md)的属性，为意图执行提供基础能力，例如启动本应用内的[UIAbility组件](arkts-app-ability-uiability.md)。

**起始版本：** 11

<!--Device-unnamed-declare class InsightIntentContext--><!--Device-unnamed-declare class InsightIntentContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentContext } from '@kit.AbilityKit';
```

<a id="setreturnmodeforuiabilityforeground"></a>
## setReturnModeForUIAbilityForeground

```TypeScript
setReturnModeForUIAbilityForeground(returnMode: insightIntent.ReturnMode): void
```

设置意图执行结果的返回形式，适用于执行模式为[UI_ABILITY_FOREGROUND](arkts-ability-insightintent-executemode-e.md)的意图。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-InsightIntentContext-setReturnModeForUIAbilityForeground(returnMode: insightIntent.ReturnMode): void--><!--Device-InsightIntentContext-setReturnModeForUIAbilityForeground(returnMode: insightIntent.ReturnMode): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| returnMode | insightIntent.ReturnMode | 是 | 意图执行结果的返回形式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. Possible causes: 1.The context is not insightIntentContext; 2.The context is not for UIAbility foreground insight intent execute mode. |

**示例：**

```TypeScript
import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class InsightIntentExecutorUI extends InsightIntentExecutor {
  onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
    pageLoader: window.WindowStage): insightIntent.ExecuteResult {
    hilog.info(0x0000, 'testTag', 'onExecuteInUIAbilityForegroundMode %{public}s', name);
    let result: insightIntent.ExecuteResult;
    result = {
      code: 0,
      result: {
        message: 'Unsupported insight intent.',
      },
    };

    try {
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to setReturnModeForUIAbilityForeground. Code: ${err.code}, message: ${err.message}`);
    }

    let localStorageData: Record<string, number> = {
      'insightId': this.context.instanceId,
    };
    let storage: LocalStorage = new LocalStorage(localStorageData);
    pageLoader.loadContent('pages/UIAbilityIndex', storage, (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
      } else {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Succeeded in loading the content');
      }
    });
    return result;
  }
}

```

<a id="setreturnmodeforuiextensionability"></a>
## setReturnModeForUIExtensionAbility

```TypeScript
setReturnModeForUIExtensionAbility(returnMode: insightIntent.ReturnMode): void
```

设置意图执行结果的返回形式，适用于执行模式为[UI_EXTENSION_ABILITY](arkts-ability-insightintent-executemode-e.md)的意图。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-InsightIntentContext-setReturnModeForUIExtensionAbility(returnMode: insightIntent.ReturnMode): void--><!--Device-InsightIntentContext-setReturnModeForUIExtensionAbility(returnMode: insightIntent.ReturnMode): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| returnMode | insightIntent.ReturnMode | 是 | 意图执行结果的返回形式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. Possible causes: 1.The context is not insightIntentContext; 2.The context is not for UIExtensionAbility insight intent execute mode. |

**示例：**

```TypeScript
import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class InsightIntentExecutorUI extends InsightIntentExecutor {
  onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>,
    pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult {
    hilog.info(0x0000, 'testTag', 'onExecuteInUIExtensionAbility %{public}s', name);
    let result: insightIntent.ExecuteResult;
    result = {
      code: 0,
      result: {
        message: 'Unsupported insight intent.',
      },
    };
    try {
      this.context.setReturnModeForUIExtensionAbility(insightIntent.ReturnMode.FUNCTION)
    } catch (error) {
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag setReturnModeForUIExtensionAbility fail, error code: ${code}, error msg: ${msg}.`);
    }

    try {
      let localStorageData: Record<string, number> = {
        'insightId': this.context.instanceId,
      };
      let storage: LocalStorage = new LocalStorage(localStorageData);
      storage.setOrCreate('session', pageLoader);
      pageLoader.loadContent('pages/UIExtensionPage', storage);
    } catch (err) {
      const error: BusinessError = err as BusinessError;
      console.error(`Failed to loadContent. Code: ${error.code}, message: ${error.message}`);
    }
    return result;
  }
}

```

<a id="startability"></a>
## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

启动UIAbility组件，仅支持启动本应用内的UIAbility组件。使用callback异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InsightIntentContext-startAbility(want: Want, callback: AsyncCallback<void>): void--><!--Device-InsightIntentContext-startAbility(want: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动UIAbility组件的want信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { InsightIntentExecutor, insightIntent, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class IntentExecutorImpl extends InsightIntentExecutor {
  onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
    pageLoader: window.WindowStage): insightIntent.ExecuteResult {
    let want: Want = {
      bundleName: 'com.ohos.intentExecuteDemo', // 此处仅为示例，开发者在实际使用中需替换为真实包名
      moduleName: 'entry',
      abilityName: 'AnotherAbility',
    };

    try {
      this.context.startAbility(want, (error) => {
        if (error) {
          hilog.error(0x0000, 'testTag', 'Start ability failed with %{public}s', JSON.stringify(error));
        } else {
          hilog.info(0x0000, 'testTag', '%{public}s', 'Start ability succeed');
        }
      })
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to start ability. Code: ${err.code}, message: ${err.message}`);
    }

    let result: insightIntent.ExecuteResult = {
      code: 0,
      result: {
        message: 'Execute insight intent succeed.',
      }
    };
    return result;
  }
}

```

<a id="startability-1"></a>
## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

启动UIAbility组件，仅支持启动本应用内的UIAbility组件。使用Promise异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InsightIntentContext-startAbility(want: Want): Promise<void>--><!--Device-InsightIntentContext-startAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动UIAbility组件的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { InsightIntentExecutor, insightIntent, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class IntentExecutorImpl extends InsightIntentExecutor {
  async onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
    pageLoader: window.WindowStage): Promise<insightIntent.ExecuteResult> {
    let want: Want = {
      bundleName: 'com.ohos.intentExecuteDemo', // 此处仅为示例，开发者在实际使用中需替换为真实包名
      moduleName: 'entry',
      abilityName: 'AnotherAbility',
    };

    try {
      await this.context.startAbility(want);
      hilog.info(0x0000, 'testTag', '%{public}s', 'Start ability finished');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to start ability. Code: ${err.code}, message: ${err.message}`);
    }

    let result: insightIntent.ExecuteResult = {
      code: 0,
      result: {
        message: 'Execute insight intent succeed.',
      }
    };
    return result;
  }
}

```

## instanceId

```TypeScript
instanceId: number
```

意图实例唯一ID。用于通过[insightIntentProvider.sendExecuteResult接口](@ohos.app.ability.insightIntentProvider:insightIntentProvider.sendExecuteResult) 和[insightIntentProvider.sendIntentResult接口](@ohos.app.ability.insightIntentProvider:insightIntentProvider.sendIntentResult)返回指定意图的执行结果。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-InsightIntentContext-instanceId: int--><!--Device-InsightIntentContext-instanceId: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

