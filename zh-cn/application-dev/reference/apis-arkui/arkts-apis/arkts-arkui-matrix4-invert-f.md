# invert

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## invert

```TypeScript
function invert(): Matrix4Transit
```

Matrix的逆函数，可以返回一个当前矩阵对象的逆矩阵，即效果正好相反。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [invert](arkts-arkui-matrix4-matrix4transit-i.md#invert)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Matrix4Transit | 当前矩阵的逆矩阵对象。 |

**示例**

```TypeScript
import { matrix4 } from '@kit.ArkUI';

// matrix1(宽放大2倍) 和 matrix2(宽缩小2倍) 效果相反
let matrix1 = matrix4.identity().scale({ x: 2 });
let matrix2 = matrix1.copy().invert();

@Entry
@Component
struct Tests {
  build() {
    Column() {
      // $r("app.media.zh")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.zh"))
        .width(200)
        .height(100)
        .transform(matrix1)
        .margin({ top: 100 })
      // $r("app.media.zh")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.zh"))
        .width(200)
        .height(100)
        .margin({ top: 150 })
        .transform(matrix2)
    }
  }
}
```
