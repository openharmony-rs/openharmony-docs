# Context

Context是Stage模型的上下文基类，主要用于访问特定应用程序的资源，以及执行应用级操作的回调。

**继承/实现关系：** Context extends BaseContext

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class Context--><!--Device-unnamed-declare class Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## createAreaModeContext

```TypeScript
createAreaModeContext(areaMode: contextConstant.AreaMode): Context
```

创建特定数据加密级别的应用上下文。开发者可以调用该接口创建不同加密级别的上下文，从而获取对应的沙箱路径。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Context-createAreaModeContext(areaMode: contextConstant.AreaMode): Context--><!--Device-Context-createAreaModeContext(areaMode: contextConstant.AreaMode): Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| areaMode | contextConstant.AreaMode | 是 | 指定的数据加密等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](arkts-ability-context-c.md) | 指定数据加密等级的上下文。 |

## 示例

```TypeScript
import { common, UIAbility, contextConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let areaMode: contextConstant.AreaMode = contextConstant.AreaMode.EL2;
    let areaModeContext: common.Context;
    try {
      // 创建特定数据加密级别的应用上下文
      areaModeContext = this.context.createAreaModeContext(areaMode);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'Failed to create area mode context. Code: %{public}d, message: %{public}s', err.code, err.message);
    }
  }
}
```

## createDisplayContext

```TypeScript
createDisplayContext(displayId: long): Context
```

根据指定的物理屏幕ID创建带有屏幕信息（包括屏幕密度[ScreenDensity](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-screendensity-e.md#ScreenDensity)和屏幕方向 [Direction](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-direction-e.md#Direction)）的应用上下文。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Context-createDisplayContext(displayId: long): Context--><!--Device-Context-createDisplayContext(displayId: long): Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | long | 是 | 物理屏幕ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](arkts-ability-context-c.md) | 带有指定物理屏幕信息的上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## 示例

```TypeScript
import { common, UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let displayContext: common.Context;
    try {
      // displayId通过display.getDefaultDisplay()等接口获取，详见屏幕管理开发指导
      displayContext = this.context.createDisplayContext(0);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(0x0000, 'testTag', 'Failed to create display context. Code: %{public}d, message: %{public}s', err.code, err.message);
    }
  }
}
```

## createModuleContext

```TypeScript
createModuleContext(moduleName: string): Context
```

根据模块名创建上下文。 > **说明：** > > - 仅支持获取本应用中其他Module的Context和应用内HSP的Context，不支持获取其他应用的Context。 > - 由于创建模块上下文的过程涉及资源查询与初始化，耗时相对较长，在对应用流畅性要求较高的场景下，不建议频繁或多次调用createModuleContext接口创建多个Context实例，以免影响用户体验。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [createModuleContext](arkts-ability-application-createmodulecontext-f.md#createModuleContext)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-createModuleContext(moduleName: string): Context--><!--Device-Context-createModuleContext(moduleName: string): Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](arkts-ability-context-c.md) | 模块的上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## 示例

```TypeScript
import { common, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let moduleContext: common.Context;
    try {
      // 根据模块名创建上下文
      moduleContext = this.context.createModuleContext('entry');
    } catch (error) {
      console.error(`createModuleContext failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
    }
  }
}
```

## getApplicationContext

```TypeScript
getApplicationContext(): ApplicationContext
```

获取当前应用上下文。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-getApplicationContext(): ApplicationContext--><!--Device-Context-getApplicationContext(): ApplicationContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ApplicationContext](arkts-ability-applicationcontext-c.md) | 应用上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2 .Incorrect parameter types. |

## 示例

```TypeScript
import { common, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let applicationContext: common.Context;
    try {
      // 获取当前应用上下文
      applicationContext = this.context.getApplicationContext();
    } catch (error) {
      console.error(`Failed to get application context. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
    }
  }
}
```

## getGroupDir

```TypeScript
getGroupDir(dataGroupID: string, callback: AsyncCallback<string>): void
```

通过应用中的Group ID获取对应的共享目录，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-getGroupDir(dataGroupID: string, callback: AsyncCallback<string>): void--><!--Device-Context-getGroupDir(dataGroupID: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataGroupID | string | 是 | 原子化服务类型的应用创建时，系统会指定分配唯一Group ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数。当获取共享目录成功，err为undefined，data为对应的共享目录，如果不存在则返回为空；否则为错误对象。&lt;br&gt;**说明：**仅支持应用el2加密级别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { common, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let getGroupDirContext: common.Context = this.context;

    // 通过Group ID获取共享目录（callback方式）
    getGroupDirContext.getGroupDir("1", (err: BusinessError<void> | null, data: String | undefined) => {
      if (err) {
        console.error(`getGroupDir failed, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`getGroupDir result is: ${JSON.stringify(data)}`);
      }
    });
  }
}
```

## getGroupDir

```TypeScript
getGroupDir(dataGroupID: string): Promise<string>
```

通过应用中的Group ID获取对应的共享目录，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-getGroupDir(dataGroupID: string): Promise<string>--><!--Device-Context-getGroupDir(dataGroupID: string): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataGroupID | string | 是 | 原子化服务类型的应用创建时，系统会指定分配唯一Group ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回对应的共享目录。如果不存在则返回为空，仅支持应用el2加密级别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2 .Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { common, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let groupId = '1';
    let getGroupDirContext: common.Context = this.context;
    try {
      // 通过Group ID获取共享目录（Promise方式）
      getGroupDirContext.getGroupDir(groupId).then(data => {
        console.info('getGroupDir result:' + data);
      })
    } catch (error) {
      console.error(`Failed to get group directory. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
    }
  }
}
```

## isContextOf

```TypeScript
isContextOf(contextType: contextConstant.ContextType): boolean
```

判断当前Context是否为指定的ContextType类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Context-isContextOf(contextType: contextConstant.ContextType): boolean--><!--Device-Context-isContextOf(contextType: contextConstant.ContextType): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contextType | contextConstant.ContextType | 是 | 上下文类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否为指定类型的上下文。返回true表示Context类型为指定类型，返回false表示Context类型匹配失败。 |

## 示例

```TypeScript
import { UIAbility, contextConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    hilog.info(0x0000, 'testTag', `%{public}s`, 'Ability onCreate');
    // 判断当前Context是否为指定的ContextType类型
    let result = this.context.isContextOf(contextConstant.ContextType.UIABILITY_CONTEXT);
    hilog.info(0x0000, 'testTag', `match contextType result is:%{public}s`, JSON.stringify(result));
  }
}
```

## applicationInfo

```TypeScript
applicationInfo: ApplicationInfo
```

当前应用程序的信息。

**类型：** [ApplicationInfo](arkts-ability-applicationinfo-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-applicationInfo: ApplicationInfo--><!--Device-Context-applicationInfo: ApplicationInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## area

```TypeScript
area: contextConstant.AreaMode
```

文件分区信息，按加密等级AreaMode进行分区。

**类型：** contextConstant.AreaMode

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-area: contextConstant.AreaMode--><!--Device-Context-area: contextConstant.AreaMode-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleCodeDir

```TypeScript
bundleCodeDir: string
```

安装包目录。不能拼接路径访问资源文件，请使用[资源管理接口](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#@ohos.resourceManager)访问资源，详情参考 [应用沙箱目录](../../../file-management/app-sandbox-directory.md)。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-bundleCodeDir: string--><!--Device-Context-bundleCodeDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## cacheDir

```TypeScript
cacheDir: string
```

缓存目录，详情参考[应用沙箱目录](../../../file-management/app-sandbox-directory.md)。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-cacheDir: string--><!--Device-Context-cacheDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## cloudFileDir

```TypeScript
cloudFileDir: string
```

云文件目录。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Context-cloudFileDir: string--><!--Device-Context-cloudFileDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## databaseDir

```TypeScript
databaseDir: string
```

数据库目录，详情参考[应用沙箱目录](../../../file-management/app-sandbox-directory.md)。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-databaseDir: string--><!--Device-Context-databaseDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## distributedFilesDir

```TypeScript
distributedFilesDir: string
```

分布式文件目录，详情参考[应用沙箱目录](../../../file-management/app-sandbox-directory.md)。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-distributedFilesDir: string--><!--Device-Context-distributedFilesDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## eventHub

```TypeScript
eventHub: EventHub
```

事件中心，提供订阅、取消订阅、触发事件对象。

**类型：** [EventHub](arkts-ability-eventhub-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-eventHub: EventHub--><!--Device-Context-eventHub: EventHub-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## filesDir

```TypeScript
filesDir: string
```

文件目录，详情参考[应用沙箱目录](../../../file-management/app-sandbox-directory.md)。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-filesDir: string--><!--Device-Context-filesDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## preferencesDir

```TypeScript
preferencesDir: string
```

preferences目录，详情参考[应用沙箱目录](../../../file-management/app-sandbox-directory.md)。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-preferencesDir: string--><!--Device-Context-preferencesDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

当前应用的进程名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Context-processName: string--><!--Device-Context-processName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## resourceDir

```TypeScript
resourceDir: string
```

资源目录。 > **说明：** > > 需要开发者手动在`\&lt;module-name&gt;\resource`路径下创建`resfile`目录。创建的`resfile`目录仅支持以只读方式访问。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Context-resourceDir: string--><!--Device-Context-resourceDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## resourceManager

```TypeScript
resourceManager: resmgr.ResourceManager
```

资源管理对象。

**类型：** resmgr.ResourceManager

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-resourceManager: resmgr.ResourceManager--><!--Device-Context-resourceManager: resmgr.ResourceManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## tempDir

```TypeScript
tempDir: string
```

临时目录，详情参考[应用沙箱目录](../../../file-management/app-sandbox-directory.md)。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Context-tempDir: string--><!--Device-Context-tempDir: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

