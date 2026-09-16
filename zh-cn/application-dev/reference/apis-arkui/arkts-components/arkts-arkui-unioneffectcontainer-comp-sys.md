# UnionEffectContainer (System API)

定义UnionEffectContainer组件.

## UnionEffectContainer

```TypeScript
UnionEffectContainer(options?: UnionEffectContainerOptions)
```

创建形状融合容器组件。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UnionEffectContainerOptions](arkts-arkui-unioneffectcontaineroptions-i-sys.md) | 否 | UnionEffectContainer构造参数，用于决定收集到的后代组件形状的融合形变程度。<br>默认值：{spacing:0} |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [UnionEffectContainerOptions](arkts-arkui-unioneffectcontaineroptions-i-sys.md) | 设置UnionEffectContainer构造参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [UnionMode](arkts-arkui-unionmode-e-sys.md) | 设置融合效果模式。 |

## 示例

```TypeScript
### 示例1（设置融合形变效果）

该示例主要演示如何使用[UnionEffectContainer](#unioneffectcontainer)组件，通过改变spacing值或后代组件的距离，产生融合形变效果。


```

```TypeScript
### 示例2（设置不同类型的融合形变效果）

该示例主要演示如何使用[unionMode](#unionmode)接口，通过设置不同的融合类型，产生不同的融合形变效果。

从API版本26.0.0开始，新增unionMode接口。
```
