# Path属性/事件

```TypeScript
declare class PathAttribute extends CommonShapeMethod<PathAttribute>
```

除支持[通用属性](arkts-arkui-common-comp-commonmethod-c.md)以及[图形绘制通用属性](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-common.md)外，还支持以下属性：

**继承/实现关系：** PathAttribute extends CommonShapeMethod<PathAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands(value: ResourceStr)
```

设置符合[SVG路径描述规范](arkts-arkui-path-comp.md#svg路径描述规范)的命令字符串，单位为px。命令字符串决定了路径的绘制形状和轨迹。支持[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)动态设置属性方法。像素单位转换方法请参考[像素单位转换](arkts-arkui-common-comp.md#common)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 路径绘制的命令字符串，需符合[SVG路径描述规范](arkts-arkui-path-comp.md#svg路径描述规范)，单位为px。<br>默认值：空字符串<br>异常值undefined和null按照默认值处理。<br>**适用版本：** 20 |
