# SafeAreaInsetEdgeConfig（系统接口）

```TypeScript
declare interface SafeAreaInsetEdgeConfig
```

单个边缘内容及其布局配置。

**起始版本：** 26.2.0

<!--Device-unnamed-declare interface SafeAreaInsetEdgeConfig--><!--Device-unnamed-declare interface SafeAreaInsetEdgeConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## alignment

```TypeScript
alignment?: SafeAreaInsetAlignment
```

内容沿附着边的对齐方式。默认值：`SafeAreaInsetAlignment.CENTER`。省略或传入非法值时回退为 `SafeAreaInsetAlignment.CENTER`，不清除有效内容。

**类型：** [SafeAreaInsetAlignment](arkts-arkui-common-comp-safeareainsetalignment-e-sys.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-SafeAreaInsetEdgeConfig-alignment?: SafeAreaInsetAlignment--><!--Device-SafeAreaInsetEdgeConfig-alignment?: SafeAreaInsetAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## content

```TypeScript
content: CustomBuilder
```

用于创建该边内容的必填构建函数。构建结果为空时清除该边，不影响其他有效边。该边预留的空间等于内容在垂直于附着边方向上的实测尺寸加上 `spacing`。

每边 builder 应生成一个根组件，可以是普通组件或自定义组件。多个组件应由容器组成单根；多根构建结果不作保证。

**类型：** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-SafeAreaInsetEdgeConfig-content: CustomBuilder--><!--Device-SafeAreaInsetEdgeConfig-content: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## spacing

```TypeScript
spacing?: LengthMetrics
```

边缘内容与主体内容之间、指向容器内部的间隔。支持的单位为 vp、px、fp、lpx，取值须为非负有限值；不支持百分比或资源值。默认值：`0vp`。省略或传入非法值时回退为 `0vp`，不清除有效内容。间隔在内容测量之后计入占用，不预先扣减内容的测量空间。

**类型：** LengthMetrics

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-SafeAreaInsetEdgeConfig-spacing?: LengthMetrics--><!--Device-SafeAreaInsetEdgeConfig-spacing?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
