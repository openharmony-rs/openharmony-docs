# offSeniorModeStateChangeForSelf

## offSeniorModeStateChangeForSelf

```TypeScript
function offSeniorModeStateChangeForSelf(callback?: Callback<boolean>): void
```

Unregister the observer for this application's senior mode state changes.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | 否 | Asynchronous callback interface.<br>Default behavior: Unregister all callbacks for app senior mode state changes. |

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

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}

```

