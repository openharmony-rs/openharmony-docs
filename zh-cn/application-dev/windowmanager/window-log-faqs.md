## 1300012 画中画窗口状态异常

错误码1300012表示画中画窗口状态异常。

### 可能原因

- 画中画窗口已被销毁，但代码仍在尝试访问该窗口。

- 画中画窗口处于无效状态（如尚未创建、已关闭、正在销毁）。

- 在画中画窗口销毁后，异步任务或回调中访问了窗口对象。

- 画中画窗口已经启动或正在启动中，但代码仍在尝试重复启动画中画窗口。

### 画中画窗口销毁后访问导致崩溃

开发者在画中画窗口销毁后（如用户退出画中画、窗口生命周期结束等）调用画中画窗口相关接口（`stopPiP`），触发错误码1300012。

**典型日志信息**

```text
Error Name: Error
Error Message: [PiPWindow][stopPiP]msg: The window is not created or destroyed.
Error code: 1300012
```

**分析定位及解决**

- 是否在画中画生命周期状态为`ABOUT_TO_STOP`或`STOPPED`时调用`stopPiP`接口。

    答：在该状态时，代表画中画窗口即将停止或已经停止，此时不可调用`stopPiP`接口。

- 是否在`setTimeout`、`Promise`等异步回调中调用`stopPiP`，且回调执行时窗口可能已销毁。

    答：在异步回调函数中，可能会存在画中画窗口已经被销毁，但未获取其状态，调用`stopPiP`接口会导致错误。

**正反案例**

错误示例

```ts
stopPiPTimer() {
    setTimeout(() => {
        this.pipController.stopPiP();
    }, 1000);
}
```

正确示例
```ts
async function stopPiPSafely(pipController: PiPController) {
  let state: string = 'undefined';
  
  pipController.on('stateChange', (newState: string, reason: string) => {
    state = newState;
    if (state === 'STARTED') {
      pipController.stopPiP();
    }
  });
}
```

### 画中画窗口重复启动导致崩溃

开发者在画中画窗口处于已经启动或正在启动中的状态时，调用画中画窗口相关接口（`startPiP`），触发错误码1300012。

**典型日志信息**

```text
Error Name: Error
Error Message: [PiPWindow][startPiP]msg: The window is already started or is about to start.
Error code: 1300012
```

**分析定位及解决**

- 是否在画中画生命周期状态为`ABOUT_TO_START`或`STARTED`时调用`startPiP`接口。

    答：在该状态时，代表画中画窗口即将启动或已经启动，此时不可调用`startPiP`接口。

- 是否在`setTimeout`、`Promise`等异步回调中调用`startPiP`，且回调执行时窗口可能已启动。

    答：在异步回调函数中，可能会存在画中画窗口已经启动或正在启动中，但未获取其状态，调用`startPiP`接口会导致错误。

**正反案例**

错误示例

```ts
startPiPTimer() {
    setTimeout(() => {
        this.pipController.startPiP();
    }, 1000);
}
```

正确示例
```ts
async function startPiPSafely(pipController: PiPController) {
  let state: string = 'undefined';
  
  pipController.on('stateChange', (newState: string, reason: string) => {
    state = newState;
    if (state === 'STOPPED') {
      pipController.startPiP();
    }
  });
}
```