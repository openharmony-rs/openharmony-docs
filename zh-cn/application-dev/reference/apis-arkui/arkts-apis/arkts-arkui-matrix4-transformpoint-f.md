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

**替代接口：** [transformPoint](arkts-arkui-matrix4-matrix4transit-i.md#transformpoint-1)

<!--Device-matrix4-function transformPoint(options: [number, number]): [number, number]--><!--Device-matrix4-function transformPoint(options: [number, number]): [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [number, number] | 是 | 需要转换的坐标点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [number, number] | 返回矩阵变换后的Point对象。 |

