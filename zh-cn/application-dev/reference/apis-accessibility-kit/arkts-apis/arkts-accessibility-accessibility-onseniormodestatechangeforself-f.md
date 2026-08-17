# onSeniorModeStateChangeForSelf

## onSeniorModeStateChangeForSelf

```TypeScript
function onSeniorModeStateChangeForSelf(callback: Callback<boolean>): void
```

监听应用自身“长辈模式”变化事件。使用callback异步回调。 与[accessibility.onSeniorModeStateChange](arkts-accessibility-accessibility-onseniormodestatechange-f.md#onseniormodestatechange)（监听系统关怀模式状态变化）对应不同作用范围，本接口仅关注应 用自身状态。 > **说明：** > > - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。 > > - 调用此方法后，务必在组件实例销毁前（如aboutToDisappear生命周期中）使用 > [accessibility.offSeniorModeStateChangeForSelf](arkts-accessibility-accessibility-offseniormodestatechangeforself-f.md#offseniormodestatechangeforself)取消监听，否则可能会导致 > 崩溃。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function onSeniorModeStateChangeForSelf(callback: Callback<boolean>): void--><!--Device-accessibility-function onSeniorModeStateChangeForSelf(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | 回调函数。在应用自身“长辈模式”状态变化时将状态通过此函数进行通知。返回true表示应用自身“长辈模式”已开启；返回false表示应用自身“长辈模式” 已关闭。 |

## 示例

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
    accessibility.onSeniorModeStateChangeForSelf(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

