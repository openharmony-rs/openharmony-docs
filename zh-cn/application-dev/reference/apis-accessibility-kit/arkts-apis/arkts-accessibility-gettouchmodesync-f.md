# getTouchModeSync

## getTouchModeSync

```TypeScript
function getTouchModeSync(): string
```

查询触摸浏览功能下的单击/双击操作模式。

**起始版本：** 20

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示当前操作模式。<br>- singleTouchMode：表示单击操作模式。<br>- doubleTouchMode：表示双击操作模式。<br>- none：表示未开启触摸浏览功能。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let touchMode: string = accessibility.getTouchModeSync();
    console.info(`current touch mode: ${JSON.stringify(touchMode)}`);
  }

  build() {
    Column() {
    }
  }
}

```

