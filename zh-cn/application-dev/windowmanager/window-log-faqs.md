## 1300012 画中画窗口状态异常

错误码1300012表示画中画窗口状态异常。

### 可能原因

- 画中画窗口已被销毁，但代码仍在尝试访问该窗口
- 画中画窗口处于无效状态（如尚未创建、已关闭、正在销毁）
- 在画中画窗口销毁后，异步任务或回调中访问了窗口对象

### 画中画窗口销毁后访问导致崩溃

开发者在画中画窗口销毁后（如用户退出画中画、窗口生命周期结束等）调用画中画窗口相关接口（如`startPiP`、`stopPiP`），触发错误码 1300012。

**典型日志信息**

```text
Error Name: Error
Error Message: [PiPWindow][stopPiP]msg: The window is not created or destroyed.
Error code: 1300012
```

**分析定位及解决**

1. 是否在画中画生命周期状态变化的监听函数回调状态为`ABOUT_TO_STOP`或`STOPPED`。

- 答：在该状态时，代表画中画窗口即将停止或已经停止，此时不可调用`stopPiP`接口。

2. 是否在`aboutToDisappear`生命周期方法中。

- 答: 在该生命周期时，代表画中画窗口即将被销毁，此时调用`stopPiP`接口可能会导致错误。

3. 是否在`setTimeout`、`Promise`等异步回调中，且回调执行时窗口可能已销毁。

- 答：在异步回调函数中，可能会存在画中画窗口已经被销毁，但未获取其状态，调用`stopPiP`接口会导致错误。



**正反案例**

错误示例

<!>
```ts
// 错误：异步任务在窗口销毁后执行
topPipTimer() {
    setTimeout(() => {
        // 用户可能在 1 秒内退出了画中画，窗口已销毁
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