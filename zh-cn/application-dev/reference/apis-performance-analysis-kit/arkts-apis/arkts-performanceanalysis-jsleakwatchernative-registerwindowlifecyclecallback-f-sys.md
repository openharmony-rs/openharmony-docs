# registerWindowLifeCycleCallback（系统接口）

## 导入模块

```TypeScript
```

## registerWindowLifeCycleCallback

```TypeScript
function registerWindowLifeCycleCallback(cb: WindowLifeCycleCallback): boolean
```

注册窗口生命周期的回调

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function registerWindowLifeCycleCallback(cb: WindowLifeCycleCallback): boolean--><!--Device-jsLeakWatcherNative-function registerWindowLifeCycleCallback(cb: WindowLifeCycleCallback): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cb | [WindowLifeCycleCallback](arkts-performanceanalysis-windowlifecyclecallback-t-sys.md) | 是 | 接收生命周期已结束的window对象的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 回调是否注册成功 |
