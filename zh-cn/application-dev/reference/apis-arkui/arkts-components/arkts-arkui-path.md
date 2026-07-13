# Path

路径绘制组件，根据绘制路径生成封闭的自定义形状。

> **说明：**
>
> 该组件从API version 20开始支持使用[AttributeUpdater]{@link AttributeUpdater}类的
> [updateConstructorParams](docroot://reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。


## Path

```TypeScript
Path(options?: PathOptions)
```

Use new to create Path.
Annonymous Object Rectification.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PathOptions | 否 | path options |

## Path

```TypeScript
Path(options?: PathOptions)
```

用于描述Path组件绘制属性。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PathOptions | 否 | Path绘制区域。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [PathOptions](arkts-arkui-path-pathoptions-i.md)
