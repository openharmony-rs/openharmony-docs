# ViewData

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->

ViewData用于表示自动填充的视图数据信息，包含应用名称、页面URL、页面节点信息和页面坐标与宽高等关键数据，适用于需要获取和处理页面视图信息以实现自动填充功能的场景。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**起始版本：** 26.0.0

## ViewData

**原子化服务API（仅ArkTS-Dyn）**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称          | 类型                                                              | 只读 | 可选 | 说明      |
| ------------- | ----------------------------------------------------------------- | ---- | ---- | --------- |
| bundleName    | string                                                            | 否   | 否   | 应用的名称。 |
| pageUrl       | string                                                            | 否   | 否   | 页面的url。 |
| pageNodeInfos | Array\<[PageNodeInfo](js-apis-inner-application-pageNodeInfo.md)> | 否   | 否   | 页面节点的信息。 |
| pageRect      | [AutoFillRect](js-apis-inner-application-autoFillRect.md)         | 否   | 否   | 页面坐标和宽高信息。 |