# UnionEffectContainer属性/事件

```TypeScript
declare class UnionEffectContainerAttribute extends CommonMethod<UnionEffectContainerAttribute>
```

支持通用属性，支持宽高设置。

**说明：** 

融合过程中容器会变成粘连的非线性形变效果，边框会变成融合后的粘连效果，故与边框相关的能力在融合形变过程中会发生变化，未支持融合形变效果的边框属性可能无法正常生效。目前与边框相关且支持融合形变效果的属性：[shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow)、[backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor)、[pointLight](#pointlight)。上述效果会绘制在融合后的形状上，属于UnionEffectContainer的绘制部分。

在该组件上设置上述与边框相关支持融合形变效果的属性，绘制体现在该组件上，如果后代组件设置了同一个属性，实际上两个属性的设置相互独立，会绘制两次，一次发生在UnionEffectContainer组件的绘制中，一次发生在后代组件自身的属性绘制中。在无特殊设计需求时，不需要在使用祖先组件UnionEffectContainer融合效果的后代组件中设置同一个支持融合形变效果的属性，避免融合效果因双重绘制而出现视觉异常。

**继承/实现关系：** UnionEffectContainerAttribute extends CommonMethod<UnionEffectContainerAttribute>

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
