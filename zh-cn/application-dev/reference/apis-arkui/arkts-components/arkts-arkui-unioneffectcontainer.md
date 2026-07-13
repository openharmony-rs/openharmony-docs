# UnionEffectContainer

形状融合容器，会收集该容器内所有使用[useUnionEffect]{@link CommonMethod#useUnionEffect(value: boolean | undefined)}的后代组件形状，将收集的形状融合生效在容
器上，作为该容器的绘制形状。


## UnionEffectContainer

```TypeScript
UnionEffectContainer(options?: UnionEffectContainerOptions)
```

Specify the construction options for the UnionEffectContainer to create the UnionEffectContainer component.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | UnionEffectContainerOptions | 否 | UnionEffectContainer constructor options. |

## 汇总

- [UnionEffectContainerOptions](arkts-arkui-unioneffectcontainer-unioneffectcontaineroptions-i-sys.md)
- [UnionMode](arkts-arkui-unioneffectcontainer-unionmode-e-sys.md)
