# UnionEffectContainer properties/events

```TypeScript
declare class UnionEffectContainerAttribute extends CommonMethod<UnionEffectContainerAttribute>
```

Universal attributes are supported. The width and height can be set.

> **NOTE:** 
> 
> - During the union, the container exhibits a sticky non-linear deformation effect, and its border will show a sticky effect after union. Therefore, border-related capabilities will be affected. Currently, the following border-related attributes support the union deformation effect:[border](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#border),[outline](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-outline.md#outline),[shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow),[backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), and [pointLight](#pointlight). The above effects are drawn on the shape after union,which is the drawing part of **UnionEffectContainer**.
> 
> - If the attributes related to the border and supporting the union deformation effect are set on the component, the drawing is displayed on the component. If the same attribute is set on the descendant component, the two attributes are set independently. The drawing is performed twice, once in the drawing of the **UnionEffectContainer**component and once in the drawing of the descendant component. Generally, you do not need to set the same attribute that supports the union deformation effect on the descendant component that uses the union effect of the ancestor component **UnionEffectContainer**. This prevents the deterioration of the union effect.

**Inheritance/Implementation:** UnionEffectContainerAttribute extends CommonMethod<UnionEffectContainerAttribute>

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
