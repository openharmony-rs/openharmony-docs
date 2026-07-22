# onSeniorModeStateChangeForSelf

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## onSeniorModeStateChangeForSelf

```TypeScript
function onSeniorModeStateChangeForSelf(callback: Callback<boolean>): void
```

Register an observer for this application's senior mode state changes.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function onSeniorModeStateChangeForSelf(callback: Callback<boolean>): void--><!--Device-accessibility-function onSeniorModeStateChangeForSelf(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt; | 是 | Asynchronous callback interface. |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: boolean): void => {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}

```

