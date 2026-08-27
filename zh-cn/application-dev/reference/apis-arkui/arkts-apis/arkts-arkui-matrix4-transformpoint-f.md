# transformPoint

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## transformPoint

```TypeScript
function transformPoint(options: [number, number]): [number, number]
```

Matrix的坐标点转换函数，可以将当前的变换效果作用到一个坐标点上。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [transformPoint](arkts-arkui-matrix4-matrix4transit-i.md#transformpoint)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [number, number] | 是 | 需要转换的坐标点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [number, number] | 返回矩阵变换后的Point对象。 |

**示例**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private originPoint: number[] = [50, 50];
  private matrix1 = matrix4.identity().translate({ x: 150, y: -50 });
  private transformPoint = this.matrix1.transformPoint([this.originPoint[0], this.originPoint[1]]);
  private matrix2 = matrix4.identity().translate({ x: this.transformPoint[0], y: this.transformPoint[1] });

  build() {
    Column() {
      Text(`矩阵变换前的坐标：[${this.originPoint}]`)
        .fontSize(16)
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.image"))
        .width('600px')
        .height('300px')
        .margin({ top: 50 })
      Text(`矩阵变换后的坐标：[${this.transformPoint}]`)
        .fontSize(16)
        .margin({ top: 100 })
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.image"))
        .width('600px')
        .height('300px')
        .margin({ top: 50 })
        .transform(this.matrix2)
    }.width('100%').padding(50)
  }
}
```
