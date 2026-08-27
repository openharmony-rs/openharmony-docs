# scale

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## scale

```TypeScript
function scale(options: ScaleOption): Matrix4Transit
```

Matrix的缩放函数，可以为当前矩阵增加x轴/y轴/z轴缩放效果。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [scale](arkts-arkui-matrix4-matrix4transit-i.md#scale)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | 是 | 设置缩放参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Matrix4Transit | 缩放后的矩阵对象。 |

**示例**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .scale({
      x: 2,
      y: 3,
      z: 4,
      centerX: 50,
      centerY: 50
    });

  build() {
    Column() {
      // $r("app.media.testImage")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.testImage")).transform(this.matrix1)
        .width('300px')
        .height("300px")
    }.width("100%").height("100%").justifyContent(FlexAlign.Center)
  }
}
```
