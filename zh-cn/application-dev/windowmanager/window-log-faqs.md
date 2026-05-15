## 1300012 画中画窗口状态异常

**错误信息**  
The PiP window state is abnormal.

**错误描述**  
画中画窗口状态异常。

### 可能原因

- 画中画窗口已被销毁，但代码仍在尝试访问该窗口
- 画中画窗口处于无效状态（如尚未创建、已关闭、正在销毁）
- 在画中画窗口销毁后，异步任务或回调中访问了窗口对象
- 画中画生命周期管理错误，如在退出画中画模式时未及时释放窗口引用

### 画中画窗口销毁后访问导致崩溃

开发者在画中画窗口销毁后（如用户退出画中画、应用切后台、窗口生命周期结束等）调用画中画窗口相关接口（如 `setPipWindow`、`getPipWindow` 或窗口操作方法），触发错误码 1300012。

**日志信息**

通过 DevEco Studio 或 hdc 查看崩溃日志：

```bash
hdc shell hilog | grep "1300012"
```

典型日志示例：

```
Error Name: BusinessError
Error Message: The PiP window state is abnormal
Error code: 1300012
Stack trace:
  at PipController.updatePipWindow (pip_manager.ts:45)
  at onPipWindowDestroy (PipAbility.ets:78)
```

关键信息：
- 错误码：1300012
- 堆栈：画中画窗口操作调用位置
- 文件名和行号：定位具体代码位置（如 `PipAbility.ets` 第 78 行）

**分析定位**

**步骤1：查找画中画窗口访问位置**

```bash
grep -n "setPipWindow|getPipWindow|updatePipWindow" src/**/*.ts
```

检查调用位置的上下文：
- 是否在画中画窗口销毁回调（如 `onPipWindowDestroy`）中？
- 是否在 `aboutToDisappear`、`onDestroy` 等生命周期方法中？
- 是否在 `setTimeout`、`Promise` 等异步回调中，且回调执行时窗口可能已销毁？

**步骤2：分析画中画窗口生命周期**

画中画窗口典型生命周期：
```
进入画中画 → 画中画窗口创建 → 画中画激活 → 用户关闭/应用退出 → 画中画窗口销毁 → 窗口对象无效
                                                        ↑
                                              1300012 错误触发点
```

关键结论：
- 画中画窗口销毁后，任何对该窗口的访问都会导致 1300012 错误
- 系统可能在销毁后自动清理窗口资源，但开发者应避免主动调用

**步骤3：使用 hidumper 验证画中画窗口状态**

销毁前：
```bash
hdc shell hidumper -s WindowManagerService -a '-a' | grep -i pip
```
检查是否存在画中画窗口，状态是否为 `PIP`。

销毁后：
```bash
hdc shell hidumper -s WindowManagerService -a '-a' | grep -i pip
```
确认画中画窗口已从列表中移除，或状态变为 `DESTROYED`。

**错误示例**

```ts
// 错误：在画中画窗口销毁回调中再次操作窗口
onPipWindowDestroy() {
    // 此时窗口已销毁，再次调用会触发 1300012
    let pipWindow = getPipWindow(this.context);
    pipWindow.hide(); // 崩溃！1300012
}

// 错误：异步任务在窗口销毁后执行
startPipTimer() {
    setTimeout(() => {
        // 用户可能在 1 秒内退出了画中画，窗口已销毁
        let pipWindow = getPipWindow(this.context);
        pipWindow.updateRect(rect); // 崩溃风险
    }, 1000);
}
```

**解决步骤**

**常规处理：无需处理**  
该错误码通常表示画中画窗口已自然销毁，系统会自动回收资源，开发者无需额外干预。如果错误频繁出现且影响体验，可按以下方式优化代码。

**优化建议**（可选）：

1. **避免在销毁回调中访问窗口**  
   不在 `onPipWindowDestroy`、`onWindowStageDestroy` 等销毁方法中调用画中画窗口接口。

2. **访问前检查窗口有效性**  
   ```ts
   let pipWindow = getPipWindow(this.context);
   if (pipWindow && pipWindow.getWindowState() !== window.WindowState.DESTROYED) {
       // 安全操作
       pipWindow.updateRect(rect);
   }
   ```

3. **取消销毁后的异步任务**  
   ```ts
   private pipTimer: number | undefined;
   
   startPipTimer() {
       this.pipTimer = setTimeout(() => {
           // 操作前先判断标志位
           if (!this.isPipWindowValid) return;
           // 执行操作
       }, 1000);
   }
   
   onPipWindowDestroy() {
       this.isPipWindowValid = false;
       if (this.pipTimer) clearTimeout(this.pipTimer);
   }
   ```

**检查清单**

1. 找到所有画中画窗口的访问点（`getPipWindow`、`setPipWindow` 等）
2. 检查是否在窗口销毁回调（`onPipWindowDestroy`）中调用了窗口方法
3. 检查是否有异步任务（定时器、网络回调、Promise）在窗口销毁后执行
4. 确认画中画窗口的生命周期边界，销毁后不再持有窗口引用
5. 使用 `hidumper` 验证销毁时机是否与代码访问时机吻合

> **说明**
>
> 错误码 1300012 多出现在画中画窗口的正常销毁流程中，系统通常能自行处理。若开发者未主动访问已销毁窗口，可忽略该错误。如需深度排查，请按照上述步骤定位不必要的窗口访问代码并移除。
