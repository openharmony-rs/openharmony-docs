# SheetOptions

继承自[BindOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 半模态页面内容选项。

**继承/实现关系：** SheetOptions extends [BindOptions](../../apis-na/arkts-apis/arkts-na-component/common-bindoptions-i.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare interface SheetOptions extends BindOptions--><!--Device-unnamed-declare interface SheetOptions extends BindOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置半模态弹窗边缘光效动画模式。 默认值：EdgeLightMode.EDGELIGHT\_DISABLED **系统接口：** 此接口为系统接口。

**类型：** EdgeLightMode

**默认值：** EdgeLightMode.EDGELIGHT_DISABLED

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetOptions-edgeLightMode?: EdgeLightMode--><!--Device-SheetOptions-edgeLightMode?: EdgeLightMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: Position
```

设置半模态弹窗偏移量。当半模态为底部弹窗时，支持设置底部间距。不支持设置半模态的[SheetOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的detents属性。y轴设置为负数的时候不生效。 默认值：x轴为0vp，y轴坐标为0vp。 **系统接口：** 此接口为系统接口。

**类型：** Position

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetOptions-offset?: Position--><!--Device-SheetOptions-offset?: Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

