# init

## init

```TypeScript
function init(options: [
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double,
        double
    ]): Matrix4Transit
```

Matrix的构造函数，可以通过传入的参数创建一个四阶矩阵，矩阵为列优先。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-matrix4-function init(options: [        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double    ]): Matrix4Transit--><!--Device-matrix4-function init(options: [        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double,        double    ]): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [         double,         double,         double,         double,         double,         double,         double,         double,         double,         double,         double,         double,         double,         double,         double,         double     ] | 是 | 参数为长度为16（4*4）的number数组, 详情见四阶矩阵说明。&lt;br/&gt;各number取值范围：(-∞, +∞)&lt;br/&gt;默认值：&lt;br/&gt; [1, 0, 0, 0,&lt;br/&gt;0, 1, 0, 0,&lt;br/&gt;0, 0, 1, 0,&lt;br/&gt;0, 0, 0, 1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Matrix4Transit | 根据入参创建的四阶矩阵对象。 |

