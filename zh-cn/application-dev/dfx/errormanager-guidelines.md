# 错误管理开发指导

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @rr_cn-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 场景介绍

当应用的代码存在规范问题或错误时，会在运行中产生异常和错误，如应用未捕获异常等。在错误产生后，应用会异常退出。错误日志通常会保存在用户本地存储设备中，不方便开发者定位问题。所以，应用开发者可以使用错误管理的接口，在应用退出前，及时将相关错误及日志上报到开发者的服务平台来定位问题。

使用errorManager接口监听异常和错误后，应用不会退出，建议在回调函数执行完后，增加同步退出操作，如果只是为了获取错误日志，建议使用[HiAppEvent订阅事件](hiappevent-intro.md)。

## 接口说明

应用错误管理接口由[@ohos.app.ability.errorManager (错误管理模块)](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md)提供，使用接口能力前需注册错误观测器，开发者可以通过import引入，详见[开发示例](#开发示例)。

**错误管理接口功能介绍**：

| 接口名称 | 说明 |
| -------- | -------- |
| on(type: "error", observer: ErrorObserver): number | 注册错误监听接口，当系统监测到应用异常时会回调该监听。该接口为同步接口，返回值为注册的监听对象对应的序号。 |
| off(type: "error", observerId: number, callback: AsyncCallback&lt;void>): void | 以callback的形式解除注册监听，传入的number为之前注册监听时返回的序号。 |
| off(type: "error", observerId: number): Promise&lt;void> | 以Promise的形式解除注册监听，传入的number为之前注册监听时返回的序号。 |
| on(type: 'globalErrorOccurred', observer: GlobalObserver): void | 注册进程错误监听接口，当系统监测到应用异常时会回调该监听，该接口为同步接口，即一次注册，全局监听。（**推荐使用**）<br/>说明：从API version 18开始，支持该接口。 |
| off(type: 'globalErrorOccurred', observer?: GlobalObserver): void | 以callback的形式解除注册监听。（**推荐使用**）<br/>说明：从API version 18开始，支持该接口。 |
| on(type: 'globalUnhandledRejectionDetected', observer: GlobalObserver): void | 注册进程错误监听接口，当系统监测到应用promise异常时会回调该监听，该接口为同步接口，即一次注册，全局监听。（**推荐使用**）<br/>说明：从API version 18开始，支持该接口。 |
| off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void | 以callback的形式解除注册监听。（**推荐使用**）<br/>说明：从API version 18开始，支持该接口。 |
| on(type: 'loopObserver', timeout: number, observer: LoopObserver): void | 注册主线程消息处理耗时监听器，当系统监测到应用主线程事件处理超时时会回调该监听。<br/>只能在主线程调用，多次注册后，后一次的注册会覆盖前一次的。 |
| off(type: 'loopObserver', observer?: LoopObserver): void | 以LoopObserver的形式解除应用主线程消息处理耗时监听。 |
| on(type: 'freeze', observer: FreezeObserver): void | 注册应用主线程freeze监听。只能在主线程调用，重复注册后，后一次的注册会覆盖前一次的。 |
| off(type: 'freeze', observer?: FreezeObserver): void | 以FreezeObserver的形式解除应用主线程消息处理耗时监听。<br/>说明：从API version 18开始，支持该接口。 |
| setDefaultErrorHandler(defaultHandler?: ErrorHandler): ErrorHandler | 仅允许在主线程调用，发生JS_CRASH异常时，支持链式回调，返回值为上一次注册的处理器。 <br/>说明：从API version 21开始，支持该接口。 |
当采用callback作为异步回调时，可以在callback中进行下一步处理。
当采用Promise对象返回时，可以在Promise对象中类似地处理接口返回值，具体结果码说明见[解除注册结果码](#解除注册结果码)。

**错误监听(ErrorObserver)接口功能介绍**：

| 接口名称 | 说明 |
| -------- | -------- |
| onUnhandledException(errMsg: string): void | 系统回调接口，应用注册后，当应用产生未捕获的异常时的回调。 |
| onException?(errObject: Error): void | 系统回调接口，应用注册后，当应用产生异常上报js层时的回调。 |

**应用主线程监听(LoopObserver)接口功能介绍**：

| 接口名称 | 说明 |
| -------- | -------- |
| onLoopTimeOut?(timeout: number): void | 系统回调接口，应用注册后，当应用主线程处理事件超时的回调。 |

### 解除注册结果码

| 结果码 | 原因 |
| -------- | -------- |
| 0 | 正常返回 |
| -1 | 传入的number参数不存在 |
| -2 | 参数错误 |

## 开发示例

> **注意：**
>
> 建议在异常回调函数处理的最后，增加同步退出操作，以避免多次异常回调。

### 单线程监听场景

 引入头文件。
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 新增监听回调函数。
<!-- @[error_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    hilog.info(0x0000, 'testTag','onUnhandledException, errorMsg: ', errorMsg);
  },
  onException(errorObj) {
    hilog.info(0x0000, 'testTag','onException, name: ', errorObj.name);
    hilog.info(0x0000, 'testTag','onException, message: ', errorObj.message);
    if (typeof(errorObj.stack) === 'string') {
      hilog.info(0x0000, 'testTag','onException, stack: ', errorObj.stack);
    }
  }
};
```

 新增触发按钮。
<!-- @[onclick_error_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('单线程监听场景').onClick(()=>{
  let observerId = -1;
  try {
    observerId = errorManager.on('error', observer);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:50});
```


### 进程监听异常场景

 引入头文件。
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 新增监听回调函数。
<!-- @[error_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function errorFunc(observer: errorManager.GlobalError) {
  hilog.info(0x0000, 'testTag','result name :' + observer.name);
  hilog.info(0x0000, 'testTag','result message :' + observer.message);
  hilog.info(0x0000, 'testTag','result stack :' + observer.stack);
  hilog.info(0x0000, 'testTag','result instanceName :' + observer.instanceName);
  hilog.info(0x0000, 'testTag','result instanceType :' + observer.instanceType);
};
```

 新增触发按钮。
<!-- @[onclick_error_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('进程监听异常场景').onClick(()=>{
  try {
    errorManager.on('globalErrorOccurred', errorFunc);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:100});
```

### 进程监听promise异常场景

 引入头文件。
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 新增监听回调函数。
<!-- @[promise_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function promiseFunc(observer: errorManager.GlobalError) {
  hilog.info(0x0000, 'testTag','result name :' + observer.name);
  hilog.info(0x0000, 'testTag','result message :' + observer.message);
  hilog.info(0x0000, 'testTag','result stack :' + observer.stack);
  hilog.info(0x0000, 'testTag','result instanceName :' + observer.instanceName);
  hilog.info(0x0000, 'testTag','result instanceType :' + observer.instanceType);
}
```

 新增触发按钮。
<!-- @[onclick_promise_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('进程监听promise异常场景').onClick(()=>{
  try {
    errorManager.on('globalUnhandledRejectionDetected', promiseFunc);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:200});
```

### 主线程监听freeze

 引入头文件。
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 新增监听回调函数。
<!-- @[freeze_call_back](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function freezeCallback() {
  hilog.info(0x0000, 'testTag','freezecallback');
}
```

 新增触发按钮。
<!-- @[onclick_freeze_call_back](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('主线程监听freeze').onClick(()=>{
  try {
    errorManager.on('freeze', freezeCallback);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:300});
```

### 主线程监听消息处理耗时

 引入头文件。
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 新增监听回调函数。
<!-- @[loop_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let loopObserver: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    hilog.info(0x0000, 'testTag','Duration timeout: ' + timeout);
  }
};
```

 新增触发按钮。
<!-- @[onclick_loop_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('主线程监听消息处理耗时').onClick(()=>{
  try {
    errorManager.on('loopObserver', 1, loopObserver);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:150});
```

### 进程promise监听注册被拒绝

 引入头文件。
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 新增监听回调函数。
<!-- @[unhandled_rejection_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error('uncaught error');
});

let unhandledrejectionObserver: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    hilog.info(0x0000, 'testTag','promise1 is rejected');
  }
  hilog.info(0x0000, 'testTag','reason.name: ', reason.name);
  hilog.info(0x0000, 'testTag','reason.message: ', reason.message);
  if (reason.stack) {
    hilog.info(0x0000, 'testTag','reason.stack: ', reason.stack);
  }
};
```

 新增触发按钮。
<!-- @[onclick_unhandled_rejection_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('进程promise监听注册被拒绝').onClick(()=>{
  try {
    errorManager.on('unhandledRejection', unhandledrejectionObserver);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:250});
```

### 错误处理器责任链模式场景

以下示例文件均位于同一目录。

定义第一个错误处理器及注册方法，无前置处理器时退出进程:
```ts
// firstErrorHandler.ets
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let firstHandler: errorManager.ErrorHandler;
const firstErrorHandler: errorManager.ErrorHandler = (reason: Error) => {
    // 自定义的第一个errorHandler实现逻辑
    console.info('[FirstHandler] First uncaught exception handler invoked.');
    if (firstHandler) {
        firstHandler(reason);
    } else {
        // 建议增加判空操作，如果为空采用同步退出方式
        const processManager = new process.ProcessManager();
        processManager.exit(0);
    }  
};

export function setFirstErrorHandler() {
    firstHandler = errorManager.setDefaultErrorHandler(firstErrorHandler); 
    console.info('Registered First Error Handler');
}
```

定义第二个错误处理器及注册方法，形成链式调用:
```ts
// secondErrorHandler.ets
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let secondHandler: errorManager.ErrorHandler;
const secondErrorHandler: errorManager.ErrorHandler = (reason: Error) => {
    // 自定义的第二个errorHandler实现逻辑
    console.info('[SecondHandler] Second uncaught exception handler invoked.');
    if (secondHandler) {
        secondHandler(reason);
    } else {
        const processManager = new process.ProcessManager();
        processManager.exit(0);
    }
};

export function setSecondErrorHandler() {
    secondHandler = errorManager.setDefaultErrorHandler(secondErrorHandler); 
    console.info('Registered Second Error Handler');
}
```

主组件通过按钮触发测试，注册两个处理器并抛错验证处理链:
```ts
// Index.ets
import { setFirstErrorHandler } from './firstErrorHandler';
import { setSecondErrorHandler } from './secondErrorHandler';

@Entry
@Component
// 注册两个错误处理器，抛出错误以验证链式调用
struct ErrorHandlerTest {
    private testErrorHandlers() {
      setFirstErrorHandler();
      setSecondErrorHandler();
      throw new Error('Test uncaught exception!');
    }

    build() {
      Column() {
        Button('Test Handler Chain')
          .width('90%') 
          .height(48)
          .margin(16)
          .onClick(() => this.testErrorHandlers())
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center) 
    }
}

```
