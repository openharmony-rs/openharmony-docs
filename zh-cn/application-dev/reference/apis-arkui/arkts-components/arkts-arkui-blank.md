# Blank

空白填充组件，在容器主轴方向上，空白填充组件具有自动填充容器空余部分的能力。仅当父组件为[Row]{@link Row}/[Column]{@link Column}/[Flex]{@link Flex}时生效。

> **说明：**
>
> 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## Blank

```TypeScript
Blank(min?: number | string)
```

创建空白填充组件。

从API version 10开始：

- Blank在父容器[Row]{@link Row}, [Column]{@link Column} 或[Flex]{@link Flex}主轴方向上未设置大小时会自动拉伸、压缩，设置了大小或容器自适应子节点大小时不会自动拉伸、压缩。  
- Blank设置主轴方向大小（size）与min时约束关系为max(min, size)。  
- Blank在父容器交叉轴上设置大小时不会撑满父容器交叉轴，交叉轴不设置大小时alignSelf默认值为ItemAlign.Stretch，会撑满容器交叉轴。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlankInterface-(min?: number | string): BlankAttribute--><!--Device-BlankInterface-(min?: number | string): BlankAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| min | number \| string | 否 | 空白填充组件在容器主轴上的最小大小。<br/>默认值：0，number类型单位为vp，string类型可以显式指定像素单位，如'10px'。不指定像素单位时，默认单位vp，如'10'，等同于10vp。<br />非法值：按默认值处理。<br/>**说明：** <br/>不支持设置百分比。负值使用默认值。当最小值大于容器可用空间时，使用最小值作为自身大小并超出容器。 |

## 汇总

