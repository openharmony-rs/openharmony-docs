# isAudioMonoEnabled

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

<a id="isaudiomonoenabled"></a>
## isAudioMonoEnabled

```TypeScript
function isAudioMonoEnabled(): Promise<boolean>
```

判断单声道音频模式是否开启。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function isAudioMonoEnabled(): Promise<boolean>--><!--Device-accessibility-function isAudioMonoEnabled(): Promise<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示单声道音频模式已开启；返回false表示单声道音频模式已关闭。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isAudioMonoEnabled().then((data: boolean) => {
      console.info(`success data:isAudioMonoEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to isAudioMonoEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}

```

