# PathShape

用于clipShape和maskShape接口的路径。

继承自[CommonShapeMethod](arkts-arkui-commonshapemethod-c.md)。

**继承/实现关系：** PathShape extends [CommonShapeMethod<PathShape>](CommonShapeMethod<PathShape>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands(commands: string): PathShape
```

设置路径的绘制指令。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| commands | string | 是 | 路径的绘制指令。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PathShape | 返回PathShape对象。 |

## constructor

```TypeScript
constructor(options?: PathShapeOptions)
```

创建PathShape对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PathShapeOptions | 否 | 路径参数。 |

