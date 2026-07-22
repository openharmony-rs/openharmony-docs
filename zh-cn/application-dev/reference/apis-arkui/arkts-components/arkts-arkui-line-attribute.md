# Line属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** LineAttribute extends [CommonShapeMethod<LineAttribute>](CommonShapeMethod<LineAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class LineAttribute extends CommonShapeMethod<LineAttribute>--><!--Device-unnamed-declare class LineAttribute extends CommonShapeMethod<LineAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endPoint

```TypeScript
endPoint(value: Array<any>)
```

设置直线终点坐标点（相对坐标），支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法，异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LineAttribute-endPoint(value: Array<any>): LineAttribute--><!--Device-LineAttribute-endPoint(value: Array<any>): LineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 直线终点坐标点（相对坐标），单位vp。<br/>默认值：[0, 0] <br/>异常值undefined和null按照默认值处理。 |

## startPoint

```TypeScript
startPoint(value: Array<any>)
```

设置直线起点坐标点（相对坐标），支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法，异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LineAttribute-startPoint(value: Array<any>): LineAttribute--><!--Device-LineAttribute-startPoint(value: Array<any>): LineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 直线起点坐标点（相对坐标），单位vp。<br/>默认值：[0, 0] <br/>异常值undefined和null按照默认值处理。 |

