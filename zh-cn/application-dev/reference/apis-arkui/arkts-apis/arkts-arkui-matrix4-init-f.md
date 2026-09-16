# init

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## init

```TypeScript
function init(
    options: [
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number
    ]
  ): Matrix4Transit
```

Matrix的构造函数，可以通过传入的参数创建一个四阶矩阵，矩阵为列优先，即输入数组的16个值按列依次填充至矩阵：array[0]~array[3]为第1列，array[4]~array[7]为第2列，array[8]~array [11]为第3列，array[12]~array[15]为第4列。当仅需单位矩阵时，推荐使用matrix4.identity()。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number     ] | 是 | 参数为长度为16（4*4）的number数组，详情见四阶矩阵说明。<br>各number取值范围：(-∞, +∞) <br>默认值：<br>[1, 0, 0, 0, <br>0, 1, 0, 0, <br>0, 0, 1, 0, <br>0, 0, 0, 1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 根据入参创建的四阶矩阵对象。 |

**示例**

```TypeScript
import { matrix4 } from '@kit.ArkUI';

// 创建一个四阶矩阵
let matrix = matrix4.init(
  [1.0, 0.0, 0.0, 0.0,
    0.0, 1.0, 0.0, 0.0,
    0.0, 0.0, 1.0, 0.0,
    0.0, 0.0, 0.0, 1.0]);

@Entry
@Component
struct Tests {
  build() {
    Column() {
      // $r("app.media.zh")需要替换为开发者所需的图像资源文件。 
      Image($r("app.media.zh"))
        .width('40%')
        .height(100)
        .transform(matrix)
    }
  }
}
```
