# Line属性/事件

```TypeScript
declare class LineAttribute extends CommonShapeMethod<LineAttribute>
```

除支持[通用属性](arkts-arkui-common-comp-commonmethod-c.md)以及[图形绘制通用属性](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-common.md)外，还支持以下属性：

**继承/实现关系：** LineAttribute extends CommonShapeMethod<LineAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endPoint

```TypeScript
endPoint(value: Array<any>)
```

设置直线终点坐标点（相对于Line组件绘制区域的左上角原点），支持[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)动态设置属性方法，异常值按照默认值处理。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 直线终点坐标点（相对于Line组件绘制区域的左上角原点），单位vp。数组格式为[x坐标, y坐标]，数组长度必须为2，元素应为Length类型。<br>默认值：[0, 0] <br>异常值undefined和null按照默认值处理。 |

## startPoint

```TypeScript
startPoint(value: Array<any>)
```

设置直线起点坐标点（相对于Line组件绘制区域的左上角原点），支持[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)动态设置属性方法，异常值按照默认值处理。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 直线起点坐标点（相对于Line组件绘制区域的左上角原点），单位vp。数组格式为[x坐标, y坐标]，数组长度必须为2，元素应为Length类型。<br>默认值：[0, 0] <br>异常值undefined和null按照默认值处理。 |
