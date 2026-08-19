# ColorFilter

创建具有4*5矩阵的颜色过滤器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ColorFilter--><!--Device-unnamed-export declare class ColorFilter-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: double[])
```

构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorFilter-constructor(value: double[])--><!--Device-ColorFilter-constructor(value: double[])-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double[] | 是 | 创建具有4*5矩阵的颜色过滤器，入参为[m*n]位于m行和n列中矩阵值，矩阵是行优先的。 |

