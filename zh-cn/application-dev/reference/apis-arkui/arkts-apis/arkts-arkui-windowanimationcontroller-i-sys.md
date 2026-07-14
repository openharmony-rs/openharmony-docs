# WindowAnimationController（系统接口）

窗口动画控制器。在创建一个WindowAnimationController对象时，需要实现其中的所有回调函数。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onAppTransition

```TypeScript
onAppTransition(fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

应用转场时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromWindowTarget | WindowAnimationTarget | 是 | 转场前的动画窗口。 |
| toWindowTarget | WindowAnimationTarget | 是 | 转场后的动画窗口。 |
| finishCallback | WindowAnimationFinishedCallback | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

## onCloseWindow

```TypeScript
onCloseWindow(closingWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback): void
```

关闭窗口时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| closingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | WindowAnimationFinishedCallback | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

## onMinimizeWindow

```TypeScript
onMinimizeWindow(minimizingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

最小化窗口时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minimizingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | WindowAnimationFinishedCallback | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

## onScreenUnlock

```TypeScript
onScreenUnlock(finishCallback: WindowAnimationFinishedCallback): void
```

屏幕解锁时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| finishCallback | WindowAnimationFinishedCallback | 是 | 动画完成后的回调。 |

## onStartAppFromLauncher

```TypeScript
onStartAppFromLauncher(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从桌面启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | WindowAnimationFinishedCallback | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

## onStartAppFromOther

```TypeScript
onStartAppFromOther(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从除了桌面和最近任务列表以外其他地方启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | WindowAnimationFinishedCallback | 是 | 动画完成后的回调 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

## onStartAppFromRecent

```TypeScript
onStartAppFromRecent(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从最近任务列表启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | WindowAnimationFinishedCallback | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

## onWindowAnimationTargetsUpdate

```TypeScript
onWindowAnimationTargetsUpdate(fullScreenWindowTarget: WindowAnimationTarget,
      floatingWindowTargets: Array<WindowAnimationTarget>): void
```

动画目标窗口更新时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullScreenWindowTarget | WindowAnimationTarget | 是 | 全屏状态的动画目标窗口。 |
| floatingWindowTargets | Array&lt;WindowAnimationTarget&gt; | 是 | 悬浮状态的动画目标窗口。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

