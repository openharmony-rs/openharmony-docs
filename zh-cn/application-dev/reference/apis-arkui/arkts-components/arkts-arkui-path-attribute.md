# Path属性/事件

除支持通用属性以及[图形绘制通用属性](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-common.md)外，还支持以下 属性：

**继承/实现关系：** PathAttribute extends CommonShapeMethod<PathAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## commands

```TypeScript
commands(value: ResourceStr)
```

设置符合SVG路径描述规范的命令字符串，单位为px。命令字符串决 定了路径的绘制形状和轨迹。支持attributeModifier动态设置属性方法。像素单位转换方法请参考 像素单位转换。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 路径绘制的命令字符串，需符合 SVG路径描述规范，单位为px。 默认值：空字符串 异常值undefined和null按照默认值处理。<br>**起始版本：** 20 |
