# init

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

<a id="init"></a>
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

Matrix的构造函数，可以通过传入的参数创建一个四阶矩阵，矩阵为列优先。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-matrix4-function init(
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
  ): Matrix4Transit--><!--Device-matrix4-function init(
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
  ): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number     ] | 是 | 参数为长度为16（4*4）的number数组, 详情见四阶矩阵说明。<br/>各number取值范围：(-∞, +∞)<br/>默认值：<br/>[1, 0, 0, 0,<br/>0, 1, 0, 0,<br/>0, 0, 1, 0,<br/>0, 0, 0, 1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 根据入参创建的四阶矩阵对象。 |

