# AutoFillExtensionAbility（系统接口）

AutoFillExtensionAbility模块支持账号、密码、地址等多种数据类型的自动填充与保存，继承自[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)。

**继承/实现关系：** AutoFillExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**起始版本：** 11

<!--Device-unnamed-declare class AutoFillExtensionAbility extends ExtensionAbility--><!--Device-unnamed-declare class AutoFillExtensionAbility extends ExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { AutoFillExtensionAbility } from '@kit.AbilityKit';
```

<a id="onbackground"></a>
## onBackground

```TypeScript
onBackground(): void
```

当AutoFillExtensionAbility从前台转到后台时触发。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onBackground(): void--><!--Device-AutoFillExtensionAbility-onBackground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { AutoFillExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onBackground() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onBackground');
  }
}

```

<a id="oncreate"></a>
## onCreate

```TypeScript
onCreate(): void
```

AutoFillExtensionAbility创建时触发回调函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onCreate(): void--><!--Device-AutoFillExtensionAbility-onCreate(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { AutoFillExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onCreate() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onCreate');
  }
}

```

<a id="ondestroy"></a>
## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

在AutoFillExtensionAbility销毁时回调，执行资源清理等操作。回调结束直接返回，或者使用Promise异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onDestroy(): void | Promise<void>--><!--Device-AutoFillExtensionAbility-onDestroy(): void | Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { AutoFillExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onDestroy() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onDestroy');
  }
}

```

<a id="onfillrequest"></a>
## onFillRequest

```TypeScript
onFillRequest(session: UIExtensionContentSession, request: FillRequest, callback: FillRequestCallback): void
```

当发起自动填充请求或者生成密码时触发此回调函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onFillRequest(session: UIExtensionContentSession, request: FillRequest, callback: FillRequestCallback): void--><!--Device-AutoFillExtensionAbility-onFillRequest(session: UIExtensionContentSession, request: FillRequest, callback: FillRequestCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md) | 是 | AutoFillExtensionAbility界面内容相关信息。 |
| request | [FillRequest](arkts-ability-autofillrequest-fillrequest-i-sys.md) | 是 | 自动填充数据。 |
| callback | [FillRequestCallback](arkts-ability-autofillrequest-fillrequestcallback-i-sys.md) | 是 | 自动填充请求回调。 |

**示例：**

```TypeScript
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onFillRequest(session: UIExtensionContentSession,
                request: autoFillManager.FillRequest,
                callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    hilog.info(0x0000, 'testTag', 'fill requestCallback: %{public}s', JSON.stringify(callback));
    hilog.info(0x0000, 'testTag', 'get request viewData: %{public}s', JSON.stringify(request.viewData));
    try {
      // 定义本地存储数据
      let localStorageData: Record<string, UIExtensionContentSession | string | autoFillManager.FillRequestCallback |
      autoFillManager.ViewData | common.AutoFillExtensionContext> = {
        'session': session,
        'message': 'AutoFill Page',
        'saveCallback': callback,
        'viewData': request.viewData,
        'context': this.context
      };
      // 创建本地存储实例，用于在页面间传递数据
      let storage_fill = new LocalStorage(localStorageData);
      if (session) {
        // 加载自动保存页面
        session.loadContent('pages/SelectorList', storage_fill);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}

```

<a id="onforeground"></a>
## onForeground

```TypeScript
onForeground(): void
```

当AutoFillExtensionAbility从后台转到前台时触发。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onForeground(): void--><!--Device-AutoFillExtensionAbility-onForeground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { AutoFillExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onForeground() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onForeground');
  }
}

```

<a id="onsaverequest"></a>
## onSaveRequest

```TypeScript
onSaveRequest(session: UIExtensionContentSession, request: SaveRequest, callback: SaveRequestCallback): void
```

当发起自动保存或者手动保存时触发此回调函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onSaveRequest(session: UIExtensionContentSession, request: SaveRequest, callback: SaveRequestCallback): void--><!--Device-AutoFillExtensionAbility-onSaveRequest(session: UIExtensionContentSession, request: SaveRequest, callback: SaveRequestCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md) | 是 | AutoFillExtensionAbility界面内容相关信息。 |
| request | [SaveRequest](arkts-ability-autofillmanager-saverequest-t.md) | 是 | 保存请求数据。 |
| callback | [SaveRequestCallback](arkts-ability-autofillmanager-saverequestcallback-t-sys.md) | 是 | 保存请求回调。 |

**示例：**

```TypeScript
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onSaveRequest(session : UIExtensionContentSession,
                request : autoFillManager.SaveRequest,
                callback : autoFillManager.SaveRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onSaveRequest');
    try {
      // 定义本地存储数据
      let localStorageData: Record<string, UIExtensionContentSession | string | autoFillManager.SaveRequestCallback |
      autoFillManager.ViewData | common.AutoFillExtensionContext> = {
        'session': session,
        'message': 'AutoFill Page',
        'fillCallback': callback,
        'viewData': request.viewData,
        'context': this.context,
      };
      // 创建本地存储实例，用于在页面间传递数据
      let storage_save = new LocalStorage(localStorageData);
      if (session) {
        // 加载自动保存页面
        session.loadContent('pages/SavePage', storage_save);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}

```

<a id="onsessiondestroy"></a>
## onSessionDestroy

```TypeScript
onSessionDestroy(session: UIExtensionContentSession): void
```

当AutoFillExtensionAbility界面内容对象销毁后调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onSessionDestroy(session: UIExtensionContentSession): void--><!--Device-AutoFillExtensionAbility-onSessionDestroy(session: UIExtensionContentSession): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md) | 是 | AutoFillExtensionAbility界面内容相关信息。 |

**示例：**

```TypeScript
import { AutoFillExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onSessionDestroy(session : UIExtensionContentSession) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onSessionDestroy');
  }
}

```

<a id="onupdaterequest"></a>
## onUpdateRequest

```TypeScript
onUpdateRequest(request: UpdateRequest): void
```

当收到更新请求时触发此回调函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-onUpdateRequest(request: UpdateRequest): void--><!--Device-AutoFillExtensionAbility-onUpdateRequest(request: UpdateRequest): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [UpdateRequest](arkts-ability-autofillrequest-updaterequest-i-sys.md) | 是 | 更新请求。 |

**示例：**

```TypeScript
import { AutoFillExtensionAbility, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onUpdateRequest(request: autoFillManager.UpdateRequest) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'on update request, view data is: %{public}s',
      JSON.stringify(request.viewData));
  }
}

```

## context

```TypeScript
context: AutoFillExtensionContext
```

AutoFillExtension的上下文环境，继承自ExtensionContext。

**类型：** AutoFillExtensionContext

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionAbility-context: AutoFillExtensionContext--><!--Device-AutoFillExtensionAbility-context: AutoFillExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

