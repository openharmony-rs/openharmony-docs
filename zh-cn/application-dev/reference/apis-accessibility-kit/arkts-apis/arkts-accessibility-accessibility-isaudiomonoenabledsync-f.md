# isAudioMonoEnabledSync

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## isAudioMonoEnabledSync

```TypeScript
function isAudioMonoEnabledSync(): boolean
```

使用同步方法判断单声道音频模式是否开启。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function isAudioMonoEnabledSync(): boolean--><!--Device-accessibility-function isAudioMonoEnabledSync(): boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否开启单声道音频模式。true表示开启单声道音频模式，false表示未开启单声道音频模式。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isAudioMonoEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}

```

