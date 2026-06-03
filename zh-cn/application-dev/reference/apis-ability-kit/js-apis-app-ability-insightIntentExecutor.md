# @ohos.app.ability.InsightIntentExecutor (意图执行基类)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本模块提供意图执行基类，开发者通过本模块对接端侧[意图框架](../../application-models/insight-intent-overview.md)，[通过配置文件开发意图](../../application-models/insight-intent-config-development.md)实现意图的业务逻辑。

除了可以通过配置文件开发意图，还可以通过装饰器开发意图。对于API version 20及以后的版本，推荐使用[通过装饰器开发意图](../../application-models/insight-intent-decorator-development.md)。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { InsightIntentExecutor } from '@kit.AbilityKit';
```

## InsightIntentExecutor

表示意图执行基类。

### 属性

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [InsightIntentContext](./js-apis-app-ability-insightIntentContext.md) | 否 | 否 | 意图执行上下文。 |

### onExecuteInUIAbilityForegroundMode

onExecuteInUIAbilityForegroundMode(name: string, param: Record\<string, Object>, pageLoader: window.WindowStage): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult>

当意图执行依赖[UIAbility](./js-apis-app-ability-uiAbility.md)组件前台启动时，会在UIAbility组件生命周期执行中触发本意图执行接口。支持同步返回和使用Promise异步返回。

- 若UIAbility组件冷启动，意图执行时UIAbility组件生命周期触发顺序：[onCreate](./js-apis-app-ability-uiAbility.md#oncreate)、[onWindowStageCreate](./js-apis-app-ability-uiAbility.md#onwindowstagecreate)、onExecuteInUIAbilityForegroundMode、[onForeground](./js-apis-app-ability-uiAbility.md#onforeground)。
- 若UIAbility组件热启动，且启动时UIAbility组件处于后台，意图执行时UIAbility组件生命周期触发顺序：[onNewWant](./js-apis-app-ability-uiAbility.md#onnewwant)、onExecuteInUIAbilityForegroundMode、[onForeground](./js-apis-app-ability-uiAbility.md#onforeground)。
- 若UIAbility组件热启动，且启动时UIAbility组件处于前台，意图执行时UIAbility组件生命周期触发顺序：onExecuteInUIAbilityForegroundMode。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 意图名称。 |
| param | Record\<string, Object> | 是 | 意图参数，表示本次意图执行由系统入口传递给应用的数据。 |
| pageLoader | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 表示windowStage实例对象，和[onWindowStageCreate](./js-apis-app-ability-uiAbility.md#onwindowstagecreate)接口的windowStage实例是同一个，可用于加载意图执行的页面。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) \| Promise<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | 返回意图执行结果或返回带有意图执行结果的Promise对象，表示本次意图执行返回给系统入口的数据。 |

**示例：**

同步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
      pageLoader: window.WindowStage): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发者定义
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      // 若开发者需要加载意图内容，pages/IntentPage即为意图页面
      pageLoader.loadContent('pages/IntentPage', (err, data) => {
        if (err.code) {
          hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        } else {
          hilog.info(0x0000, 'testTag', '%{public}s', 'Succeeded in loading the content');
        }
      });

      result = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```

使用Promise异步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    })
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // 实现异步接口需要使用async/await语法糖，通过async声明该接口是一个异步函数
    async onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
      pageLoader: window.WindowStage): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发者定义
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInUIAbilityForegroundMode<sup>23+</sup>

onExecuteInUIAbilityForegroundMode(name: string, param: Record\<string, RecordData>, pageLoader: window.WindowStage): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult>

当意图调用的目的是将UIAbility显示在前台时，触发该回调。支持同步返回和使用Promise异步返回。

- 若UIAbility冷启动，意图调用时UIAbility生命周期触发顺序：onCreate、onWindowStageCreate、onExecuteInUIAbilityForegroundMode、onForeground。
- 若UIAbility热启动，且启动时UIAbility处于后台，意图调用时UIAbility生命周期触发顺序：onNewWant、onExecuteInUIAbilityForegroundMode、onForeground。
- 若UIAbility热启动，且启动时UIAbility处于前台，意图调用时UIAbility生命周期触发顺序：onExecuteInUIAbilityForegroundMode。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明           |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| name       | string                                                       | 是   | 意图调用名称。 |
| param      | Record\<string, RecordData>                                  | 是   | 意图调用参数。 |
| pageLoader | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是   | 页面加载器。   |

**返回值：**

| 类型                                                         | 说明                                |
| ------------------------------------------------------------ | ----------------------------------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) | 意图调用执行结果。                  |
| Promise\<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | Promise对象，返回意图调用执行结果。 |

**示例：**

直接返回意图调用的结果，示例如下：

  ```ts
  // ArkTS-Sta示例  
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { RecordData } from '@kit.BasicServicesKit';
  
  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, RecordData>,
      pageLoader: window.WindowStage): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发人员决定
          code: 404,
          result: {
            'message': 'Unsupported insight intent.',
          } as Record<string, RecordData>
        };
        return result;
      }
  
      // 若开发者需加载内容
      pageLoader.loadContent('pages/Index', (err, data) => {
        if (err?.code) {
          hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        } else {
          hilog.info(0x0000, 'testTag', '%{public}s', 'Succeeded in loading the content');
        }
      });
  
      result = {
        code: 0,
        result: {
          'message': 'Execute insight intent succeed.',
        } as Record<string, RecordData>
      };
      return result;
    }
  }
  ```

使用Promise异步返回意图调用的结果，示例如下：

  ```ts
  // ArkTS-Sta示例  
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { RecordData } from '@kit.BasicServicesKit';
  
  async function executeInsightIntent(param: Record<string, RecordData>): Promise<insightIntent.ExecuteResult> {
    return new Promise<insightIntent.ExecuteResult>((resolve, reject) => { // 添加泛型类型
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          'message': 'Execute insight intent succeed.',
        } as Record<string, RecordData>
      };
      resolve(result);
    });
  }
  
  export default class IntentExecutorImpl extends InsightIntentExecutor {
    async onExecuteInUIAbilityForegroundMode(
      name: string,
      param: Record<string, RecordData>,
      pageLoader: window.WindowStage
    ): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
  
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          code: 404,
          result: {
            'message': 'Unsupported insight intent.',
          } as Record<string, RecordData>
        };
        return result;
      }
  
      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInUIAbilityBackgroundMode

onExecuteInUIAbilityBackgroundMode(name: string, param: Record\<string, Object>): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult>

当意图执行依赖[UIAbility](./js-apis-app-ability-uiAbility.md)组件后台启动时，会在UIAbility组件生命周期执行中触发本意图执行接口。支持同步返回和使用Promise异步返回。

- 若UIAbility组件冷启动，意图执行时UIAbility组件生命周期触发顺序：[onCreate](./js-apis-app-ability-uiAbility.md#oncreate)、onExecuteInUIAbilityBackgroundMode、[onBackground](./js-apis-app-ability-uiAbility.md#onbackground)。
- 若UIAbility组件热启动，意图执行时UIAbility组件生命周期触发顺序：onExecuteInUIAbilityBackgroundMode。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 意图名称。 |
| param | Record\<string, Object> | 是 | 意图参数，表示本次意图执行由系统入口传递给应用的数据。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) \| Promise\<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | 返回意图执行结果或返回带有意图执行结果的Promise对象，表示本次意图执行返回给系统入口的数据。 |

**示例：**

同步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIAbilityBackgroundMode(name: string, param: Record<string, Object>): insightIntent.ExecuteResult {
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

使用Promise异步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    })
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // 实现异步接口需要使用async/await语法糖，通过async声明该接口是一个异步函数
    async onExecuteInUIAbilityBackgroundMode(name: string,
      param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInUIAbilityBackgroundMode<sup>23+</sup>

onExecuteInUIAbilityBackgroundMode(name: string, param: Record\<string, RecordData>): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult>

当意图调用的目的是将UIAbility从后台拉起时，触发该回调。支持同步返回和使用Promise异步返回。

- 若UIAbility冷启动，意图调用时UIAbility生命周期触发顺序：onCreate、onExecuteInUIAbilityBackgroundMode、onBackground。
- 若UIAbility热启动，意图调用时UIAbility生命周期触发顺序：onExecuteInUIAbilityBackgroundMode。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                        | 必填 | 说明           |
| ------ | --------------------------- | ---- | -------------- |
| name   | string                      | 是   | 意图调用名称。 |
| param  | Record\<string, RecordData> | 是   | 意图调用参数。 |

**返回值：**

| 类型                                                         | 说明                                |
| ------------------------------------------------------------ | ----------------------------------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) | 意图调用执行结果。                  |
| Promise\<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | Promise对象，返回意图调用执行结果。 |

**示例：**

直接返回意图调用的结果，示例如下：

  ```ts
  // ArkTS-Sta示例  
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { RecordData } from '@kit.BasicServicesKit';
  
  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIAbilityBackgroundMode(name: string, param: Record<string, RecordData>): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          'message': 'Execute insight intent succeed.',
        } as Record<string, RecordData>
      };
      return result;
    }
  }
  ```

使用Promise异步返回意图调用的结果，示例如下：

  ```ts
  // ArkTS-Sta示例  
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { RecordData } from '@kit.BasicServicesKit';
  
  async function executeInsightIntent(param: Record<string, RecordData>): Promise<insightIntent.ExecuteResult> {
    return new Promise<insightIntent.ExecuteResult>((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          'message': 'Execute insight intent succeed.',
        } as Record<string, RecordData>
      };
      resolve(result);
    })
  }
  
  export default class IntentExecutorImpl extends InsightIntentExecutor {
    async onExecuteInUIAbilityBackgroundMode(name: string,
      param: Record<string, RecordData>): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInUIExtensionAbility

onExecuteInUIExtensionAbility(name: string, param: Record\<string, Object>, pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult>

当意图执行依赖[UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md)启动时，会在UIExtensionAbility组件生命周期执行中触发本意图执行接口。支持同步返回和使用Promise异步返回。

- 意图执行时UIExtensionAbility生命周期触发顺序：[onCreate](./js-apis-app-ability-uiExtensionAbility.md#oncreate)、[onSessionCreate](./js-apis-app-ability-uiExtensionAbility.md#onsessioncreate)、onExecuteInUIExtensionAbility、[onForeground](./js-apis-app-ability-uiExtensionAbility.md#onforeground)。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 意图名称。 |
| param | Record\<string, Object> | 是 | 意图参数，表示本次意图执行由系统入口传递给应用的数据。 |
| pageLoader | [UIExtensionContentSession](js-apis-app-ability-uiExtensionContentSession.md) | 是 | 表示UIExtensionContentSession实例对象，和[onSessionCreate](./js-apis-app-ability-uiExtensionAbility.md#onsessioncreate)接口的UIExtensionContentSession实例是同一个，可用于加载意图执行的页面。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) \| Promise\<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | 返回意图执行结果或返回带有意图执行结果的Promise对象，表示本次意图执行返回给系统入口的数据。 |

**示例：**

同步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>,
      pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发者定义
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      // 若开发者需要加载意图内容，pages/Index即为意图页面
      pageLoader.loadContent('pages/Index');

      result = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```

使用Promise异步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    })
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // 实现异步接口需要使用async/await语法糖，通过async声明该接口是一个异步函数
    async onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>,
      pageLoader: UIExtensionContentSession): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发者定义
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInUIExtensionAbility<sup>23</sup>

onExecuteInUIExtensionAbility(name: string, param: Record\<string, RecordData>, pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult\>

当意图调用是拉起UIExtensionAbility时，触发该回调。支持同步返回和使用Promise异步返回。

意图调用时UIExtensionAbility生命周期触发顺序：onCreate、onSessionCreate、onExecuteInUIExtensionAbility、onForeground。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明           |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| name       | string                                                       | 是   | 意图调用名称。 |
| param      | Record\<string, RecordData>                                  | 是   | 意图调用参数。 |
| pageLoader | [UIExtensionContentSession](js-apis-app-ability-uiExtensionContentSession.md) | 是   | 页面加载器。   |

**返回值：**

| 类型                                                         | 说明                                |
| ------------------------------------------------------------ | ----------------------------------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) | 意图调用执行结果。                  |
| Promise\<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | Promise对象，返回意图调用执行结果。 |

**示例：**

直接返回意图调用的结果，示例如下：

  ```ts
  // ArkTS-Sta示例 
  import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { RecordData } from '@kit.BasicServicesKit';
  
  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIExtensionAbility(name: string, param: Record<string, RecordData>,
      pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发人员决定
          code: 404,
          result: {
            'message': 'Unsupported insight intent.',
          } as Record<string, RecordData>
        };
        return result;
      }
  
      // 若开发者需加载内容
      pageLoader.loadContent('pages/Index');
  
      result = {
        code: 0,
        result: {
          'message': 'Execute insight intent succeed.',
        } as Record<string, RecordData>
      };
      return result;
    }
  }
  ```

使用Promise异步返回意图调用的结果，示例如下：

  ```ts
  // ArkTS-Sta示例  
  import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { RecordData } from '@kit.BasicServicesKit';
  
  async function executeInsightIntent(param: Record<string, RecordData>): Promise<insightIntent.ExecuteResult> {
    return new Promise<insightIntent.ExecuteResult>((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          'message': 'Execute insight intent succeed.',
        } as Record<string, RecordData>
      };
      resolve(result);
    })
  }
  
  export default class IntentExecutorImpl extends InsightIntentExecutor {
    async onExecuteInUIExtensionAbility(name: string, param: Record<string, RecordData>,
      pageLoader: UIExtensionContentSession): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发人员决定
          code: 404,
          result: {
            'message': 'Unsupported insight intent.',
          } as Record<string, RecordData>
        };
        return result;
      }

      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInServiceExtensionAbility

onExecuteInServiceExtensionAbility(name: string, param: Record\<string, Object>): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult>

当意图执行依赖ServiceExtensionAbility组件启动时，会在ServiceExtensionAbility组件生命周期执行中触发本意图执行接口。支持同步返回和使用Promise异步返回。

意图执行时ServiceExtensionAbility生命周期触发顺序：onCreate、onRequest、onExecuteInServiceExtensionAbility。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 意图名称。 |
| param | Record\<string, Object> | 是 | 意图参数，表示本次意图执行由系统入口传递给应用的数据。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) \| Promise<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | 返回意图执行结果或返回带有意图执行结果的Promise对象，表示本次意图执行返回给系统入口的数据。 |

**示例：**

同步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInServiceExtensionAbility(name: string, param: Record<string, Object>): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发者定义
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```

使用Promise异步返回意图执行结果的示例如下：
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    });
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // 实现异步接口需要使用async/await语法糖，通过async声明该接口是一个异步函数
    async onExecuteInServiceExtensionAbility(name: string,
      param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发者定义
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInServiceExtensionAbility<sup>23+</sup>

onExecuteInServiceExtensionAbility(name: string, param: Record\<string, RecordData>): insightIntent.ExecuteResult | Promise\<insightIntent.ExecuteResult>

当意图调用是拉起ServiceExtensionAbility时，触发该回调。支持同步返回和使用Promise异步返回。

意图调用时ServiceExtensionAbility生命周期触发顺序：onCreate、onRequest、onExecuteInServiceExtensionAbility。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                        | 必填 | 说明           |
| ------ | --------------------------- | ---- | -------------- |
| name   | string                      | 是   | 意图调用名称。 |
| param  | Record\<string, RecordData> | 是   | 意图调用参数。 |

**返回值：**

| 类型                                                         | 说明                                |
| ------------------------------------------------------------ | ----------------------------------- |
| [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) | 意图调用执行结果。                  |
| Promise\<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | Promise对象，返回意图调用执行结果。 |

**示例：**

直接返回意图调用的结果，示例如下：

  ```ts
  // ArkTS-Sta示例 
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { RecordData } from '@kit.BasicServicesKit';
  
  
  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInServiceExtensionAbility(name: string, param: Record<string, RecordData>): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // 由开发人员决定
          code: 404,
          result: {
            'message': 'Unsupported insight intent.',
          } as Record<string, RecordData>
  
        };
        return result;
      }
  
      result = {
        code: 0,
        result: {
          'message': 'Execute insight intent succeed.',
        } as Record<string, RecordData>
      };
      return result;
    }
  }
  ```

使用Promise异步返回意图调用的结果，示例如下：

  ```ts
   // ArkTS-Sta示例   
   import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { RecordData } from '@kit.BasicServicesKit';
   
   async function executeInsightIntent(param: Record<string, RecordData>): Promise<insightIntent.ExecuteResult> {
     return new Promise<insightIntent.ExecuteResult>((resolve, reject) => {
       let result: insightIntent.ExecuteResult = {
         code: 0,
         result: {
           'message': 'Execute insight intent succeed.',
         } as Record<string, RecordData>
       };
       resolve(result);
     });
   }
   
   export default class IntentExecutorImpl extends InsightIntentExecutor {
     async onExecuteInServiceExtensionAbility(name: string,
       param: Record<string, RecordData>): Promise<insightIntent.ExecuteResult> {
       let result: insightIntent.ExecuteResult;
       if (name !== 'SupportedInsightIntentName') {
         hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
         result = {
           // 由开发人员决定
           code: 404,
           result: {
             'message': 'Unsupported insight intent.',
           } as Record<string, RecordData>
         };
         return result;
       }

       result = await executeInsightIntent(param);
       return result;
     }
   }
  ```