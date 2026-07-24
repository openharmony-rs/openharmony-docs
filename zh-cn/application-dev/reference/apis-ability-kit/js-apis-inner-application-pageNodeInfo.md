# PageNodeInfo

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->

PageNodeInfo用于描述自动填充场景下的页面节点信息，包含节点ID、自动填充类型、当前值、占位提示文本、坐标位置及获焦状态等关键数据，适用于自动填充服务获取页面控件信息以执行填充操作的场景。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**起始版本：** 26.0.0

## PageNodeInfo

**原子化服务API（仅ArkTS-Dyn）**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称         | 类型                                                      | 只读 | 可选 | 说明            |
| ------------ | --------------------------------------------------------- | ---- | ---- | -------------- |
| id           | ArkTS-Dyn: number<br/>ArkTS-Sta: int                      | 否   | 否   | 页面节点的ID。 |
| autoFillType | [AutoFillType](js-apis-inner-application-autoFillType.md) | 否   | 否   | 页面节点的自动填充类型。 |
| value        | string                                                    | 否   | 否   | 页面节点当前显示的值或用户输入的值。用于自动填充时将此值填充到对应节点。 |
| placeholder  | string  | 否   | 是   | 页面节点的占位提示文本，通常显示在输入控件中用于提示用户期望输入的内容，可辅助自动填充服务识别填充类型。 |
| rect         | [AutoFillRect](js-apis-inner-application-autoFillRect.md) | 否   | 否   | 当前节点的坐标和宽高信息。 |
| isFocus      | boolean                                                   | 否   | 否   | 当前节点是否获焦。true表示当前节点获焦，false表示当前节点未获焦。 |
