# getSeniorModeStateForSelf

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## getSeniorModeStateForSelf

```TypeScript
function getSeniorModeStateForSelf(): Promise<boolean>
```

Check if this application's senior mode is enabled.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function getSeniorModeStateForSelf(): Promise<boolean>--><!--Device-accessibility-function getSeniorModeStateForSelf(): Promise<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Returns {@code true} if senior mode is enabled; returns {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality. |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.getSeniorModeStateForSelf().then((data: boolean) => {
      console.info(`Succeeded in getting seniorModeStateForSelf, data: ${data}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to call getSeniorModeStateForSelf, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}

```

