# setSeniorModeStateForSelf

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## setSeniorModeStateForSelf

```TypeScript
function setSeniorModeStateForSelf(state: boolean): Promise<void>
```

Set this application's senior mode.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function setSeniorModeStateForSelf(state: boolean): Promise<void>--><!--Device-accessibility-function setSeniorModeStateForSelf(state: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | boolean | 是 | Indicates whether to enable senior mode for this application. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

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
    accessibility.setSeniorModeStateForSelf(true).then(() => {
      console.info(`Succeeded in setting seniorModeStateForSelf`);
    }).catch((err: BusinessError) => {
      console.error(`failed to call setSeniorModeStateForSelf, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}

```

