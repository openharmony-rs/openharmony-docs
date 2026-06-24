# EffectComponent

Defines Effect Component instance.


## EffectComponent

```TypeScript
EffectComponent()
```

创建特效绘制合并组件，用于对子组件背景模糊特效的绘制合并。

**起始版本：** 10

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为10.

## EffectComponent

```TypeScript
EffectComponent(options?: EffectComponentOptions)
```

创建特效绘制合并组件，无参数或者参数为EffectLayer.None时用于对子组件背景模糊特效的绘制合并。有明确参数时表示当前渲染图层置于特殊图层。

**起始版本：** 20

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为20.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | EffectComponentOptions | 否 |  |

## 汇总

- [EffectComponentOptions](arkts-arkui-effectcomponent-effectcomponentoptions-i-sys.md)
- [EffectLayer](arkts-arkui-effectcomponent-effectlayer-e-sys.md)
