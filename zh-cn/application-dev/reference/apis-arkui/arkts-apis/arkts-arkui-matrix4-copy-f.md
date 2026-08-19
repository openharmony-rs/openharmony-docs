# copy

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## copy

```TypeScript
function copy(): Matrix4Transit
```

Matrix的拷贝函数，可以拷贝一份当前的矩阵对象。 > **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [copy](arkts-arkui-matrix4-matrix4transit-i.md#copy)

<!--Device-matrix4-function copy(): Matrix4Transit--><!--Device-matrix4-function copy(): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Matrix4Transit | 当前矩阵的拷贝对象。 |

**示例**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().translate({ x: 100 });
  // 对matrix1的拷贝矩阵做scale操作，不影响到matrix1
  private matrix2 = this.matrix1.copy().scale({ x: 2 });

  build() {
    Column() {
      // $r("app.media.bg1")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.bg1"))
        .width("40%")
        .height(100)
        .transform(this.matrix1)
      // $r("app.media.bg2")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.bg2"))
        .width("40%")
        .height(100)
        .margin({ top: 50 })
        .transform(this.matrix2)
    }
  }
}
```

