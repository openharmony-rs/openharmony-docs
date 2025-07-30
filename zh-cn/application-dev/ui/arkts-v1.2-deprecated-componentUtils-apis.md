# @ohos.arkui.componentUtils

以下接口在ArkTS1.1中已标记为废弃，并在ArkTS1.2中不再支持。

## get

ArkTS1.1接口声明：[getRectangleById(id: string): ComponentInfo](../reference/apis-arkui/js-apis-arkui-componentUtils.md#componentutilsgetrectanglebyiddeprecated)

替代的ArkTS1.2接口声明：[getRectangleById(id: string): componentUtils.ComponentInfo](../reference/apis-arkui/js-apis-arkui-UIContext.md#getrectanglebyid)

ArkTS1.1

```typescript
import { componentUtils, matrix4 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Utils {
  @Local x: number = 120;
  @Local y: number = 10;
  @Local z: number = 100;
  @Local value: string = '';
  private matrix1 = matrix4.identity().translate({ x: this.x, y: this.y, z: this.z });

  build() {
    Column() {
      Image($r("app.media.startIcon"))
        .transform(this.matrix1)
        .translate({ x: 20, y: 20, z: 20 })
        .scale({ x: 0.5, y: 0.5, z: 1 })
        .rotate({
          x: 1,
          y: 1,
          z: 1,
          centerX: '50%',
          centerY: '50%',
          angle: 300
        })
        .width(300)
        .height(100)
        .key("image_01")
      Button('getRectangleById')
        .onClick(() => {
          this.value = JSON.stringify(componentUtils.getRectangleById("image_01"))
        }).margin(10).id('onClick')
      Text(this.value)
        .margin(20)
        .width(300)
        .height(300)
        .borderWidth(2)
    }.margin({ left: 50 })
  }
}
```

ArkTS1.2

```typescript
import { matrix4 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Utils {
  @Local x: number = 120;
  @Local y: number = 10;
  @Local z: number = 100;
  @Local value: string = '';
  private matrix1 = matrix4.identity().translate({ x: this.x, y: this.y, z: this.z });

  build() {
    Column() {
      Image($r("app.media.startIcon"))
        .transform(this.matrix1)
        .translate({ x: 20, y: 20, z: 20 })
        .scale({ x: 0.5, y: 0.5, z: 1 })
        .rotate({
          x: 1,
          y: 1,
          z: 1,
          centerX: '50%',
          centerY: '50%',
          angle: 300
        })
        .width(300)
        .height(100)
        .key("image_01")
      Button('getRectangleById')
        .onClick(() => {
          // 使用UIContext上的同名接口替代
          this.value = JSON.stringify(this.getUIContext().getComponentUtils().getRectangleById("image_01"))
        }).margin(10).id('onClick')
      Text(this.value)
        .margin(20)
        .width(300)
        .height(300)
        .borderWidth(2)
    }.margin({ left: 50 })
  }
}
```
