# rotate

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## rotate

```TypeScript
function rotate(options: RotateOption): Matrix4Transit
```

Matrix的旋转函数，可以为当前矩阵增加x轴/y轴/z轴旋转效果。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [rotate](arkts-arkui-matrix4-matrix4transit-i.md#rotate)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | 是 | 设置旋转参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Matrix4Transit | 旋转后的矩阵对象。 |

**示例**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .rotate({
      x: 1,
      y: 1,
      z: 2,
      angle: 30
    });

  build() {
    Column() {
      // $r("app.media.bg1")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.bg1")).transform(this.matrix1)
        .width('40%')
        .height(100)
    }.width("100%").margin({ top: 50 })
  }
}
```
