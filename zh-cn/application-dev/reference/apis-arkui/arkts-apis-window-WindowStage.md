# Interface (WindowStage)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @waterwin-->
<!--Designer: @nyankomiya-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本Interface首批接口从API version 9开始支持。

窗口管理器。管理各个基本窗口单元，即[Window](arkts-apis-window-Window.md)实例。

下列API示例中都需在[onWindowStageCreate()](../apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate)函数中使用WindowStage的实例调用对应方法。

## 导入模块

```ts
import { window } from '@kit.ArkUI';
```

## getMainWindow<sup>9+</sup>

getMainWindow(callback: AsyncCallback&lt;Window&gt;): void

获取该WindowStage实例下的主窗口，使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                                   | 必填 | 说明                                          |
| -------- | -------------------------------------- | ---- | --------------------------------------------- |
| callback | AsyncCallback&lt;[Window](arkts-apis-window-Window.md)&gt; | 是   | 回调函数。返回当前WindowStage下的主窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
    });
  }
};
```

## getMainWindow<sup>9+</sup>

getMainWindow(): Promise&lt;Window&gt;

获取该WindowStage实例下的主窗口，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**返回值：**

| 类型                             | 说明                                             |
| -------------------------------- | ------------------------------------------------ |
| Promise&lt;[Window](arkts-apis-window-Window.md)&gt; | Promise对象。返回当前WindowStage下的主窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    let promise = windowStage.getMainWindow();
    promise.then((data) => {
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
    }).catch((err: BusinessError) => {
      console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
    });
  }
};
```

## getMainWindowSync<sup>9+</sup>

getMainWindowSync(): Window

获取该WindowStage实例下的主窗口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**返回值：**

| 类型 | 说明 |
| ----------------- | --------------------------------- |
| [Window](arkts-apis-window-Window.md) | 返回当前WindowStage下的主窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**
<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      let windowClass = windowStage.getMainWindowSync();
    } catch (exception) {
      console.error(`Failed to obtain the main window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## createSubWindow<sup>9+</sup>

createSubWindow(name: string, callback: AsyncCallback&lt;Window&gt;): void

创建该WindowStage实例下的子窗口，使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                                   | 必填 | 说明                                          |
| -------- | -------------------------------------- | ---- | --------------------------------------------- |
| name     | string                                 | 是   | 子窗口的名字。                                |
| callback | AsyncCallback&lt;[Window](arkts-apis-window-Window.md)&gt; | 是   | 回调函数。返回当前WindowStage下的子窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: Incorrect parameter types. |
| 1300002 | This window state is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    try {
      windowStage.createSubWindow('mySubWindow', (err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to create the subwindow. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        console.info('Succeeded in creating the subwindow. Data: ' + JSON.stringify(data));
        if (!windowClass) {
          console.info('Failed to load the content. Cause: windowClass is null');
        }
        else {
          windowClass.resize(500, 1000);
        }
      });
    } catch (exception) {
      console.error(`Failed to create the subwindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## createSubWindow<sup>9+</sup>

createSubWindow(name: string): Promise&lt;Window&gt;

创建该WindowStage实例下的子窗口，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| name   | string | 是   | 子窗口的名字。 |

**返回值：**

| 类型                             | 说明                                             |
| -------------------------------- | ------------------------------------------------ |
| Promise&lt;[Window](arkts-apis-window-Window.md)&gt; | Promise对象。返回当前WindowStage下的子窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: Incorrect parameter types. |
| 1300002 | This window state is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    try {
      let promise = windowStage.createSubWindow('mySubWindow');
      promise.then((data) => {
        windowClass = data;
        console.info('Succeeded in creating the subwindow. Data: ' + JSON.stringify(data));
      }).catch((err: BusinessError) => {
        console.error(`Failed to create the subwindow. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to create the subwindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## createSubWindowWithOptions<sup>11+</sup>

createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise&lt;Window&gt;

创建该WindowStage实例下的子窗口，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| name   | string | 是   | 子窗口的名字。 |
| options  | [SubWindowOptions](arkts-apis-window-i.md#subwindowoptions11) | 是   | 子窗口参数。  |

**返回值：**

| 类型                             | 说明                                             |
| -------------------------------- | ------------------------------------------------ |
| Promise&lt;[Window](arkts-apis-window-Window.md)&gt; | Promise对象。返回当前WindowStage下创建的子窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: Incorrect parameter types. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    try {
      let options : window.SubWindowOptions = {
        title: 'title',
        decorEnabled: true
      };
      let promise = windowStage.createSubWindowWithOptions('mySubWindow', options);
      promise.then((data) => {
        windowClass = data;
        console.info('Succeeded in creating the subwindow. Data: ' + JSON.stringify(data));
      }).catch((err: BusinessError) => {
        console.error(`Failed to create the subwindow. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to create the subwindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## getSubWindow<sup>9+</sup>

getSubWindow(callback: AsyncCallback&lt;Array&lt;Window&gt;&gt;): void

获取该WindowStage实例下的所有子窗口，使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                              |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------- |
| callback | AsyncCallback&lt;Array&lt;[Window](arkts-apis-window-Window.md)&gt;&gt; | 是   | 回调函数。返回当前WindowStage下的所有子窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 1300002 | This window state is abnormal. |

**示例：**
<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window[] = [];
    windowStage.getSubWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the subwindow. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the subwindow. Data: ' + JSON.stringify(data));
    });
  }
};
```

## getSubWindow<sup>9+</sup>

getSubWindow(): Promise&lt;Array&lt;Window&gt;&gt;

获取该WindowStage实例下的所有子窗口，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**返回值：**

| 类型                                          | 说明                                                 |
| --------------------------------------------- | ---------------------------------------------------- |
| Promise&lt;Array&lt;[Window](arkts-apis-window-Window.md)&gt;&gt; | Promise对象。返回当前WindowStage下的所有子窗口对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 1300002 | This window state is abnormal. |

**示例：**
<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window[] = [];
    let promise = windowStage.getSubWindow();
    promise.then((data) => {
      windowClass = data;
      console.info('Succeeded in obtaining the subwindow. Data: ' + JSON.stringify(data));
    }).catch((err: BusinessError) => {
      console.error(`Failed to obtain the subwindow. Cause code: ${err.code}, message: ${err.message}`);
    });
  }
};
```

## loadContent<sup>9+</sup>

loadContent(path: string, storage: LocalStorage, callback: AsyncCallback&lt;void&gt;): void

根据当前工程中指定的页面路径为WindowStage的主窗口加载具体页面内容，通过LocalStorage传递状态属性给加载的页面，使用callback异步回调。建议在UIAbility启动过程中调用该接口，重复调用将首先销毁旧的页面内容（即UIContent）再加载新页面内容，请谨慎使用。当前UI的执行上下文可能不明确，所以不建议在回调函数中做UI相关的操作。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                                            | 必填 | 说明                                                         |
| -------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| path     | string                                          | 是   | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main_pages.json文件中。  |
| storage  | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | 是   | 页面级UI状态存储单元，这里用于为加载到窗口的页面内容传递状态属性。 |
| callback | AsyncCallback&lt;void&gt;                       | 是   | 回调函数。                                                   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Invalid path parameter.|
| 1300002 | This window state is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  storage: LocalStorage = new LocalStorage();

  onWindowStageCreate(windowStage: window.WindowStage) {
    this.storage.setOrCreate('storageSimpleProp', 121);
    console.info('onWindowStageCreate');
    try {
      windowStage.loadContent('pages/page2', this.storage, (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in loading the content.');
      });
    } catch (exception) {
      console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## loadContent<sup>9+</sup>

loadContent(path: string, storage?: LocalStorage): Promise&lt;void&gt;

根据当前工程中指定的页面路径为WindowStage的主窗口加载具体页面内容，通过LocalStorage传递状态属性给加载的页面，使用Promise异步回调。建议在UIAbility启动过程中调用该接口，重复调用将首先销毁旧的页面内容（即UIContent）再加载新页面内容，请谨慎使用。当前UI的执行上下文可能不明确，所以不建议在回调函数中做UI相关的操作。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名  | 类型                                            | 必填 | 说明                                                         |
| ------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| path    | string                                          | 是   | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main_pages.json文件中。 |
| storage | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | 否   | 页面级UI状态存储单元，这里用于为加载到窗口的页面内容传递状态属性。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Invalid path parameter.|
| 1300002 | This window state is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  storage: LocalStorage = new LocalStorage();

  onWindowStageCreate(windowStage: window.WindowStage) {
    this.storage.setOrCreate('storageSimpleProp', 121);
    console.info('onWindowStageCreate');
    try {
      let promise = windowStage.loadContent('pages/page2', this.storage);
      promise.then(() => {
        console.info('Succeeded in loading the content.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
    }
    ;
  }
};
```

## loadContent<sup>9+</sup>

loadContent(path: string, callback: AsyncCallback&lt;void&gt;): void

根据当前工程中指定的页面路径为WindowStage的主窗口加载具体页面内容，使用callback异步回调。建议在UIAbility启动过程中调用该接口，重复调用将首先销毁旧的页面内容（即UIContent）再加载新页面内容，请谨慎使用。当前UI的执行上下文可能不明确，所以不建议在回调函数中做UI相关的操作。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                      | 必填 | 说明                 |
| -------- | ------------------------- | ---- | -------------------- |
| path     | string                    | 是   | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main_pages.json文件中。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。           |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Invalid path parameter.|
| 1300002 | This window state is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      windowStage.loadContent('pages/page2', (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in loading the content.');
      });
    } catch (exception) {
      console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## loadContentByName<sup>11+</sup>

loadContentByName(name: string, storage: LocalStorage, callback: AsyncCallback&lt;void&gt;): void

根据指定路由页面名称为当前WindowStage加载[命名路由](../../ui/arkts-routing.md#命名路由)页面，通过LocalStorage传递状态属性至加载页面，使用callback异步回调。建议在UIAbility启动过程中使用该接口，重复调用该接口将先销毁旧的页面内容（即UIContent）再加载新的页面内容，请谨慎使用。当前UI的执行上下文可能不明确，所以不建议在回调函数中做UI相关的操作。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| name     | string                                                  | 是   | 命名路由页面的名称。                                             |
| storage  | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | 是   | 页面级UI状态存储单元，这里用于为加载到窗口的页面内容传递状态属性。 |
| callback | AsyncCallback&lt;void&gt;                               | 是   | 回调函数。                                                   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                                      |
| -------- | --------------------------------------------- |
| 401      | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 1300002  | This window state is abnormal.                |

**示例：**

<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import * as Index from '../pages/Index'; // 导入命名路由页面

export default class EntryAbility extends UIAbility {
  // ...

  storage: LocalStorage = new LocalStorage();

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    this.storage.setOrCreate('storageSimpleProp', 121);
    try {
      windowStage.loadContentByName(Index.entryName, this.storage, (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in loading the content.');
      });
    } catch (exception) {
      console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```
<!--code_no_check-->
```ts
// ets/pages/Index.ets
export const entryName : string = 'Index';
@Entry({routeName: entryName, useSharedStorage: true})
@Component
export struct Index {
  @State message: string = 'Hello World'
  @LocalStorageLink('storageSimpleProp') storageSimpleProp: number = 1;
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## loadContentByName<sup>11+</sup>

loadContentByName(name: string, callback: AsyncCallback&lt;void&gt;): void

根据指定路由页面名称为当前WindowStage加载[命名路由](../../ui/arkts-routing.md#命名路由)页面，使用callback异步回调。建议在UIAbility启动过程中使用该接口，重复调用该接口将先销毁旧的页面内容（即UIContent）再加载新的页面内容，请谨慎使用。当前UI的执行上下文可能不明确，所以不建议在回调函数中做UI相关的操作。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                      | 必填 | 说明             |
| -------- | ------------------------- | ---- | ---------------- |
| name     | string                    | 是   | 命名路由页面的名称。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。       |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                                      |
| -------- | --------------------------------------------- |
| 401      | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 1300002  | This window state is abnormal.                |

**示例：**

<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import * as Index from '../pages/Index'; // 导入命名路由页面

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      windowStage.loadContentByName(Index.entryName, (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in loading the content.');
      });
    } catch (exception) {
      console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```
<!--code_no_check-->
```ts
// ets/pages/Index.ets
export const entryName : string = 'Index';
@Entry({routeName: entryName})
@Component
export struct Index {
  @State message: string = 'Hello World'
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## loadContentByName<sup>11+</sup>

loadContentByName(name: string, storage?: LocalStorage): Promise&lt;void&gt;

根据指定路由页面名称为当前WindowStage加载[命名路由](../../ui/arkts-routing.md#命名路由)页面，通过LocalStorage传递状态属性至加载页面，使用promise异步回调。建议在UIAbility启动过程中使用该接口，重复调用该接口将先销毁旧的页面内容（即UIContent）再加载新的页面内容，请谨慎使用。当前UI的执行上下文可能不明确，所以不建议在回调函数中做UI相关的操作。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名  | 类型         | 必填 | 说明                                                         |
| ------- | ------------ | ---- | ------------------------------------------------------------ |
| name    | string       | 是   | 命名路由页面的名称。                                             |
| storage | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | 否   | 页面级UI状态存储单元，这里用于为加载到窗口的页面内容传递状态属性。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                                      |
| -------- | --------------------------------------------- |
| 401      | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 1300002  | This window state is abnormal.                |

**示例：**

<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import * as Index from '../pages/Index'; // 导入命名路由页面

export default class EntryAbility extends UIAbility {
  // ...

  storage: LocalStorage = new LocalStorage();

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    this.storage.setOrCreate('storageSimpleProp', 121);
    try {
      let promise = windowStage.loadContentByName(Index.entryName, this.storage);
      promise.then(() => {
        console.info('Succeeded in loading the content.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```
<!--code_no_check-->
```ts
// ets/pages/Index.ets
export const entryName : string = 'Index';
@Entry({routeName: entryName, useSharedStorage: true})
@Component
export struct Index {
  @State message: string = 'Hello World'
  @LocalStorageLink('storageSimpleProp') storageSimpleProp: number = 1;
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## on('windowStageEvent')<sup>9+</sup>

on(eventType: 'windowStageEvent', callback: Callback&lt;WindowStageEventType&gt;): void

开启WindowStage生命周期变化的监听。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| eventType  | string                                                       | 是   | 监听事件，固定为'windowStageEvent'，即WindowStage生命周期变化事件。 |
| callback | Callback&lt;[WindowStageEventType](arkts-apis-window-e.md#windowstageeventtype9)&gt; | 是   | 回调函数。返回当前的WindowStage生命周期状态。                |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      windowStage.on('windowStageEvent', (data) => {
        console.info('Succeeded in enabling the listener for window stage event changes. Data: ' +
        JSON.stringify(data));
      });
    } catch (exception) {
      console.error(`Failed to enable the listener for window stage event changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## off('windowStageEvent')<sup>9+</sup>

off(eventType: 'windowStageEvent', callback?: Callback&lt;WindowStageEventType&gt;): void

关闭WindowStage生命周期变化的监听。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| eventType  | string                                                       | 是   | 监听事件，固定为'windowStageEvent'，即WindowStage生命周期变化事件。 |
| callback | Callback&lt;[WindowStageEventType](arkts-apis-window-e.md#windowstageeventtype9)&gt; | 否   | 回调函数。返回当前的WindowStage生命周期状态。若传入参数，则关闭该监听。若未传入参数，则关闭所有WindowStage生命周期变化的监听。                |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    const callback = (windowStageEventType: window.WindowStageEventType) => {
      // ...
    }
    try {
      windowStage.on('windowStageEvent', callback);
    } catch (exception) {
      console.error(`Failed to enable the listener for window stage event changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
    try {
      windowStage.off('windowStageEvent', callback);
      // 如果通过on开启多个callback进行监听，同时关闭所有监听：
      windowStage.off('windowStageEvent');
    } catch (exception) {
      console.error(`Failed to disable the listener for window stage event changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## on('windowStageLifecycleEvent')<sup>20+</sup>

on(eventType: 'windowStageLifecycleEvent', callback: Callback&lt;WindowStageLifecycleEventType&gt;): void

开启WindowStage生命周期变化的监听。

> **说明：**
>
>  [on('windowStageEvent')](#onwindowstageevent9)与本接口的区别：
>
> 1.前者无法保证状态切换间的顺序，对于状态间的顺序有要求的情况下不推荐使用，推荐使用本接口；
>
> 2.当前接口不提供WindowStage的获焦失焦状态监听，对于windowStage获焦失焦状态有监听需求的情况下，推荐使用[on('windowEvent')](arkts-apis-window-Window.md#onwindowevent10)；
>
> 3.其他系统机制及其生命周期状态切换的详细说明，请参考[主窗口的生命周期](../../windowmanager/window-overview.md#主窗口的生命周期)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| eventType  | string                                                       | 是   | 监听事件，固定为'windowStageLifecycleEvent'，即WindowStage生命周期变化事件。 |
| callback | Callback&lt;[WindowStageLifecycleEventType](arkts-apis-window-e.md#windowstagelifecycleeventtype20)&gt; | 是   | 回调函数。返回当前的WindowStage生命周期状态。                |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    const callback = (data: window.WindowStageLifecycleEventType) => {
      console.info('Succeeded in enabling the listener for window stage event changes. Data: ' +
        JSON.stringify(data));
      // 根据事件状态类型选择进行具体的处理
      if (data === window.WindowStageLifecycleEventType.SHOWN) {
        console.info('current window stage event is SHOWN');
        // ...
      } else if (data === window.WindowStageLifecycleEventType.RESUMED) {
        console.info('current window stage event is RESUMED');
        // ...
      } else if (data === window.WindowStageLifecycleEventType.PAUSED) {
        console.info('current window stage event is PAUSED');
        // ...
      } else if (data === window.WindowStageLifecycleEventType.HIDDEN) {
        console.info('current window stage event is HIDDEN');
        // ...
      }
      // ...
    }
    try {
      windowStage.on('windowStageLifecycleEvent', callback);
    } catch (exception) {
      console.error(`Failed to enable the listener for window stage event changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## off('windowStageLifecycleEvent')<sup>20+</sup>

off(eventType: 'windowStageLifecycleEvent', callback?: Callback&lt;WindowStageLifecycleEventType&gt;): void

关闭WindowStage生命周期变化的监听。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| eventType  | string                                                       | 是   | 监听事件，固定为'windowStageLifecycleEvent'，即WindowStage生命周期变化事件。 |
| callback | Callback&lt;[WindowStageLifecycleEventType](arkts-apis-window-e.md#windowstagelifecycleeventtype20)&gt; | 否   | 回调函数。返回当前的WindowStage生命周期状态。若传入参数，则关闭该监听。若未传入参数，则关闭所有WindowStage生命周期变化的监听。                |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    const callback = (windowStageLifecycleEvent: window.WindowStageLifecycleEventType) => {
      // ...
    }
    try {
      windowStage.on('windowStageLifecycleEvent', callback);
    } catch (exception) {
      console.error(`Failed to enable the listener for window stage event changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
    try {
      windowStage.off('windowStageLifecycleEvent', callback);
      // 如果通过on开启多个callback进行监听，同时关闭所有监听：
      windowStage.off('windowStageLifecycleEvent');
    } catch (exception) {
      console.error(`Failed to disable the listener for window stage event changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## on('windowStageClose')<sup>14+</sup>

on(eventType: 'windowStageClose', callback: Callback&lt;void&gt;): void

该接口仅在[自由窗口](../../windowmanager/window-terminology.md#自由窗口)状态下生效，用于开启点击主窗三键区的关闭按钮监听事件。点击主窗口的三键区域的关闭键时触发该回调函数，将不执行注册的[UIAbility.onPrepareToTerminate](../apis-ability-kit/js-apis-app-ability-uiAbility.md#onpreparetoterminate10)生命周期回调函数。

当重复注册窗口关闭事件的监听时，最后一次注册成功的监听事件生效。

触发的回调函数是同步执行，主窗口的异步关闭事件监听参考[on('windowWillClose')](arkts-apis-window-Window.md#onwindowwillclose15)方法。

如果存在[on('windowWillClose')](arkts-apis-window-Window.md#onwindowwillclose15)监听事件，只响应[on('windowWillClose')](arkts-apis-window-Window.md#onwindowwillclose15)接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**设备行为差异：** 该接口在2in1设备、Tablet设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| eventType  | string                                                       | 是   | 监听事件，固定为'windowStageClose'，即开启主窗三键区的关闭按钮监听。|
| callback | Callback&lt;void&gt; | 是   | 回调函数。当点击主窗口右上角关闭按钮事件发生时的回调。该回调函数不返回任何参数。回调函数内部逻辑需要有boolean类型的返回值，该返回值决定当前主窗是否继续关闭，true表示不关闭，false表示关闭。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      windowStage.on('windowStageClose', () => {
        console.info('Succeeded in enabling the listener for window stage close event.');
        return false;
      });
    } catch (exception) {
      console.error(`Failed to enable the listener for window stage close event. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## off('windowStageClose')<sup>14+</sup>

off(eventType: 'windowStageClose', callback?: Callback&lt;void&gt;): void

该接口仅在[自由窗口](../../windowmanager/window-terminology.md#自由窗口)状态下生效，用于关闭主窗口关闭事件的监听。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**设备行为差异：** 该接口在2in1设备、Tablet设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| eventType  | string                                                       | 是   | 监听事件，固定为'windowStageClose'，即关闭主窗口关闭事件的监听。 |
| callback | Callback&lt;void&gt; | 否   | 回调函数。当点击主窗口右上角关闭按钮事件发生时的回调。该回调函数不返回任何参数。回调函数内部逻辑需要有boolean类型的返回值，该返回值决定当前主窗是否继续关闭，true表示不关闭，false表示关闭。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有主窗口关闭的监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    const callback = () => {
      // ...
      return false;
    }
    try {
      windowStage.on('windowStageClose', callback);
      windowStage.off('windowStageClose', callback);
      windowStage.off('windowStageClose');
    } catch (exception) {
      console.error(`Failed to disable the listener for window stage close changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## setDefaultDensityEnabled<sup>12+</sup>

setDefaultDensityEnabled(enabled: boolean): void

设置应用主窗口是否使用系统默认Density，子窗和系统窗口会跟随主窗生效。调用此接口前，需先调用[WindowStage.loadContent()](#loadcontent9)初始化布局，确保接口调用时序正确。

不调用此接口进行设置，则表示不使用系统默认Density。

不使用系统默认Density时，若调用过[setCustomDensity()](#setcustomdensity15)，则窗口会跟随用户自定义的显示大小变化重新布局，否则跟随系统显示大小变化重新布局。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名           | 类型    | 必填 | 说明                         |
| ---------------- | ------- | ---- | ---------------------------- |
| enabled | boolean | 是   | 是否设置应用使用系统默认Density。true表示使用系统默认Density，窗口不跟随系统显示大小变化重新布局；false表示不使用系统默认Density，窗口跟随系统显示大小变化重新布局。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit'

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
      windowStage.loadContent("pages/page2", (err: BusinessError) => {
        let errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('onWindowStageCreate');
      try {
        windowStage.setDefaultDensityEnabled(true);
        console.info('Succeeded in loading the content.');
      } catch (exception) {
        console.error(`Failed to set default density enabled. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
};
```

## setCustomDensity<sup>15+</sup>

setCustomDensity(density: number): void

支持应用主窗口自定义其显示大小缩放系数。

已创建的子窗和系统窗口不会立即跟随主窗的customDensity变化重新布局，而是在子窗或系统窗口下一次位置、大小、系统缩放大小等窗口布局信息变化时跟随主窗的customDensity变化重新布局。

当存在同时使用该接口和[setDefaultDensityEnabled(true)](#setdefaultdensityenabled12)的情况时，以最后调用的设置效果为准。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名           | 类型    | 必填 | 说明                         |
| ---------------- | ------- | ---- | ---------------------------- |
| density | number | 是   | 自定义显示大小缩放系数。该参数为浮点数，取值范围为[0.5, 4.0]或-1.0。4.0表示窗口可显示的最大显示大小缩放系数，-1.0表示窗口使用系统显示大小缩放系数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      windowStage.setCustomDensity(-1.0);
    } catch (exception) {
      console.error(`Failed to set custom density. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## setCustomDensity<sup>20+</sup>

setCustomDensity(density: number, applyToSubWindow?: boolean): void

支持应用主窗口自定义显示大小缩放系数，并设置已创建的子窗和系统窗口跟随主窗重新布局的生效时机。

当存在同时使用该接口和[setDefaultDensityEnabled(true)](#setdefaultdensityenabled12)的情况时，以最后调用的设置效果为准。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名           | 类型    | 必填 | 说明                         |
| ---------------- | ------- | ---- | ---------------------------- |
| density | number | 是   | 自定义显示大小缩放系数。该参数为浮点数，取值范围为[0.5, 4.0]或-1.0。4.0表示窗口可显示的最大显示大小缩放系数，-1.0表示窗口使用系统显示大小缩放系数。 |
| applyToSubWindow | boolean | 否   | 设置当前已创建的子窗和系统窗口是否跟随立即跟随主窗口更新customDensity并重新布局。设置为true时，表示立即跟随主窗生效；设置为false时，表示不会立即跟随主窗生效，而是在子窗或系统窗口下一次位置、大小、系统缩放大小等窗口布局信息变化时跟随主窗的customDensity变化重新布局。默认值为false。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      windowStage.setCustomDensity(2.0);
      windowStage.setCustomDensity(3.0, true);
      windowStage.setCustomDensity(-1.0, false);
    } catch (exception) {
      console.error(`Failed to set custom density. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};
```

## setWindowModal<sup>14+</sup>

setWindowModal(isModal: boolean): Promise&lt;void&gt;

该接口仅在[自由窗口](../../windowmanager/window-terminology.md#自由窗口)状态下生效，用于设置主窗的模态属性是否启用，使用Promise异步回调。

主窗口调用该接口时，设置主窗口模态属性是否启用。启用主窗口模态属性后，其相同应用进程下的其他主窗口以及其他主窗口的子窗口不能响应用户操作，直到该主窗口关闭或者主窗口的模态属性被禁用。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**设备行为差异：** 该接口在2in1设备、Tablet设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数名    | 类型    | 必填 | 说明                                          |
| --------- | ------- | ---- | --------------------------------------------- |
| isModal | boolean | 是   | 设置主窗口模态属性是否启用，true为启用，false为不启用。 |


**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002  | This window state is abnormal. |
| 1300003  | This window manager service works abnormally. |
| 1300005 | This window stage is abnormal. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    try {
      let promise = windowStage.setWindowModal(true);
      promise.then(() => {
        console.info('Succeeded in setting window modal');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set window modal. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set window modal. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## removeStartingWindow<sup>14+</sup>

removeStartingWindow(): Promise&lt;void&gt;

支持应用控制启动页消失时机。

此接口只对应用主窗口生效，且需要在module.json5配置文件[abilities](../../quick-start/module-configuration-file.md#abilities标签)标签中的metadata标签下配置"enable.remove.starting.window"为"true"才会生效。

在标签配置为"true"的情况下，系统提供了启动页超时保护机制，若5s内未调用此接口，系统将自动移除启动页。

若标签配置为"false"或未配置标签，则此接口不生效，启动页将会在应用首帧渲染完成后自动移除。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300003 | This window manager service works abnormally. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    windowStage.removeStartingWindow().then(() => {
      console.info('Succeeded in removing starting window.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to remove starting window. Cause code: ${err.code}, message: ${err.message}`);
    });
  }
};
```

## setWindowRectAutoSave<sup>14+</sup>

setWindowRectAutoSave(enabled: boolean): Promise&lt;void&gt;

设置是否启用最后关闭的主窗尺寸的记忆功能，使用Promise异步回调。

启用记忆功能后，在同一个UIAbility下，记忆最后关闭的主窗口的尺寸；此主窗口再次启动时，以记忆的尺寸按照规则进行打开。

层叠规则: 1、当前实例是自由窗口时，打开下一实例窗口层叠时，大小要跟随。2、当前实例是最大化或全屏窗口时，打开下一个实例窗口层叠时，保持最大化。

记忆规则：
|上一次窗口状态|记忆规则|
|-------------|-------|
|自由窗口|保留自由窗口的大小/位置，超出工作区回弹|
|二分屏窗口|保留二分屏之前自由窗口的大小/位置|
|最大化窗口|保留最大化|
|沉浸式窗口|保留沉浸式之前自由窗口的大小/位置|
|最小化窗口|保留最小化之前自由窗口的大小/位置|

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**设备行为差异：** 该接口在2in1设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数名    | 类型    | 必填 | 说明                                          |
| --------- | ------- | ---- | --------------------------------------------- |
| enabled | boolean | 是   | 设置是否启用主窗尺寸的记忆功能，true为启用，false为不启用。 |


**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002  | This window state is abnormal. |
| 1300003  | This window manager service works abnormally. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    try {
      let promise = windowStage.setWindowRectAutoSave(true);
      promise.then(() => {
        console.info('Succeeded in setting window rect auto-save');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set window rect auto-save. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set window rect auto-save. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setWindowRectAutoSave<sup>17+</sup>

setWindowRectAutoSave(enabled: boolean, isSaveBySpecifiedFlag: boolean): Promise&lt;void&gt;

设置是否启用主窗的尺寸记忆功能，使用Promise异步回调。

在同一个UIAbility下，可记忆最后关闭的主窗口尺寸，也可针对每个主窗口尺寸单独进行记忆。只有在UIAbility启动模式为specified，且isSaveBySpecifiedFlag设置为true时，才能针对每个主窗口尺寸进行单独记忆。

启用记忆功能后，记忆主窗口关闭时的尺寸；对应主窗口再次启动时，以记忆的尺寸按照规则进行打开。

记忆规则：
|上一次窗口状态|记忆规则|
|-------------|-------|
|自由窗口|保留自由窗口的大小/位置，超出工作区回弹。|
|二分屏窗口|保留二分屏之前自由窗口的大小/位置。|
|最大化窗口|保留最大化。|
|沉浸式窗口|保留沉浸式之前自由窗口的大小/位置。|
|最小化窗口|保留最小化之前自由窗口的大小/位置。|

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**设备行为差异：** 该接口在2in1设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数名    | 类型    | 必填 | 说明                                          |
| --------- | ------- | ---- | --------------------------------------------- |
| enabled | boolean | 是   | 设置是否启用主窗的尺寸记忆功能，true为启用，false为不启用。 |
| isSaveBySpecifiedFlag | boolean | 是   | 设置specified模式下是否启用对窗口进行单独记忆，true为启用，false为不启用。 |


**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | Capability not supported. Function setWindowRectAutoSave can not work correctly due to limited device capabilities. |
| 1300002  | This window state is abnormal. |
| 1300003  | This window manager service works abnormally. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    try {
      let promise = windowStage.setWindowRectAutoSave(true, true);
      promise.then(() => {
        console.info('Succeeded in setting window rect auto-save');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set window rect auto-save. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set window rect auto-save. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## isWindowRectAutoSave<sup>14+</sup>

isWindowRectAutoSave(): Promise&lt;boolean&gt;

判断当前主窗口是否已经启用尺寸记忆，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**设备行为差异：** 该接口在2in1设备中可正常调用，在其他设备中返回801错误码。

**返回值：**

| 类型 | 说明 |
| ---------------------- | ------------------------------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前窗口启用尺寸记忆，返回false表示当前窗口禁用尺寸记忆。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
| ------- | ------------------------------ |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |
| 1300003 | This window manager service works abnormally. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    try {
      let promise = windowStage.isWindowRectAutoSave();
      promise.then((data) => {
        console.info(`Succeeded in checking whether the window support the rect auto-save. Data: ${data}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to check whether the window support the rect auto-save. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to check whether the window support the rect auto-save. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setSupportedWindowModes<sup>15+</sup>

setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>): Promise&lt;void&gt;

该接口仅在[自由窗口](../../windowmanager/window-terminology.md#自由窗口)状态下生效，用于设置主窗的窗口支持模式，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Window.SessionManager

**设备行为差异：** 该接口在2in1设备、Tablet设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数名    | 类型    | 必填 | 说明                                          |
| --------- | ------- | ---- | --------------------------------------------- |
| supportedWindowModes | Array&lt;[bundleManager.SupportWindowMode](../apis-ability-kit/js-apis-bundleManager.md#supportwindowmode)&gt; | 是   | 设置主窗的窗口支持模式。<br>- FULL_SCREEN：支持全屏模式。<br>- FLOATING：支持悬浮窗模式。<br>- SPLIT：支持分屏模式。需要配合FULL_SCREEN或FLOATING一起使用，不支持仅配置SPLIT。<br> 注：数组中SupportWindowMode字段取值不应该与该UIAbility对应的[module.json5配置文件](../../quick-start/module-configuration-file.md)中[abilities标签](../../quick-start/module-configuration-file.md#abilities标签)的supportWindowMode字段取值或者[StartOptions](../apis-ability-kit/js-apis-app-ability-startOptions.md)中[属性](../apis-ability-kit/js-apis-app-ability-startOptions.md#startoptions)的supportWindowModes字段取值冲突。当取值冲突时，最终以该参数设置的窗口支持模式为准。|

**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002  | This window state is abnormal. |
| 1300003  | This window manager service works abnormally. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    try {
      let promise = windowStage.setSupportedWindowModes([
        bundleManager.SupportWindowMode.FULL_SCREEN,
        bundleManager.SupportWindowMode.SPLIT,
        bundleManager.SupportWindowMode.FLOATING
      ]);
      promise.then(() => {
        console.info('Succeeded in setting window support modes');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set window support modes. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set window support modes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setSupportedWindowModes<sup>20+</sup>

setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>, grayOutMaximizeButton: boolean): Promise&lt;void&gt;

该接口仅在[自由窗口](../../windowmanager/window-terminology.md#自由窗口)状态下生效，用于设置主窗的窗口支持模式，并提供最大化按钮置灰功能，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**设备行为差异：** 该接口在2in1设备、Tablet设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数名    | 类型    | 必填 | 说明                                          |
| --------- | ------- | ---- | --------------------------------------------- |
| supportedWindowModes | Array&lt;[bundleManager.SupportWindowMode](../apis-ability-kit/js-apis-bundleManager.md#supportwindowmode)&gt; | 是   | 设置主窗的窗口支持模式。<br>- FULL_SCREEN：支持全屏模式。<br>- FLOATING：支持悬浮窗模式。<br>- SPLIT：支持分屏模式。需要配合FULL_SCREEN或FLOATING一起使用，不支持仅配置SPLIT。<br> 注：数组中SupportWindowMode字段取值不应该与该UIAbility对应的[module.json5配置文件](../../quick-start/module-configuration-file.md)中[abilities标签](../../quick-start/module-configuration-file.md#abilities标签)的supportWindowMode字段取值或者[StartOptions](../apis-ability-kit/js-apis-app-ability-startOptions.md#startoptions)中属性的supportWindowModes字段取值冲突。当取值冲突时，最终以该参数设置的窗口支持模式为准。|
| grayOutMaximizeButton | boolean | 是 | 是否显示并将主窗口的最大化按钮置灰。true表示显示并将主窗口的最大化按钮置灰，此时最大化按钮不可用；false表示不显示主窗口的最大化按钮。此参数配置仅在supportedWindowModes不支持FULL_SCREEN时生效。 |

**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 801      | Capability not supported. Function setSupportedWindowModes can not work correctly due to limited device capabilities. |
| 1300002  | This window state is abnormal. |
| 1300003  | This window manager service works abnormally. |
| 1300016  | Parameter error. Possible cause: 1. Invalid parameter range. 2. Invalid parameter length. 3. Incorrect parameter format. |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    try {
      let promise = windowStage.setSupportedWindowModes([
        bundleManager.SupportWindowMode.FULL_SCREEN,
        bundleManager.SupportWindowMode.SPLIT,
        bundleManager.SupportWindowMode.FLOATING
      ], true);
      promise.then(() => {
        console.info('Succeeded in setting window support modes');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set window support modes. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set window support modes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```