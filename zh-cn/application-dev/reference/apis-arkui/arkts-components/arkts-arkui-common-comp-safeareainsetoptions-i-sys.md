# SafeAreaInsetOptions（系统接口）

```TypeScript
declare interface SafeAreaInsetOptions
```

组件四边的完整边缘内容配置。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface SafeAreaInsetOptions--><!--Device-unnamed-declare interface SafeAreaInsetOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bottom

```TypeScript
bottom?: SafeAreaInsetEdgeConfig
```

附着在物理下边的内容配置。默认值：`undefined`，不设置该边内容。省略该边、传入 `undefined`、`null` 或非法边配置时清除该边原有内容，不影响其他有效边。

**类型：** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SafeAreaInsetOptions-bottom?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-bottom?: SafeAreaInsetEdgeConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## end

```TypeScript
end?: SafeAreaInsetEdgeConfig
```

附着在逻辑结束边的内容配置：从左到右布局时为右边，从右到左布局时为左边。默认值：`undefined`，不设置该边内容。省略该边、传入 `undefined`、`null` 或非法边配置时清除该边原有内容，不影响其他有效边。

**类型：** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SafeAreaInsetOptions-end?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-end?: SafeAreaInsetEdgeConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## start

```TypeScript
start?: SafeAreaInsetEdgeConfig
```

附着在逻辑起始边的内容配置：从左到右布局时为左边，从右到左布局时为右边。默认值：`undefined`，不设置该边内容。省略该边、传入 `undefined`、`null` 或非法边配置时清除该边原有内容，不影响其他有效边。

**类型：** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SafeAreaInsetOptions-start?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-start?: SafeAreaInsetEdgeConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## top

```TypeScript
top?: SafeAreaInsetEdgeConfig
```

附着在物理上边的内容配置。默认值：`undefined`，不设置该边内容。省略该边、传入 `undefined`、`null` 或非法边配置时清除该边原有内容，不影响其他有效边。

**类型：** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SafeAreaInsetOptions-top?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-top?: SafeAreaInsetEdgeConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
