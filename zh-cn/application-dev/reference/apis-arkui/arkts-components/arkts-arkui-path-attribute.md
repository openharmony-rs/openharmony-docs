# Path属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** PathAttribute extends [CommonShapeMethod<PathAttribute>](CommonShapeMethod<PathAttribute>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands(value: ResourceStr)
```

设置符合[SVG路径描述规范](../../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg路径描述规范)的命令字符串，单位为px。像素单位转换
方法请参考[像素单位转换](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceStr | 是 | 线条绘制的路径。<br/>默认值：空字符串<br/>默认单位：px <br/>异常值undefined和null按照默认值处理。<br>**起始版本：** 20 |

