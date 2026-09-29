# ViewData

```TypeScript
export default interface ViewData
```

自动填充的视图数据信息。

**起始版本：** 26.0.0

<!--Device-unnamed-export default interface ViewData--><!--Device-unnamed-export default interface ViewData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## bundleName

```TypeScript
bundleName: string
```

应用的包名。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ViewData-bundleName: string--><!--Device-ViewData-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## pageNodeInfos

```TypeScript
pageNodeInfos: Array<PageNodeInfo>
```

页面节点信息。

**类型：** Array&lt;[PageNodeInfo](arkts-ability-pagenodeinfo-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ViewData-pageNodeInfos: Array<PageNodeInfo>--><!--Device-ViewData-pageNodeInfos: Array<PageNodeInfo>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## pageRect

```TypeScript
pageRect: AutoFillRect
```

页面的位置坐标与宽高信息。在PC/2in1设备上，密码保险箱以弹窗形式展示，为保证弹窗位置跟随输入框，left和top需置为0。

**类型：** [AutoFillRect](arkts-ability-autofillrect-i-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ViewData-pageRect: AutoFillRect--><!--Device-ViewData-pageRect: AutoFillRect-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## pageUrl

```TypeScript
pageUrl: string
```

页面url。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ViewData-pageUrl: string--><!--Device-ViewData-pageUrl: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore
