# onSeniorModeStateChange

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## onSeniorModeStateChange

```TypeScript
function onSeniorModeStateChange(callback: Callback<boolean>): void
```

监听关怀模式启用状态变化事件。使用callback异步回调。

> **说明：**  
>  
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。  
>  
> - 调用此方法后，务必在对象生命周期结束前使用  
> [accessibility.offSeniorModeStateChange](arkts-accessibility-accessibility-offseniormodestatechange-f.md#offseniormodestatechange-1)  
> 取消监听，否则可能会导致崩溃。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function onSeniorModeStateChange(callback: Callback<boolean>): void--><!--Device-accessibility-function onSeniorModeStateChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<boolean> | 是 | 回调函数。返回true表示关怀模式已开启；返回false表示关怀模式已关闭。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}

```

