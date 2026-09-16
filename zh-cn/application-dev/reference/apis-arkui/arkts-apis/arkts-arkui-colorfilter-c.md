# ColorFilter

创建具有4*5矩阵的颜色过滤器。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: number[])
```

ColorFilter的构造函数，创建具有4\*5矩阵的颜色过滤器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number[] | 是 | 4*5颜色矩阵的值，[m*n]位于m行和n列中矩阵值，矩阵是行优先的。 |
