# StackOptions

设置堆叠容器的子组件对齐方式。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-declare interface StackOptions--><!--Device-unnamed-declare interface StackOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent?: Alignment
```

设置子组件在容器内的对齐方式。该属性与接口的构造入参同时设置时，以属性设置的值为准。 默认值：Alignment.Center 非法值：按默认值处理。 **说明：** 该参数与align同时设置时，后设置的属性值会覆盖先设置的属性值。

**类型：** Alignment

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-StackOptions-alignContent?: Alignment--><!--Device-StackOptions-alignContent?: Alignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

