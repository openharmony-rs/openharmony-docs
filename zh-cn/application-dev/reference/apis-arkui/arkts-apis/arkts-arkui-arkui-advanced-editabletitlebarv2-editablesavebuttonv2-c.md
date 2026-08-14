# EditableSaveButtonV2

保存按钮配置类，使用@ObservedV2装饰器，支持状态观察。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class EditableSaveButtonV2--><!--Device-unnamed-export declare class EditableSaveButtonV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: EditableSaveButtonV2Options)
```

EditableSaveButtonV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableSaveButtonV2-constructor(options?: EditableSaveButtonV2Options)--><!--Device-EditableSaveButtonV2-constructor(options?: EditableSaveButtonV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EditableSaveButtonV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editablesavebuttonv2options-i.md) | 否 | 保存按钮配置选项。 |

## defaultFocus

```TypeScript
@Trace
  public defaultFocus: boolean
```

是否默认获取焦点。 true：获焦。 false：不获焦。 默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableSaveButtonV2-@Trace  public defaultFocus: boolean--><!--Device-EditableSaveButtonV2-@Trace  public defaultFocus: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isRequired

```TypeScript
@Trace
  public isRequired: boolean
```

是否显示保存按钮。 true：显示保存按钮。 false：不显示保存按钮。 默认值：true。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableSaveButtonV2-@Trace  public isRequired: boolean--><!--Device-EditableSaveButtonV2-@Trace  public isRequired: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
@Trace
  public onAction?: OnActionCallback
```

点击保存按钮的回调函数。未设置时点击按钮无响应。

**类型：** [OnActionCallback](arkts-arkui-onactioncallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableSaveButtonV2-@Trace  public onAction?: OnActionCallback--><!--Device-EditableSaveButtonV2-@Trace  public onAction?: OnActionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

